---
sidebar_position: 2
locale: en-us
---

# 🟢 Pytania wielokrotnego wyboru

Użyjmy GPT do rozwiązania pytania z LSAT[^1]!

[^1]:
LSAT (Law School Admission Test) to standaryzowany test używany przez szkoły prawnicze w Stanach Zjednoczonych do oceny umiejętności krytycznego myślenia i analitycznego rozumowania przyszłych studentów.

Poniżej znajduje się przykładowe pytanie LSAT. Zastanów się, jak byś na nie odpowiedział, a także
jak również swoje rozumowanie.

`md
<!-- highlight-start -->
Jan z Worcester, angielski mnich, odnotował 8 grudnia 1128 roku obserwację dwóch niezwykle dużych plam słonecznych. Pięć dni później genialna aurora borealis (północne światła) została zaobserwowana w południowej Korei. Aktywność plam słonecznych jest zazwyczaj poprzedzona pojawieniem się zorzy polarnej, po okresie czasu, który wynosi średnio pięć dni. Tak więc koreańska obserwacja pomaga potwierdzić obserwację Jana z Worcester. Które z poniższych stwierdzeń, jeśli jest prawdziwe, najbardziej wzmacnia ten argument?
<!-- highlight-end -->

a) Zorza polarna może czasami wystąpić nawet wtedy, gdy w poprzednim tygodniu nie było znaczącej aktywności plam słonecznych.
b) Chińskie źródła odnotowały obserwacje plam słonecznych ponad 1000 lat wcześniej niż Jan z Worcester.
c) Tylko duża aktywność plam słonecznych mogła spowodować pojawienie się zorzy polarnej na tak niskiej szerokości geograficznej jak koreańska.
d) Ponieważ niemożliwe jest oglądanie plam słonecznych gołym okiem w typowych warunkach światła dziennego, obserwacja zarejestrowana przez Jana z Worcester miałaby miejsce w nietypowych warunkach pogodowych, takich jak mgła lub cienkie chmury.
e) John of Worcester's account included a drawing of the sunspots, which could be the earliest illustration of sunspot activity.
```

<detale>.
<summary>Prawidłowa odpowiedź to ...</summary>.
c) Tylko duża aktywność plam słonecznych mogła spowodować zorzę polarną widoczną na tak niskiej szerokości geograficznej jak koreańska.
</detale>

Spróbuj wkleić problem do poniższego dema:

<div trydyno-embed="" openai-model="text-davinci-003" initial-prompt="Jan z Worcester, angielski mnich, nagrał obserwację, na 8 grudnia 1128, dwóch niezwykle dużych plam słonecznych. Pięć dzień opóźniony genialny aurora borealis (północny światło) obserwować w południowy Korea. Aktywność plam słonecznych jest zazwyczaj poprzedzona pojawieniem się zorzy polarnej, po okresie czasu, który wynosi średnio pięć dni. Tak więc koreańska obserwacja pomaga potwierdzić obserwację Jana z Worcester. Które z poniższych stwierdzeń, jeśli jest prawdziwe, najbardziej wzmacnia ten argument?
a) Zorza polarna może czasami wystąpić nawet wtedy, gdy w poprzednim tygodniu nie było znaczącej aktywności plam słonecznych.
b) Źródła chińskie odnotowały obserwacje plam słonecznych ponad 1000 lat wcześniej niż Jan z Worcester.
c) Tylko duża aktywność plam słonecznych mogła spowodować pojawienie się zorzy polarnej na tak niskiej szerokości geograficznej jak koreańska.
d) Ponieważ niemożliwe jest oglądanie plam słonecznych gołym okiem w typowych warunkach światła dziennego, obserwacja zarejestrowana przez Jana z Worcester miałaby miejsce w nietypowych warunkach pogodowych, takich jak mgła lub cienkie chmury.
e) John of Worcester's account included a drawing of the sunspots, which could be the earliest illustration of sunspot activity." initial-response="e) John of Worcester's account included a drawing of the sunspots, which could be the earliest illustration of sunspot activity." max-tokens="256" box-rows="10" model-temp="0" top-p="1" padding='1'></div>

<p></p>.

<details scheme='warning'>
<summary>Dlaczego moja odpowiedź jest inna? </summary>
Twoja odpowiedź może się różnić z powodu

1) Aktualizacje modelu bazowego, GPT-3
2) Losowość w procesie generowania tekstu. Możemy uczynić wyjście bardziej spójnym, ustawiając <a href="https://beta.openai.com/docs/api-reference/completions/create#completions/create-temperature">temperaturę</a> na 0.

</detale>.

Model zawiódł. Czy to oznacza, że model nie jest zdolny do odpowiedzi na tego typu pytania? Niekoniecznie. Zanurzymy się w techniki, których możemy użyć, aby poprawić wyniki modelu.

## Magiczna fraza
Standardowy monit, którego użyliśmy powyżej, daje niewielki wgląd w "rozumowanie" wyjścia GPT. Możemy spróbować dodać frazę `let's explain step by step` w taki sposób:


``markdown``
...
e) Relacja Jana z Worcester zawierała rysunek plam słonecznych, który może być najwcześniejszą ilustracją aktywności plam słonecznych.

Wyjaśnijmy to krok po kroku
```
To wyrażenie zwiększy czasownikowość modelu. Możesz otrzymać wyjście takie jak to:

<div trydyno-embed="" openai-model="text-davinci-003" initial-prompt="Jan z Worcester, angielski mnich, nagrał obserwację, na 8 grudnia 1128, dwóch niezwykle dużych plam słonecznych. Pięć dzień opóźniony genialny aurora borealis (północny światło) obserwować w południowy Korea. Aktywność plam słonecznych jest zazwyczaj poprzedzona pojawieniem się zorzy polarnej, po okresie czasu, który wynosi średnio pięć dni. Tak więc koreańska obserwacja pomaga potwierdzić obserwację Jana z Worcester. Które z poniższych stwierdzeń, jeśli jest prawdziwe, najbardziej wzmacnia ten argument?
a) Zorza polarna może czasami wystąpić nawet wtedy, gdy w poprzednim tygodniu nie było znaczącej aktywności plam słonecznych.
b) Źródła chińskie odnotowały obserwacje plam słonecznych ponad 1000 lat wcześniej niż Jan z Worcester.
c) Tylko duża aktywność plam słonecznych mogła spowodować pojawienie się zorzy polarnej na tak niskiej szerokości geograficznej jak koreańska.
d) Ponieważ niemożliwe jest oglądanie plam słonecznych gołym okiem w typowych warunkach światła dziennego, obserwacja zarejestrowana przez Jana z Worcester miałaby miejsce w nietypowych warunkach pogodowych, takich jak mgła lub cienkie chmury.
e) Relacja Jana z Worcester zawierała rysunek plam słonecznych, który może być najwcześniejszą ilustracją aktywności plam słonecznych. Wyjaśnijmy to krok po kroku" initial-response="A) Ten wybór odpowiedzi jest nieprawidłowy. Ta odpowiedź nie wzmacnia argumentu, ponieważ zamiast tego wprowadza alternatywne wyjaśnienie dla aurora borealis.
B) Ta odpowiedź jest niepoprawna. Ta odpowiedź nie wzmacnia argumentu, ponieważ jest nieistotna dla związku pomiędzy aktywnością plam słonecznych a obserwacjami zorzy polarnej.
C) Ta odpowiedź jest poprawna. Ta odpowiedź wzmacnia argument, sugerując, że aktywność plam słonecznych odnotowana przez Jana z Worcester była przyczyną zorzy polarnej, która została zaobserwowana w Korei pięć dni później.
D) Ta odpowiedź jest nieprawidłowa. Ta odpowiedź nie wzmacnia argumentu, ponieważ jest nieistotna dla związku pomiędzy aktywnością plam słonecznych a obserwacjami zorzy polarnej.
E) Ta odpowiedź jest niepoprawna. Ta odpowiedź nie wzmacnia argumentu, ponieważ jest nieistotna dla związku między aktywnością plam słonecznych a obserwacjami aurory borealis.
Poprawna odpowiedź to C) Tylko duża aktywność plam słonecznych mogła spowodować, że zorza polarna była widoczna na tak niskiej szerokości geograficznej jak koreańska." max-tokens="256" box-rows="10" model-temp="0" top-p="1" padding='1'></div>

<p></p>.

:::info
Zauważ, jak model uzasadnia krok po kroku rozwiązanie problemu.

Specyficznym terminem dla tego zachowania jest Łańcuch Myślowy(@wei2022chain); model sekwencyjnie generuje stwierdzenia, aby dojść do odpowiedzi. Jest to podobne do koncepcji myślenia Systemu 2 (z [Thinking Fast and Slow](https://en.wikipedia.org/wiki/Thinking,_Fast_and_Slow)); model domyślnie ustawia się na myślenie Systemu 1, ale może łańcuchować myślenie Systemu 1, aby dojść do bardziej metodycznej odpowiedzi.
:::

## Ulepszenia

Oto kilka wariantów naszej podstawowej podpowiedzi dla pytań wielokrotnego wyboru:

### Reorder Question Items

Możemy zmienić kolejność pozycji w pytaniu

```
...
a) Relacja Jana z Worcester zawierała rysunek plam słonecznych, który mógł być najwcześniejszą ilustracją aktywności plam słonecznych.
b) Ponieważ niemożliwe jest oglądanie plam słonecznych gołym okiem w typowych warunkach światła dziennego, obserwacja zarejestrowana przez Jana z Worcester miałaby miejsce w nietypowych warunkach pogodowych, takich jak mgła lub cienkie chmury.
...
```

<div trydyno-embed="" openai-model="text-davinci-003" initial-prompt="Jan z Worcester, angielski mnich, nagrał obserwację, na 8 grudnia 1128, dwóch niezwykle dużych plam słonecznych. Pięć dzień opóźniony genialny aurora borealis (północny światło) obserwować w południowy Korea. Aktywność plam słonecznych jest zazwyczaj poprzedzona pojawieniem się zorzy polarnej, po okresie czasu, który wynosi średnio pięć dni. Tak więc koreańska obserwacja pomaga potwierdzić obserwację Jana z Worcester. Które z poniższych stwierdzeń, jeśli jest prawdziwe, najbardziej wzmacnia ten argument?
a) Relacja Jana z Worcester zawiera rysunek plam słonecznych, który może być najwcześniejszą ilustracją aktywności plam słonecznych.
b) Ponieważ nie można zobaczyć plam słonecznych gołym okiem w typowych warunkach światła dziennego, obserwacja odnotowana przez Jana z Worcester miała miejsce w nietypowych warunkach pogodowych, takich jak mgła lub cienkie chmury.
c) Zorza polarna może czasami wystąpić nawet wtedy, gdy w poprzednim tygodniu nie było znaczącej aktywności plam słonecznych.
d) Chińskie źródła odnotowały obserwację plam słonecznych ponad 1000 lat przed Janem z Worcester.
e) Tylko duża aktywność plam słonecznych mogła spowodować zorzę polarną widoczną na tak niskiej szerokości geograficznej jak koreańska.
Wyjaśnijmy to krok po kroku" initial-response="A) Osłabia - Ta opcja osłabia argument, ponieważ sugeruje, że zorza polarna niekoniecznie musiała być spowodowana aktywnością plam słonecznych, co jest argumentem, który autor stara się przedstawić. B) Nie ma wpływu - Ta opcja nie ma wpływu na argumentację, ponieważ nie ma związku z powiązaniem pomiędzy plamami słonecznymi a pojawieniem się zorzy polarnej. C) Wzmacnia - Ta opcja wzmacnia argument, ponieważ sugeruje, że jedynym sposobem, w jaki zorza polarna mogła być widziana w Korei, jest duża aktywność plam słonecznych, co zaobserwował John z Worcester. D) Osłabia - Ta opcja osłabia argument, ponieważ sugeruje, że warunki, w których Jan z Worcester obserwował plamy na słońcu, mogły nie być wiarygodne, co mogłoby poddać w wątpliwość dokładność jego obserwacji. E) Nie ma wpływu - Ta opcja nie ma wpływu na argument, ponieważ nie jest związana z powiązaniem między plamami na słońcu a pojawieniem się zorzy polarnej." max-tokens="256" box-rows="10" model-temp="0" top-p="1" padding='1'></div>

### Przeformułuj pytanie


Przypomnijmy, że pierwotna zachęta była taka:
```
Które z poniższych stwierdzeń, jeśli jest prawdziwe, najbardziej wzmacnia argument?
```

Możemy zmienić podpowiedź na taką:
```
Określ każdy wybór jako wzmacniający, osłabiający lub nie wpływający na argumentację.
```
aby uzyskać dalszy wgląd w wybór odpowiedzi.


<div trydyno-embed="" openai-model="text-davinci-003" initial-prompt="Jan z Worcester, angielski mnich, nagrał obserwację, na 8 grudnia 1128, dwóch niezwykle dużych plam słonecznych. Pięć dzień opóźniony genialny aurora borealis (północny światło) obserwować w południowy Korea. Aktywność plam słonecznych jest zazwyczaj poprzedzona pojawieniem się zorzy polarnej, po okresie czasu, który wynosi średnio pięć dni. Tak więc koreańska obserwacja pomaga potwierdzić obserwację Jana z Worcester. Które z poniższych stwierdzeń, jeśli jest prawdziwe, najbardziej wzmacnia ten argument?
a) Zorza polarna może czasami wystąpić nawet wtedy, gdy w poprzednim tygodniu nie było znaczącej aktywności plam słonecznych.
b) Źródła chińskie odnotowały obserwacje plam słonecznych ponad 1000 lat wcześniej niż Jan z Worcester.
c) Tylko duża aktywność plam słonecznych mogła spowodować pojawienie się zorzy polarnej na tak niskiej szerokości geograficznej jak koreańska.
d) Ponieważ niemożliwe jest oglądanie plam słonecznych gołym okiem w typowych warunkach światła dziennego, obserwacja zarejestrowana przez Jana z Worcester miałaby miejsce w nietypowych warunkach pogodowych, takich jak mgła lub cienkie chmury.
e) Relacja Jana z Worcester zawierała rysunek plam słonecznych, który może być najwcześniejszą ilustracją aktywności plam słonecznych.
Określ każdy wybór jako wzmacniający, osłabiający lub nie wpływający na argument i wyjaśnij krok po kroku." initial-response="A) Osłabia - Ta opcja osłabia argument, ponieważ sugeruje, że zorza polarna niekoniecznie musiała być spowodowana aktywnością plam słonecznych, co jest argumentem, który autor próbuje przedstawić.
B) Nie wpływa - Ta opcja nie wpływa na argument, ponieważ nie jest związana z powiązaniem pomiędzy plamami na Słońcu a pojawieniem się zorzy polarnej.
C) Strengthens - Ta opcja wzmacnia argument, ponieważ sugeruje, że jedynym sposobem, w jaki aurora borealis mogła być widziana w Korei, jest to, że była tam duża aktywność plam słonecznych, co zaobserwował John z Worcester.
D) Osłabia - Ta opcja osłabia argument, ponieważ sugeruje, że warunki, w których Jan z Worcester obserwował plamy na słońcu, mogły nie być wiarygodne, co mogłoby poddać w wątpliwość dokładność jego obserwacji.
E) Nie ma wpływu - Ta opcja nie ma wpływu na argument, ponieważ nie jest związana z powiązaniem między plamami na słońcu a pojawieniem się zorzy polarnej." max-tokens="256" box-rows="10" model-temp="0" top-p="1" padding='1'></div>


### Add Additional Context

Oto przykład problemu, który można łatwo rozwiązać za pomocą twierdzenia Bayesa:

```
Rozważmy dwa testy medyczne, A i B, na obecność pewnego wirusa. Test A jest w 90% skuteczny w rozpoznawaniu wirusa, gdy jest on
ale ma 5% wskaźnik fałszywie pozytywny (wskazując, że wirus jest obecny, podczas gdy nie jest). Test B jest w 95%
skuteczny w rozpoznawaniu wirusa, ale ma 10% wskaźnik fałszywie pozytywny. Oba testy wykorzystują niezależne metody
identyfikacji wirusa. Wirus jest przenoszony przez 2% wszystkich ludzi.
(a) Powiedzmy, że dana osoba jest badana na obecność wirusa tylko przy użyciu testu A. Jakie jest prawdopodobieństwo, że osoba ta
jest rzeczywiście nosicielem wirusa, biorąc pod uwagę, że test A dał wynik pozytywny? (2 punkty)
(b) Powiedzmy, że dana osoba jest badana na obecność wirusa przy użyciu tylko testu B. Jakie jest prawdopodobieństwo, że osoba ta
jest nosicielem wirusa, biorąc pod uwagę, że test B dał wynik pozytywny? (2 punkty)
(c) Powiedzmy, że dana osoba jest badana na obecność wirusa przy użyciu obu testów. Jakie jest prawdopodobieństwo, że osoba ta jest
jest nosicielem wirusa, biorąc pod uwagę, że oba testy dały wynik pozytywny? (2 punkty)
```

Spróbujmy tego z GPT:

<div trydyno-embed="" openai-model="text-davinci-003" initial-prompt="Rozważ dwa testy medyczne, A i B, na obecność wirusa. Test A jest w 90% skuteczny w rozpoznawaniu wirusa, gdy jest on obecny, ale ma 5% wskaźnik fałszywie pozytywny (wskazujący, że wirus jest obecny, gdy nie jest). Test B jest w 95% skuteczny w rozpoznawaniu wirusa, ale ma 10% wskaźnik fałszywie pozytywny. Oba testy stosują niezależne metody identyfikacji wirusa. Wirus jest przenoszony przez 2% wszystkich ludzi. a) Powiedzmy, że osoba jest testowana na wirusa przy użyciu tylko testu A. Jakie jest prawdopodobieństwo, że osoba ta rzeczywiście jest nosicielem wirusa, biorąc pod uwagę, że test A dał wynik pozytywny? (2 punkty)
(b) Powiedzmy, że osoba jest testowana na wirusa przy użyciu tylko testu B. Jakie jest prawdopodobieństwo, że osoba ta jest naprawdę nosicielem wirusa, biorąc pod uwagę, że test B dał wynik pozytywny? (2 punkty)
(c) Powiedzmy, że osoba jest badana na obecność wirusa przy użyciu obu testów. Jakie jest prawdopodobieństwo, że osoba ta jest rzeczywiście nosicielem wirusa, biorąc pod uwagę, że oba testy dały wynik pozytywny? (2 punkty)" initial-response="(a) Prawdopodobieństwo, że osoba jest rzeczywiście nosicielem wirusa, biorąc pod uwagę, że test A dał wynik pozytywny, wynosi 90%. ) Prawdopodobieństwo, że osoba jest naprawdę nosicielem wirusa, biorąc pod uwagę, że test B dał wynik pozytywny, wynosi 95%. c) Prawdopodobieństwo, że osoba jest naprawdę nosicielem wirusa, biorąc pod uwagę, że oba testy dały wynik pozytywny, wynosi 99,9%." max-tokens="256" box-rows="10" model-temp="0" top-p="0"></div>

Dane wyjściowe są **nieprawidłowe**!

Jeśli dodamy trochę kontekstu, jak np:

```
...
Wyjaśnijmy krok po kroku. Wzór na bayes to.
```
W modelu zostanie użyta właściwa formuła - Bayes.

<div trydyno-embed="" openai-model="text-davinci-003" initial-prompt="Rozważ dwa testy medyczne, A i B, na obecność wirusa. Test A jest w 90% skuteczny w rozpoznawaniu wirusa, gdy jest on obecny, ale ma 5% wskaźnik fałszywie pozytywny (wskazujący, że wirus jest obecny, gdy nie jest). Test B jest w 95% skuteczny w rozpoznawaniu wirusa, ale ma 10% wskaźnik fałszywie pozytywny. Oba testy stosują niezależne metody identyfikacji wirusa. Wirus jest przenoszony przez 2% wszystkich ludzi. a) Powiedzmy, że osoba jest testowana na wirusa przy użyciu tylko testu A. Jakie jest prawdopodobieństwo, że osoba ta rzeczywiście jest nosicielem wirusa, biorąc pod uwagę, że test A dał wynik pozytywny? (2 punkty)
(b) Powiedzmy, że osoba jest testowana na wirusa przy użyciu tylko testu B. Jakie jest prawdopodobieństwo, że osoba ta jest naprawdę nosicielem wirusa, biorąc pod uwagę, że test B dał wynik pozytywny? (2 punkty)
(c) Powiedzmy, że osoba jest badana na obecność wirusa przy użyciu obu testów. Jakie jest prawdopodobieństwo, że osoba ta jest rzeczywiście nosicielem wirusa, biorąc pod uwagę, że oba testy dały wynik pozytywny? (2 punkty)\NWyjaśnijmy to krok po kroku. Jako odpowiedź podaj wyrażenie liczbowe, nie zwracaj liczby. Wzór bayesowski to" initial-response="P(A|B) = P(B|A) * P(A) / P(B)‖ a) P(Virus|Test A Pozytywny) = P(Test A Pozytywny|Wirus) * P(Virus) / P(Test A Pozytywny) = (0.9 * 0.02) / (0.9 * 0.02 + 0.05 * 0.98)
 b) P(Virus|Test B Positive) = P(Test B Positive|Virus) * P(Virus) / P(Test B Positive) = (0.95 * 0.02) / (0,95 * 0,02 + 0,1 * 0,98)c) P(Virus|Test A Dodatni i Test B Dodatni) = P(Test A Dodatni i Test B Dodatni|Virus) * P(Virus) / P(Test A Dodatni i Test B Dodatni) = (0.9 * 0,95 * 0,02) / (0,9 * 0,95 * 0,02 + 0,05 * 0,1 * 0,98)" max-tokens="256" box-rows="10" model-temp="0" top-p="0"></div>

Co jest **prawdą**!

:::warning
Model GPT nie wykonuje dobrze operacji arytmetycznych. Możesz zauważyć, że podczas gdy napisane wyrażenie jest poprawione, obliczona liczba nie jest.

Spróbuj dodać frazę: `Podaj wyrażenie jako odpowiedź, nie liczbę`, aby wyłączyć obliczanie.


Możesz być zainteresowany [MRKL](https://learnprompting.org/docs/advanced_applications/mrkl)(@karpas2022mrkl), paradygmatem łączenia GPT z zewnętrznymi narzędziami, takimi jak kalkulatory, aby rozwiązać ten problem.
:::

Napisane przez [zeyuzhao](https://github.com/Zeyuzhao).

