---
sidebar_position: 7
---

# 🟡 Wiedza generowana


Ideą podejścia opartego na generowanej wiedzy(@liu2021generated) jest poproszenie %%LLM|LLM%% o wygenerowanie potencjalnie użytecznych informacji na temat danego pytania/promptu przed wygenerowaniem ostatecznej odpowiedzi.

Na przykład, powiedzmy, że chcesz napisać mały wpis na blogu o jakimś zwierzęciu, takim jak [Spirit bears](https://en.wikipedia.org/wiki/Kermode_bear). Zanim poprosisz %%LLM|LLM%% o napisanie wpisu, możesz poprosić ją o wygenerowanie kilku faktów na temat Spirit bears. To pomoże LLM napisać bardziej informacyjny wpis na blogu. Są dwa proste sposoby, aby to zrobić.

## Single prompt approach

Pierwsze podejście prosi LLM o wygenerowanie wiedzy, a następnie napisanie postu, wszystko za pomocą jednej zachęty.

`tekst.
Wygeneruj 4 fakty o misiu Kermode, a następnie wykorzystaj je do napisania krótkiego wpisu na blogu z wykorzystaniem informacji:
// highlight-start
Niedźwiedź Kermode, znany również jako niedźwiedź duchowy, jest rzadkim podgatunkiem amerykańskiego czarnego niedźwiedzia, który występuje w przybrzeżnych regionach Kolumbii Brytyjskiej w Kanadzie.

1. Niedźwiedź Kermode jest unikalnym podgatunkiem amerykańskiego niedźwiedzia czarnego, przy czym około 10% populacji posiada białe futro.

2. Niedźwiedź Kermode jest symbolem ludu First Nations z Kolumbii Brytyjskiej i jest postrzegany jako zwierzę duchowe.

3. Niedźwiedź Kermode jest ważnym elementem ekosystemu, pomaga w rozproszeniu nasion i utrzymaniu równowagi w lesie.

4. Niedźwiedź kermudzki jest gatunkiem chronionym, a jego populacja jest ściśle monitorowana przez władze wojewódzkie.

Niedźwiedź Kermode to wyjątkowe i szczególne zwierzę, które występuje w przybrzeżnych regionach Kolumbii Brytyjskiej w Kanadzie. Około 10% populacji tego podgatunku amerykańskiego czarnego niedźwiedzia ma białe futro, co czyni je rzadkim widokiem. Niedźwiedź Kermode jest symbolem pierwszych narodów Kolumbii Brytyjskiej i jest postrzegany jako zwierzę duchowe. Jest ważną częścią ekosystemu, pomagając w rozpraszaniu nasion i utrzymaniu równowagi w lesie. Niedźwiedź Kermode jest gatunkiem chronionym, a jego populacja jest ściśle monitorowana przez rząd prowincji. Jest to piękne i majestatyczne zwierzę, dlatego ważne jest, abyśmy zrobili co w naszej mocy, aby chronić i zachować ten gatunek.
// highlight-end
```


# Dual prompt approach

W tym podejściu najpierw skłaniamy %%LLM|LLM%% do wygenerowania faktów o niedźwiedziu:
  
`tekst`
Wygeneruj 10 faktów o misiu Kermode:
// highlight-start
1. Niedźwiedź Kermode, znany również jako Spirit Bear, to rzadki podgatunek amerykańskiego czarnego niedźwiedzia występujący w Kolumbii Brytyjskiej w Kanadzie.

2. Niedźwiedź Kermode ma unikalne białe lub kremowe umaszczenie, które jest spowodowane genem recesywnym.

3. Niedźwiedź Kermode jest symbolem nadziei i odnowy dla mieszkańców Pierwszych Narodów Kolumbii Brytyjskiej.

4. Niedźwiedź Kermode jest gatunkiem chronionym i znajduje się na liście gatunków specjalnej troski Komitetu ds. Statusu Zagrożonych Dzikich Zwierząt w Kanadzie.
// highlight-end
```

Następnie podajemy te informacje do kolejnego podpowiedzi, aby napisać wpis na blogu:

`tekst`
1. Niedźwiedź Kermode, znany również jako Spirit Bear, to rzadki podgatunek amerykańskiego niedźwiedzia czarnego występujący w Kolumbii Brytyjskiej w Kanadzie.

2. Niedźwiedź Kermode ma unikalne białe lub kremowe umaszczenie, które jest spowodowane genem recesywnym.

3. Niedźwiedź Kermode jest symbolem nadziei i odnowy dla mieszkańców Pierwszych Narodów Kolumbii Brytyjskiej.

4. Niedźwiedź Kermode jest gatunkiem chronionym i znajduje się na liście gatunków specjalnej troski Komitetu ds. Statusu Zagrożonych Dzikich Zwierząt w Kanadzie.

Wykorzystaj powyższe fakty do napisania jedno akapitowego wpisu na blogu o niedźwiedziu Kermode:

// highlight-start

Niedźwiedź Kermode, znany również jako Spirit Bear, to rzadki podgatunek amerykańskiego czarnego niedźwiedzia występujący w Kolumbii Brytyjskiej w Kanadzie. Ten wyjątkowy niedźwiedź ma białe lub kremowe umaszczenie, spowodowane przez gen recesywny, i jest symbolem nadziei i odnowy dla Pierwszych Narodów Kolumbii Brytyjskiej. Niedźwiedź Kermode jest gatunkiem chronionym i znajduje się na liście gatunków specjalnej troski Komitetu ds. Statusu Zagrożonych Dzikich Zwierząt w Kanadzie, co czyni go ważnym elementem bioróżnorodności regionu.

// highlight-end
```

Polecam to drugie podejście, ponieważ może ono bardziej wiarygodnie produkować dłuższe treści.

## Inny przypadek użycia

Podejście oparte na generowanej wiedzy zostało w rzeczywistości wprowadzone dla zupełnie innego zadania, jakim jest odpowiadanie na trudne pytania. Rozważmy następujące pytanie, na które GPT-3 odpowiada błędnie:

<div trydyno-embed="" openai-model="text-davinci-003" initial-prompt="Który kraj jest większy, Kongo czy RPA?" initial-response="RPA jest większe od Kongo." max-tokens="256" box-rows="3" model-temp="0" top-p="0">.
    <noscript>Failed to load Dyno Embed: JavaScript musi być włączony</noscript>.
</div>

<br/>.

Jeśli najpierw poprosimy %%LLM|LLM%% o wygenerowanie faktów o Kongo i RPA, możemy następnie użyć tych informacji, aby odpowiedzieć poprawnie na pytanie. W teorii jest to podobne do %%CoT|CoT prompting%%, ponieważ skutecznie nakłaniamy LLM do wygenerowania pośredniego rozumowania w postaci powiązanych faktów.

Zacznijmy od pierwszego kroku, czyli *generowania wiedzy*. Możemy poprosić %%LLM|LLM%% o wygenerowanie faktów o Kongo i RPA:

<div trydyno-embed="" openai-model="text-davinci-003" initial-prompt="Wygeneruj trochę wiedzy o rozmiarach RPA i Konga:" initial-response="RPA jest 25. co do wielkości krajem na świecie, o powierzchni 1 221 037 kilometrów kwadratowych (471 445 mil kwadratowych). Kongo natomiast jest 11. największym krajem na świecie, o powierzchni 2 344 858 kilometrów kwadratowych (905 567 mil kwadratowych). Republika Południowej Afryki jest prawie o połowę mniejsza od Konga, z liczbą ludności 57,7 mln w porównaniu do 84,3 mln ludności Konga. RPA jest najludniejszym krajem w regionie, podczas gdy Kongo jest drugim pod względem liczby ludności." max-tokens="256" box-rows="6" model-temp="0" top-p="0">
    <noscript>Failed to load Dyno Embed: JavaScript musi być włączony</noscript>.
</div>

<br/>.

Następnie wykorzystajmy tę wiedzę, aby odpowiedzieć na pytanie poprawnie. To jest właśnie etap *integracji wiedzy*!

<div trydyno-embed="" openai-model="text-davinci-003" initial-prompt="Republika Południowej Afryki jest 25. największym krajem na świecie, o powierzchni 1 221 037 kilometrów kwadratowych (471 445 mil kwadratowych). Kongo natomiast jest 11. największym krajem na świecie, o powierzchni 2 344 858 kilometrów kwadratowych (905 567 mil kwadratowych). Republika Południowej Afryki jest prawie o połowę mniejsza od Konga, z liczbą ludności 57,7 mln w porównaniu do 84,3 mln ludności Konga. RPA jest najbardziej zaludnionym krajem w regionie, podczas gdy Kongo jest drugim najbardziej zaludnionym.\NKtóry kraj jest większy, Kongo czy RPA?" initial-response="Kongo jest większe niż RPA." max-tokens="256" box-rows="15" model-temp="0" top-p="0">
    <noscript>Failed to load Dyno Embed: JavaScript musi być włączony</noscript>.
</div>

# A more technical discussion

Chociaż powyższy przypadek użycia był podobny do sposobu, w jaki generowana wiedza została pierwotnie wprowadzona, nie jest dokładnie taki sam. Poniższa treść obejmuje bardziej techniczny kontekst, w którym wprowadzono to podejście. Podąża za wzorcem dwóch kroków pośrednich (generowanie wiedzy i integracja wiedzy), które widzieliśmy powyżej.

import KGImage from '@site/docs/assets/knowledge_generation.png';

<div style={{textAlign: 'center'}}>.
  <img src={KGImage} style={{width: "750px"}} />
</div>

<div style={{textAlign: 'center'}}>.
Wiedza wygenerowana (Liu i in.)
</div>

### Generowanie wiedzy

W kroku generowania wiedzy, %%LLM|LLM%% jest proszony o wygenerowanie zestawu faktów
na temat **pytania**. LLM jest podpowiadany w kilku ujęciach, jak widać poniżej.
M różnych uzupełnień jest generowanych przy użyciu tej samej zachęty (podobnie jak w podejściu samokonsekwencji).

import KGP1Image from '@site/docs/assets/gen_k_p1.png';

<div style={{textAlign: 'center'}}>.
  <img src={KGP1Image} style={{width: "500px"}} />
</div>

<div style={{textAlign: 'center'}}>
Przykład wiedzy wygenerowanej (Liu et al.)
</div>


### Integracja wiedzy

Następnie generujemy pytania "wzbogacone o wiedzę" i podpowiadamy je %%LLM|LLM%%.
aby uzyskać ostateczne odpowiedzi. Najłatwiej zrozumieć to na przykładzie.

Załóżmy, że próbujemy odpowiedzieć na **pytanie**.
"Większość Kangurów ma <maskotki> kończyn". Załóżmy, że na etapie generowania wiedzy
wygenerowaliśmy 2 wiedzy (M=2):

- Wiedza 1: `Kangury to ssaki marsupialne, które żyją w Australii.`

- Wiedza 2: `Kangury to ssaki marsupialne, które mają 5 kończyn.`

Teraz konkatenujemy każdą wiedzę z pytaniem, aby wygenerować pytania wzbogacone o wiedzę:

- Wiedza rozszerzona Pytanie 1: `Większość kangurów ma <maskotki> kończyn. Kangury to ssaki marsupialne, które żyją w Australii.`

- Wiedza rozszerzona Pytanie 2: `Większość kangurów ma <maskotki> kończyn. Kangury to marsupiaki, które mają 5 kończyn.`

Następnie podpowiadamy LLM z tymi rozszerzonymi o wiedzę pytaniami i otrzymujemy ostateczne propozycje odpowiedzi:

- Odpowiedź 1: `4`

- Odpowiedź 2: `5`

Wybieramy odpowiedź z największym prawdopodobieństwem jako odpowiedź ostateczną. Adres
najwyższe prawdopodobieństwo może być softmax prawdopodobieństwa tokenu odpowiedzi, lub
logiem prawdopodobieństwa tokena odpowiedzi (tokenów).

# Recitation-Augmented Language Models

Recitation-augmented(@sun2022recitationaugmented) approach it is similar to generated knowledge (basically the same). Jest jednak znacznie mniej złożone niż formalna implementacja wiedzy wygenerowanej.


import RImage from '@site/docs/assets/recitation.png';

<div style={{textAlign: 'center'}}>.
  <img src={RImage} style={{width: "250px"}} />
</div>

Chodzi o to, by kilka strzałów skłoniło LLM do wygenerowania informacji *i* odpowiedzi w *tym samym* kroku. Fakt, że jest to recytowanie/generowanie wiedzy i odpowiadanie na pytanie w tym samym kroku jest główną różnicą w stosunku do podejścia opartego na wygenerowanej wiedzy.

Powtarzając, podejście to podpowiada modelowi wiele przykładów (pytanie, recytacja, odpowiedź), a następnie zadaje pytanie. Autorzy zauważają, że to podejście może być połączone z samokonsekwencją lub wieloma ścieżkami ukończenia.



## Notes

- Wygenerowana wiedza wykazuje poprawę na różnych zestawach danych commonsense.

- Wiedza odpowiadająca wybranej odpowiedzi nazywana jest _wiedzą wybraną_.

- W praktyce można przyjąć najczęściej pojawiającą się odpowiedź jako ostateczną.

