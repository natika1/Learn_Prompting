---
sidebar_position: 2
---
# 🟢 Dawanie instrukcji.

Jedną z najprostszych metod podpowiadania jest po prostu wydawanie instrukcji. Widzieliśmy już prostą instrukcję
w poprzedniej części (`Czym jest 1 000 000 * 9 000? Upewnij się, że umieściłeś odpowiednią ilość zer, nawet jeśli jest ich dużo:`). Jednak,
współczesne SI potrafią wykonywać znacznie bardziej złożone instrukcje.

Poniżej znajduje się przykład, który jest interaktywnym embedem Dyno. Jeśli go nie widzisz, upewnij się, że włączyłeś Javascript w swojej przeglądarce. Ponieważ jest to interaktywne demo, możesz edytować tekst i nacisnąć `Generate`, aby ponownie uruchomić AI.

#### Przykład 1

<div trydyno-embed="" openai-model="text-davinci-003" initial-prompt="Użytkownik wprowadził swoje imię i nazwisko do formularza. Nie wiemy, w jakiej kolejności jest jego imię/ostatnie imię, ale potrzebujemy, aby było w formacie 'Last, First'. Przekształć to w następujący sposób:" initial-response="Doe, John" max-tokens="256" box-rows="7" model-temp="0" top-p="0"></div>

<br/>AI jest w stanie łatwo rozwiązać ten problem. Używając podpowiedzi instrukcji, może rozwiązać wiele innych
prostych i bardziej złożonych problemów.

#### Przykład 2

Oto bardziej skomplikowany przykład[^1]:

```
Przeczytaj poniższy e-mail sprzedażowy. Usuń wszelkie informacje umożliwiające identyfikację osoby (PII),
i zamień je na odpowiedni placeholder. Na przykład, zastąp nazwisko "John Doe"
na "[NAME]".

Cześć John,

Piszę do Pana, ponieważ zauważyłem, że niedawno zakupił Pan nowy samochód. Jestem sprzedawcą
w lokalnym salonie (Cheap Dealz), i chciałem dać ci znać, że mamy świetną ofertę na nowy
car. Jeśli jest Pan zainteresowany, proszę dać mi znać.

Dzięki,

Jimmy Smith

Telefon: 410-805-2345
Email: jimmysmith@cheapdealz.com
```

Oto [odpowiedź SI](https://beta.openai.com/playground/p/002o3gmji5jlwUfRq9d7KDHc?model=text-davinci-003):

``text``
// highlight-start
Cześć [NAME],

Piszę do Pana, ponieważ zauważyłem, że niedawno zakupił Pan nowy samochód. Jestem sprzedawcą
w lokalnym salonie ([DEALERSHIP]) i chciałem poinformować Pana, że mamy świetną ofertę na nowy samochód.
samochód. Jeśli jest Pan zainteresowany, proszę dać mi znać.

Dzięki,

[SALESPERSON]

Telefon: [NUMER TELEFONU]
Email: [ADRES E-MAIL]
// highlight-end
```

Bardzo fajne jest to, że model potrafi ekstrapolować z instrukcji. Na przykład, wie
zamienić `Cheap Dealz` na `[DEALERSHIP]` i `Jimmy Smith` na `[SALESPERSON]`, mimo że
nie powiedzieliśmy mu tego wprost.

[^1]: Umożliwienie AI usuwania PII z tekstu jest obiecującym podejściem, ale powinno być stosowane z niezwykłą ostrożnością, ponieważ może popełniać błędy.


## Notes

🚧 Ta strona wymaga cytowania 🚧

