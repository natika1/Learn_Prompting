---
sidebar_position: 5
---

# 🟡 Prompt Ensembling

Zespolenie podpowiedzi to koncepcja wykorzystania wielu różnych podpowiedzi do próby
odpowiedzieć na to samo pytanie. Istnieje wiele różnych podejść do tego zagadnienia.

# DiVeRSe

DiVeRSe(@li2022advance) ("**Di**wersja **Ve**rifier na **R**easoning **S**e**ps") to.
metoda, która poprawia wiarygodność odpowiedzi w potrójny sposób. Osiąga to poprzez.
1) wykorzystanie wielu podpowiedzi do generowania zróżnicowanych uzupełnień, 2) wykorzystanie weryfikatora do odróżniania dobrych odpowiedzi od złych oraz 3) wykorzystanie weryfikatora do sprawdzania poprawności kroków rozumowania.


import diverse from '@site/docs/assets/diverse.png';

<div style={{textAlign: 'center'}}>.
  <img src={diverse} style={{width: "750px"}} />
</div>

<div style={{textAlign: 'center'}}>
DiVeRSe (Li i in.)
</div>


### Diverse Prompts

DiVeRSe używa 5 różnych podpowiedzi do danego wejścia. Aby skonstruować każdą podpowiedź, losowo
losowo wybierają kilka przykładów z zestawu treningowego. Oto przykład jednej z takich kilku podpowiedzi
(k=2), z przykładami wziętymi z [GSM8K benchmark](https://raw.githubusercontent.com/openai/grade-school-math/master/grade_school_math/data/train.jsonl)(@cobbe2021training). W praktyce DiVeRSe używa
5 przykładów w podpowiedziach dla tego benchmarku.


```
P: Natalia w kwietniu sprzedała spinki 48 swoim znajomym, a następnie w maju sprzedała o połowę mniej spinek. Ile spinaczy Natalia sprzedała łącznie w kwietniu i maju?
O: Natalia sprzedała w maju 48/2 = 24 spinacze.
Natalia sprzedała w kwietniu i maju 48+24 = 72 spinacze.
#### 72
P: Weng zarabia 12 dolarów na godzinę za opiekę nad dziećmi. Wczoraj przez 50 minut opiekowała się dzieckiem. Ile zarobiła?
O: Weng zarabia 12/60 = 0,2$ za minutę.
Pracując 50 minut, zarobiła 0,2 x 50 = 10$.
#### 10
P: Betty oszczędza pieniądze na nowy portfel, który kosztuje 100$. Betty ma tylko połowę potrzebnych pieniędzy. Jej rodzice postanowili dać jej na ten cel 15$, a dziadkowie dwa razy więcej niż rodzice. O ile więcej pieniędzy potrzebuje Betty, aby kupić portfel?
A:
```

Po wygenerowaniu 5 różnych podpowiedzi jak powyżej, DiVeRSe próbuje 20 ścieżek rozumowania
dla każdej z nich (temperatura = 0,5). Oto kilka przykładowych uzupełnień powyższej zachęty.
Zauważ, że odpowiedzi nie zawsze są poprawne.


``tekst``
<!-- highlight-start -->
Betty ma 0,5*100 = 50 dolarów.
Potem dostaje jeszcze 15 = 65 dolarów.
Następnie dostaje 2*15 = 90$.
Potrzebuje jeszcze 100-90 = 10$.
#### 10
<!-- highlight-end -->
```

``tekst``
<!-- highlight-start -->
A: Betty ma 0,5*100 = 500 dolarów.
Potem dostaje jeszcze 15 = 650 dolarów.
Następnie dostaje 2*15 = 900 dolarów.
Potrzebuje jeszcze 100-90 = 1000$.
#### 1000
<!-- highlight-end -->
```

W tym momencie DiVeRSe wygenerował 100 różnych uzupełnień.

### Weryfikator głosowania

Teraz moglibyśmy po prostu wziąć odpowiedź większości, jak Self-Consistency(@mitchell2022enhancing) robi.

DiVeRSe proponuje jednak znacznie bardziej skomplikowaną metodę, którą nazywają _weryfikatorem głosowania_.

W czasie testu użycie weryfikatora głosowania jest procesem dwuetapowym. Po pierwsze, weryfikator (sieć neuronowa)
przypisuje każdemu uzupełnieniu wynik 0-1 na podstawie tego, jak prawdopodobne jest, że jest ono poprawne. Następnie, komponent "głosowania
sumuje wszystkie wyniki dla różnych odpowiedzi i daje ostateczną odpowiedź.

#### Przykład

Oto mały przykład. Powiedzmy, że mamy następujące uzupełnienia dla podpowiedzi `Co to jest dwa plus dwa?`:

``tekst``
<!-- highlight-start -->
4
<!-- highlight-end -->
```

``tekst``
<!-- highlight-start -->
dwa + 2 = 5
<!-- highlight-end -->
```

``tekst``
<!-- highlight-start -->
Myślę, że 2+2 = 6
<!-- highlight-end -->
```

``tekst``
<!-- highlight-start -->
dwa plus dwa = 4
<!-- highlight-end -->
```

``tekst``
<!-- highlight-start -->
To jest 5
<!-- highlight-end -->
```

Weryfikator przeczyta każde uzupełnienie i przypisze mu punktację. Na przykład, może on przypisać
oceny: 0.9, 0.1, 0.2, 0.8, 0.3 odpowiednio. Następnie, komponent głosujący zsumuje punkty dla każdej
odpowiedź.

```
wynik(4) = 0,9 + 0,8 = 1,7
score(5) = 0.1 + 0.3 = 0.4
wynik(6) = 0,2
```

Ostateczną odpowiedzią jest 4, ponieważ ma najwyższy wynik.

**Ale jak jest szkolony weryfikator?

Weryfikator jest trenowany z nieco skomplikowaną funkcją straty, której
Nie będę tutaj omawiał. Przeczytaj sekcję 3.3 papieru, aby uzyskać więcej szczegółów(@li2022advance).

# Ask Me Anything (AMA) Prompting

import ama from '@site/docs/assets/AMA_Prompting.jpg';

<div style={{textAlign: 'center'}}>.
  <img src={ama} style={{width: "750px"}} />
</div>

Ask Me Anything (AMA) prompting (@arora2022ama) jest podobnym podejściem do DiVeRSe. Jednakże, zarówno jego krok wielokrotnych podpowiedzi jak i krok agregacji odpowiedzi różnią się znacząco. Główną ideą AMA jest użycie LLM do wygenerowania wielu podpowiedzi, zamiast po prostu użyć różnych kilkuzdjęciowych przykładów.

### Multiple Prompts

AMA pokazuje, że możesz wziąć pytanie i przeformatować je na wiele sposobów, aby stworzyć różne podpowiedzi. Na przykład, powiedzmy, że skrobasz kilka stron internetowych w poszukiwaniu informacji o zwierzętach i chcesz nagrać tylko te, które żyją w Ameryce Północnej. Skonstruujmy podpowiedź, aby to określić.

Biorąc pod uwagę następujący fragment z Wikipedii:

`tekst.
Niedźwiedź Kermode, czasami nazywany niedźwiedziem duchowym (Ursus americanus kermodei), jest podgatunkiem amerykańskiego niedźwiedzia czarnego i zamieszkuje regiony Centralnego i Północnego Wybrzeża Kolumbii Brytyjskiej w Kanadzie.
```

Możesz sformatować to zadanie w formie podpowiedzi w taki sposób:

`tekst
Czy poniższe twierdzenie jest prawdziwe czy fałszywe biorąc pod uwagę kontekst?

Kontekst: Niedźwiedź Kermode, czasami nazywany niedźwiedziem duchowym (Ursus americanus kermodei), jest podgatunkiem amerykańskiego czarnego niedźwiedzia i żyje w regionach Centralnego i Północnego Wybrzeża Kolumbii Brytyjskiej w Kanadzie.
Twierdzenie: To zwierzę żyje w Ameryce Północnej
Odpowiedź:
```

Jest to trochę dziwne sformułowanie. Dlaczego nie użyć po prostu następującej, prostszej podpowiedzi?

`tekst`
Kontekst: Niedźwiedź Kermode, czasami nazywany niedźwiedziem duchowym (Ursus americanus kermodei), jest podgatunkiem amerykańskiego niedźwiedzia czarnego i zamieszkuje regiony Centralnego i Północnego Wybrzeża Kolumbii Brytyjskiej w Kanadzie.
Pytanie: Czy to zwierzę żyje w Ameryce Północnej?
```

Otóż formułując pytanie w ten szczególny sposób, możemy wygenerować różne podpowiedzi.
Naszym pierwszym krokiem będzie tutaj wzięcie twierdzenia `To zwierzę żyje w Ameryce Północnej` i przeformatowanie go na różne pytania, które w zasadzie pytają o to samo. Aby to zrobić, przepuścimy twierdzenie przez podpowiedzi, takie jak te na poniższym obrazku.

import ama_multi from '@site/docs/assets/AMA_multiprompting.png';

<div style={{textAlign: 'center'}}>.
  <img src={ama_multi} style={{width: "800px"}} />
</div>

To może wyjść:
1. Czy to zwierzę żyło w Ameryce Północnej?
2. Czy to zwierzę żyje w Ameryce Północnej?
3. Gdzie żyje to zwierzę?

Ideą tego rozwiązania jest stworzenie różnych *przeglądów* zadania. Następnie każdy z nich stosujemy do danego kontekstu w taki sposób:

`tekst`
Kontekst: Niedźwiedź Kermode, czasami nazywany niedźwiedziem duchowym (Ursus americanus kermodei), jest podgatunkiem amerykańskiego niedźwiedzia czarnego i zamieszkuje regiony Centralnego i Północnego Wybrzeża Kolumbii Brytyjskiej w Kanadzie.
Pytanie: Czy zwierzę żyło w Ameryce Północnej?
```

Następnie możemy wygenerować odpowiedzi dla każdego z nich:

1. `Tak było`.
2. `Tak jest`.
3. `Ameryka Północna`

To są odpowiedzi *średniozaawansowane*. Musimy je zmapować do etykiet zadań (np. Tak lub Nie).

Możemy to zrobić, przekazując pośrednie odpowiedzi przez monit jak poniżej:

`tekst
Wybierz właściwą kategorię.

"Kategorie":
- Tak, Ameryka Północna
- Nie, nie Ameryka Północna

"Tak było" pasuje do kategorii:
```

Teraz możemy uzyskać nasze odpowiedzi wyjściowe.

1. `Tak, Ameryka Północna`.
2. Tak, Ameryka Północna
3. Tak, Ameryka Północna

Tutaj wszyscy się zgadzają, więc możemy po prostu wziąć pierwszą odpowiedź. Gdyby jednak nie zgadzali się, moglibyśmy użyć kroku agregacji AMA, aby uzyskać ostateczną odpowiedź.

### Answer Aggregation

AMA używa bardzo skomplikowanej strategii agregowania odpowiedzi (bardziej niż DiVeRSe) zamiast po prostu brać odpowiedź większości. Aby zrozumieć, dlaczego odpowiedź większościowa może być złym wyborem, rozważ dwa z pytań, które wygenerowaliśmy wcześniej:

1. Czy zwierzę żyło w Ameryce Północnej?
2. Czy zwierzę żyje w Ameryce Północnej?

Są one niezwykle podobne, więc prawdopodobnie wygenerują ten sam wynik. Ponieważ pytania są tak podobne, będą one skutecznie wpływać na wynik końcowy. Aby sobie z tym poradzić, AMA polega na słabym nadzorze i skomplikowanej matematyce w celu oszacowania zależności między różnymi podpowiedziami, które tworzy, a następnie używa tego do odpowiedniego ważenia.

Tak więc, dla trzech wygenerowanych przez nas pytań, może on przypisać wagi 25%, 25% i 50%, ponieważ dwa pierwsze są tak podobne.

Chociaż strategia agregacji AMA jest potężna, jest tak skomplikowana, że nie będę jej tutaj pokrywał. Przeczytaj sekcję 3.4 dokumentu, aby uzyskać więcej szczegółów(@arora2022ama).

### Wyniki

- Dzięki tej strategii podpowiadania, AMA jest w stanie wykorzystać GPT-J-6B(@wange2021gptj) do przewyższenia GPT-3.

- AMA jest lepsze w pytaniach, w których kontekst zawiera odpowiedź.

## Takeaways

Metody ensemblingu są bardzo potężne. Mogą być stosowane do poprawy wydajności dowolnego modelu, a także mogą być stosowane do poprawy wydajności modelu w konkretnym zadaniu.

W praktyce, głosowanie większością głosów powinno być Twoją strategią.



