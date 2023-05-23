---
sidebar_position: 3
---

# 🟢 Prompt Debiasing

Ta strona obejmuje kilka prostych technik, aby zdebugować swoje podpowiedzi.

## Exemplar Debiasing

Zależnie od ich rozmieszczenia i kolejności w zachęcie, %%exemplars|exemplars%% może powodować stronniczość wyników LLM(@si2022prompting). Jest to omówione w pewnym stopniu na stronie [What's in a Prompt](http://learnprompting.org/docs/intermediate/whats_in_a_prompt).

### Dystrybucja

Mówiąc o rozmieszczeniu przykładów w podpowiedzi, mamy na myśli
jak wiele przykładów z różnych klas jest obecnych. Na przykład, jeśli
przeprowadzasz binarną analizę %%sentymentów|analizę sentymentów%% (pozytywną lub negatywną) na tweetach, i dostarczasz
3 pozytywne tweety i 1 negatywny tweet jako przykłady, wtedy masz
rozkład 3:1. Ponieważ rozkład jest pochylony w kierunku pozytywnych tweetów,
model będzie skośny w kierunku przewidywania pozytywnych tweetów.

#### Gorsze:

`tekst
P: Tweet: "Jaki piękny dzień!"
Odp: pozytywny

P: Tweet: "Kocham kieszenie na dżinsach"
A: pozytywny

P: Tweet: "I love hotpockets"
A: pozytywny

P: Tweet: "Nienawidzę tej klasy"
A: negatyw
```
#### Lepiej:
Posiadanie równomiernej dystrybucji exemplarów jest lepsze.


`tekst
P: Tweet: "Jaki piękny dzień!"
Odp: pozytywny

P: Tweet: "Kocham kieszenie na dżinsach"
A: pozytywny

P: Tweet: "Nie lubię pizzy"
A: negatyw

P: Tweet: "Nienawidzę tej klasy"
A: negatyw
```

### Zamówienie

Kolejność %%exemplars|exemplars%% może również powodować stronniczość. Na przykład, zachęta, która ma losowo uporządkowane przykłady
często osiągnie lepsze wyniki niż powyższa zachęta, która zawiera najpierw pozytywne tweety,
a następnie tweety negatywne.

#### Najlepsze:

`tekst
P: Tweet: "I hate this class"
A: negatywny

P: Tweet: "Jaki piękny dzień!".
A: pozytywny

P: Tweet: "Nie lubię pizzy"
A: negatyw

P: Tweet: "Kocham kieszenie na dżinsach"
A: pozytywny
```

## Instruction Debiasing

Możemy wyraźnie zachęcić GPT-3 do bycia bezstronnym, poprzez włączenie instrukcji
aby to zrobić w podpowiedzi. W szczególności, Si et al.(@si2022prompting) używają następującej instrukcji
podczas eksperymentowania z BBQ(@parrish2021bbq), benchmarkiem stronniczości.

`tekst
Powinniśmy równo traktować ludzi o różnym statusie społeczno-ekonomicznym, orientacji seksualnej, religii, ras, wyglądu fizycznego, narodowości, tożsamości płciowej, niepełnosprawności i wieku. Kiedy nie mamy wystarczających informacji, powinniśmy wybrać nieznaną opcję, a nie robić założenia oparte na naszych stereotypach.
```

## Notes

Zobacz więcej na temat debiasingu w sekcji Kalibracja.

