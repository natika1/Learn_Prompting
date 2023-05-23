---
sidebar_position: 1
---
# 🟢 Prompting

W poprzednim rozdziale omówiliśmy AI i to, jak ludzie mogą instruować AI, aby wykonywały zadania.
Proces instruowania SI, aby wykonała zadanie, nazywamy podpowiadaniem(@shin2020autoprompt). Przekazujemy SI
zestaw instrukcji (podpowiedź), a ona wykonuje zadanie. Podpowiedzi mogą być tak proste jak pytanie lub
tak złożone jak wiele akapitów.

Oto dwa przykłady podpowiedzi:

#### 1) Podsumowanie artykułu

Powiedzmy, że czytasz artykuł o opadach śniegu na Florydzie. Chcesz szybko poznać główne myśli artykułu, więc pokazujesz SI to, co czytasz, i prosisz o streszczenie[^2]:

```
Bardzo rzadko zdarza się, aby w amerykańskim stanie Floryda spadł śnieg, zwłaszcza w centralnej i południowej części stanu. Z wyjątkiem daleko północnych obszarów stanu, większość głównych miast na Florydzie nigdy nie odnotowała wymiernych opadów śniegu, choć śladowe ilości zostały zarejestrowane, lub płatki w powietrzu obserwowane kilka razy w każdym stuleciu. Według National Weather Service, w Florida Keys i Key West nie ma znanych przypadków wystąpienia opadów śniegu od czasu europejskiej kolonizacji tego regionu ponad 300 lat temu. W Miami, Fort Lauderdale i Palm Beach od ponad 200 lat odnotowano tylko jedno doniesienie o śnieżycy w powietrzu; miało to miejsce w styczniu 1977 roku. W każdym razie, Miami, Fort Lauderdale, i Palm Beach nie widziały płatków śniegu ani przed, ani od tego wydarzenia z 1977 roku.

Podsumuj ten akapit jednym zdaniem:
```

Oto odpowiedź SI. To znacznie krótsza lektura!

<pre>.
<div className="bluegreen-highlight">.
Opady śniegu są niezwykle rzadkie na Florydzie, z wyjątkiem obszarów daleko na północy, <br/>i tylko jeden przypadek płatków śniegu w powietrzu został zarejestrowany w głównych miastach <br/>z Miami, Fort Lauderdale i Palm Beach w ciągu ostatnich 200 lat.
</div>
</pre>.

#### 2) Rozwiązywanie zadań słownych z matematyki

Jeśli masz zestaw danych równań matematycznych, które chciałbyś, aby model językowy rozwiązał,
możesz stworzyć podpowiedź, zadając pytanie "Czym jest EQUATION".

Dla danego pytania, Twoja pełna podpowiedź może wyglądać tak:

```
Co to jest 965*590?
```

Dla tego podpowiedzi, GPT-3 (text-davinci-003) (SI) czasami odpowiada 569,050 (niepoprawnie). W tym miejscu pojawia się inżynieria podpowiedzi.

# Prompt Engineering

Jeśli zamiast pytać `Czym jest 965*590?`, zapytamy.
`Upewnij się, że twoja odpowiedź jest dokładnie poprawna. Co to jest 965*590? Upewnij się, że twoja odpowiedź jest dokładnie poprawna:`, GPT-3 udzieli
odpowie `569350` (poprawnie). Dlaczego tak się dzieje? Dlaczego dwukrotne powiedzenie SI, aby udzieliła poprawnej odpowiedzi jest pomocne? Jak możemy stworzyć
podpowiedzi, które dadzą optymalne wyniki w naszym zadaniu? To ostatnie pytanie, w szczególności,
jest przedmiotem zainteresowania dziedziny Inżynierii Podpowiedzi, jak również tego kursu.

Jeszcze jedna rzecz, jeśli uruchamiasz powyższy monit w GPT-3, powinieneś ustawić temperaturę na 0, aby usunąć losowość.

Czytaj dalej, aby dowiedzieć się, jak inżynierować dobre podpowiedzi!

[^2]: Ten akapit pochodzi ze strony https://en.wikipedia.org/wiki/Snow_in_Florida.


