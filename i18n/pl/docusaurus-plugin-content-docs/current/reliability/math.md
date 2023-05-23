---
sidebar_position: 70
---

# 🟡 Matematyka

W trakcie tego kursu widzieliśmy wiele różnych metod podpowiadania, które mogą być używane do poprawy %%LLM|LLM%% zdolności matematycznych. Jedno z ostatnich podejść, MathPrompter(@imani2023mathprompter), łączy niektóre z tych metod (%%CoT|CoT prompting%%, %%PAL|PAL%%, itp.) w jedną technikę. Nadrzędną ideą jest rozbicie pytania matematycznego na terminy algebraiczne, a następnie użycie kodu Pythona do rozwiązania go na różne sposoby.

import math from '@site/docs/assets/math.png';

<div style={{textAlign: 'center'}}>.
  <img src={math} style={{width: "500px"}} />
</div>

MathPrompter posiada **cztery** kroki. Wyjaśnimy je na przykładzie poniższego problemu. Przykład jest wzięty bezpośrednio z pracy.

`tekst
P: W pewnej restauracji każdy posiłek dla dorosłych kosztuje 5$, a dzieci jedzą za darmo. Jeśli grupa 15 osób
osób, a 8 z nich to dzieci, ile kosztowałby posiłek dla tej grupy?
```

## Krok 1: Wygenerowanie szablonu algabraicznego

Pierwszym krokiem jest przypisanie zmiennej do każdej liczby w pytaniu. To pomaga, ponieważ pozwala na łatwiejsze przetłumaczenie pytania na abstrakcyjne pytanie matematyczne, a także na kod programistyczny.

Można to zrobić za pomocą kilku strzałów podpowiedzi:

<div trydyno-embed="" openai-model="text-davinci-003" initial-prompt="P: Zoo pobiera 12$ za bilet dla osoby dorosłej i pozwala dzieciom poniżej 5 roku życia wejść za darmo. Rodzina składająca się z 4 osób dorosłych i 2 dzieci poniżej 5 roku życia odwiedza zoo. Jaki jest całkowity koszt dla rodziny, aby wejść? W zoo każdy bilet dla dorosłych kosztuje A$, a dzieci poniżej 5 roku życia mogą wejść za darmo. Jeśli rodzina składająca się z B dorosłych i C dzieci poniżej 5 lat odwiedzi zoo, jaki jest całkowity koszt wejścia rodziny?  Jeśli klient kupi 2 pary butów i 3 pary skarpet, jaki jest całkowity koszt zakupu? W pewnym sklepie buty kosztują A$ za parę, a skarpetki B$ za parę. Jeśli klient kupi C par butów i D par skarpet, jaki jest całkowity koszt zakupu?\NMapping: {A: 60, B: 8, C: 2, D: 3} {A: 60, B: 8, C: 2, D: 3} W pewnej restauracji każdy posiłek dla osoby dorosłej kosztuje 5 dolarów, a dzieci jedzą za darmo. Gdyby przyszła 15-osobowa grupa, a 8 osób to dzieci, ile kosztowałby posiłek dla tej grupy?" initial-response="Qt: W pewnej restauracji każdy posiłek dla dorosłych kosztuje $A, a dzieci jedzą za darmo. Jeśli weszła grupa osób B, a C to dzieci, ile kosztowałoby zjedzenie posiłku przez tę grupę?" initial-response="Qt: Qt: W restauracji każdy posiłek dla dorosłych kosztuje A, a dzieci jedzą za darmo: {A: 5, B: 15, C: 8}" max-tokens="256" box-rows="14" model-temp="0" top-p="0">.
    <noscript>Failed to load Dyno Embed: JavaScript musi być włączony</noscript>.
</div>

# Krok 2: Math Prompts

Celem tego kroku jest sformułowanie problemu zarówno jako twierdzenia algabrycznego, jak i jako kodu Pythona. Ten krok ma dwie jednoczesne podpowiedzi, które pomagają w podaniu zróżnicowanych reprezentacji problemu.

### 2a: Stwierdzenie algebraiczne

Możemy w kilku ujęciach zachęcić LLM do przedstawienia problemu matematycznego jako twierdzenia algebraicznego. Robimy to prosząc LLM o wygenerowanie formatu odpowiedzi, zaczynając od "Odpowiedź =".

<div trydyno-embed="" openai-model="text-davinci-003" initial-prompt="Qt: W pewnym zoo każdy bilet dla dorosłych kosztuje A$, a dzieci poniżej 5 roku życia mogą wejść za darmo. Jeśli rodzina składająca się z B dorosłych i C dzieci poniżej 5 lat odwiedza zoo, jaki jest całkowity koszt wejścia rodziny?": {A: 12, B: 4, C: 2} Napisz równanie matematyczne i wygeneruj format odpowiedzi zaczynający się od 'Odpowiedź ='Odpowiedź = A * BQt: W pewnym sklepie buty kosztują A$ za parę, a skarpetki B$ za parę. Jeśli klient kupi C par butów i D par skarpet, jaki jest całkowity koszt zakupu?\NMapping: {A: 60, B: 8, C: 2, D: 3} Napisz równanie matematyczne i wygeneruj format odpowiedzi zaczynający się od 'Odpowiedź ='\NPodpowiedź = A * C + B * D: W pewnej restauracji każdy posiłek dla dorosłych kosztuje A$, a dzieci jedzą za darmo. Gdyby przyszła grupa osób B, a C to dzieci, ile kosztowałoby jedzenie dla tej grupy? {A: 5, B: 15, C: 8} Napisz równanie matematyczne i wygeneruj odpowiedź format "Odpowiedź ="" initial-response="Odpowiedź = A * B - A * C" max-tokens="256" box-rows="14" model-temp="0" top-p="0">.
    <noscript>Failed to load Dyno Embed: JavaScript musi być włączony</noscript>.
</div>

### 2b: Kod Pythona

Możemy również poprosić %%LLM|LLM%% o wygenerowanie kodu Pythona, który rozwiązuje problem. Odbywa się to poprzez poproszenie LLM o wygenerowanie funkcji Pythona.

<div trydyno-embed="" openai-model="text-davinci-003" initial-prompt="Qt: W pewnym zoo każdy bilet dla dorosłych kosztuje A$, a dzieci poniżej 5 roku życia mogą wejść za darmo. Jeśli rodzina składająca się z B dorosłych i C dzieci poniżej 5 lat odwiedza zoo, jaki jest całkowity koszt wejścia rodziny?": {A: 12, B: 4, C: 2} Napisz funkcję w Pythonie, która zwraca odpowiedź.\NNNiech zoo_cost(A, B, C):\Nzwróć A * B \NKoszt: W pewnym sklepie buty kosztują A$ za parę, a skarpetki B$ za parę. Jeśli klient kupi C par butów i D par skarpet, jaki jest całkowity koszt zakupu? Napisz w Pythonie funkcję, która zwróci odpowiedź.\Nndef store_cost(A, B, C, D):
 return (A * C) + (B * D)
Qt: W pewnej restauracji każdy posiłek dla dorosłych kosztuje A$, a dzieci jedzą za darmo. Gdyby przyszła grupa osób B, a C to dzieci, ile kosztowałoby jedzenie dla tej grupy? Napisz w Pythonie funkcję, która zwróci odpowiedź." initial-response="def restaurant_cost(A, B, C):\N return A * (B - C)" max-tokens="256" box-rows="14" model-temp="0" top-p="0">.
    <noscript>Failed to load Dyno Embed: JavaScript musi być włączony</noscript>.
</div>

### Odpowiedź Generacja

Teraz możemy użyć Mapowania, które wygenerowaliśmy wcześniej, aby automatycznie wypełnić zmienne.

`tekst
Odwzorowanie: {A: 5, B: 15, C: 8}
```

Algabraic:
`tekst.
Odpowiedź = 5 * 15 - 5 * 8
```

Funkcja w języku Python:
``python
def restaurant_cost(A=5, B=15, C=8):
  return A * (B - C)
```

Możemy ocenić oba te elementy używając Pythona.

Algebraiczny:
``python``
>>> eval("5 * 15 - 5 * 8")
35
```

Funkcja w języku Python:
``python``
>>> restaurant_cost()
35
```

# Step 4: Self-Consistency

Wreszcie, wykorzystamy %%Self-Consistency|self_consistency%%, aby powtórzyć powyższy proces wiele razy (~5), a następnie weźmiemy odpowiedź większości.

## Wniosek

MathPrompter zgłasza 92,5% dokładności na zbiorze danych MultiArith(@roy-roth-2015-solving). Sukces tej techniki jest doskonałym przykładem tego, jak **ty** jako inżynier podpowiadający możesz wziąć metody, których nauczyłeś się w trakcie tego kursu i połączyć je, aby poradzić sobie z większymi problemami.

