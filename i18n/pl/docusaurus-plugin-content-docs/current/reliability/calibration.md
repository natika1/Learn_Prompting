---
sidebar_position: 10
---

# 🔴 Kalibracja LLMs

Możliwe jest przeciwdziałanie niektórym tendencjom LLM poprzez kalibrację **rozkładów wyjściowych** (@zhao2021calibrate).
rozkładów wyjściowych**(@zhao2021calibrate).

**Co dokładnie oznacza kalibracja rozkładu wyjściowego?

Przejdźmy przez szybki przykład: Powiedzmy, że mamy zadanie %%sentiment analysis|sentiment analysis%% z dwoma możliwymi etykietami, `Positive` i `Negative`.
Zastanówmy się, co się stanie, gdy %%LLM|LLM%% zostanie poproszony o `Input: nothing Sentiment: `.
To wejście nie zawiera żadnego _kontekstu_, którego LLM może użyć do przewidywania sentymentu.
sentymentu, więc nazywane jest wejściem **bezkontekstowym**.

Ponieważ `nic` nie jest ani pozytywnym, ani negatywnym pojęciem, spodziewalibyśmy się, że LLM wyprowadzi prawdopodobieństwo około 0,5 zarówno dla `pozytywnego`, jak i `negatywnego`. Jednak często (i dla tego przykładu) tak nie będzie.
```
p("Pozytywny" | "Wkład: nic Sentyment:") = 0.9

p("Negatywny" | "Wejście: nic nie wnoszący sentyment:") = 0.1
```

Biorąc pod uwagę te prawdopodobieństwa etykiet dla bezkontekstowego wejścia, wiemy, że rozkład wyjściowy LLM
**rozkład wyjściowy** jest prawdopodobnie skrzywiony
w kierunku etykiety `Positive`. Może to spowodować, że LLM będzie faworyzował `Dodatni` dla wszystkich wejść, nawet jeśli wejście nie jest pozytywne.
dla wszystkich wejść, nawet jeśli wejście nie jest w rzeczywistości pozytywne.

Jeśli możemy w jakiś sposób **skalibrować** rozkład wyjściowy, tak że bezkontekstowe
wejścia mają przypisane prawdopodobieństwo 0,5 zarówno dla `Positive` jak i `Negative`,
wtedy możemy często usunąć tendencyjność w kierunku `Dodatniego` i LLM będzie bardziej wiarygodny
zarówno na wejściach bezkontekstowych, jak i na wejściach z kontekstem.

# Non-Technical Solution

Nietechnicznym rozwiązaniem tego problemu jest po prostu dostarczenie kilku przykładów strzałów, gdzie
bezkontekstowe exemplary są efektywnie przypisane do prawdopodobieństwa 0.5 dla obu
`Positive` i `Negative`.

Na przykład, możemy dostarczyć kilka następujących przykładów, które pokazują każdy bezkontekstowy
exemplar jest klasyfikowany zarówno jako `pozytywny` jak i `negatywny`:
```
Wejście: Nienawidzę tego filmu. Sentyment: Negatywny
Wejście: Uwielbiam ten film. Sentyment: Pozytywne
Wejście: N/A Sentyment: Pozytywne
Wejście: N/A Sentyment: Negatywny
Wejście: nic Sentyment: Pozytywne
Wejście: nic Sentyment: Negatywny
Wejście: Lubię jajka. Sentyment:
```

Według mojej wiedzy, to rozwiązanie nie było badane w literaturze i nie jestem pewien
jak dobrze działa w praktyce. Jest to jednak proste rozwiązanie, które pokazuje, co
kalibracja próbuje osiągnąć.

## Rozwiązanie techniczne

Innym rozwiązaniem tego problemu jest __kontekstowa kalibracja__(@zhao2021calibrate), gdzie
dostosowujemy specjalne parametry kalibracji, które zapewniają, że bezkontekstowe wejścia takie jak
` Wejście: nic Sentyment: ` mają przypisane prawdopodobieństwo około 0,5 dla obu etykiet.
Zauważ, że w praktyce metoda ta wykonuje kalibrację na wielu różnych bezkontekstowych wejściach (np. `Wejście: N/A Sentiment: `, `Wejście: [MASK] Sentiment: `). Uśrednia parametry kalibracji, które
działa najlepiej dla każdego wejścia bezkontekstowego, aby znaleźć najlepsze parametry kalibracji dla LLM.

### Przykład.

Przejdźmy przez przykład obliczania parametrów kalibracji dla jednego wejścia bezkontekstowego. Zauważ, że
ten przykład nie jest powtarzalny z GPT-3 ze względu na to, że nie można go ograniczyć do etykiet `Positive` i `Negative`.

Rozważmy ponownie powyższy przykład, w którym LLM przypisuje etykietom następujące prawdopodobieństwa
dla bezkontekstowego wejścia:

```
p("Pozytywny" | "Wejście: nic Sentyment:") = 0.9

p("Negatywny" | "Wejście: nic nie wnoszący sentyment:") = 0.1
```

Chcemy znaleźć pewien rozkład prawdopodobieństwa q taki, że.
```
q("Pozytywny" | "Wejście: nic Sentyment:") = 0.5

q("Negatywny" | "Wejście: nic nie czuć:") = 0.5
```

Zrobimy to poprzez stworzenie transformacji liniowej, która dostosowuje (kalibruje) prawdopodobieństwa
z $p$.

$Softmax}(W^p} + b)$

Równanie to przyjmuje oryginalne prawdopodobieństwa $^{p}$ i stosuje do nich wagi $W$ i skośność $b$.
do nich. Wagi $W$ i bias $b$ są parametrami kalibracyjnymi, które po zastosowaniu do prawdopodobieństw
bezkontekstowych przykładów, dadzą $^{q}$ = [0.5, 0.5].

#### Obliczanie W i b

Musimy w jakiś sposób obliczyć wagi $W$ i bias $b$. Jednym ze sposobów na to jest:

$W = ^{diag}(^{p})^{-1}$

$b = 0$

Chociaż definicja $W$ może wydawać się na początku nieco dziwna, ale jest to po prostu wzięcie odwrotności każdej wartości w $W$ w celu znalezienia $W$, które przekształci oryginalne prawdopodobieństwa $W$ w skalibrowane prawdopodobieństwa [0.5, 0.5].

Sprawdźmy, czy działa to dla powyższego przykładu:

$\^{p} = [0.9, 0.1]$

$W = ^diag}(^p})^{-1} = ^diag}([0.9, 0.1])^{-1}
= ¨begin{bmatrix}
   0.9 & 0 \
   0 & 0.1
\NKoniec{bmatrix}^{-1}
= ¨begin{bmatrix}
   1.11 & 0 \
   0 & 10
nd{bmatrix}$

$ = ™text{Softmax}(W^p} + b) = ™text{Softmax}(™bmatrix}
   1.11 & 0 \
   0 & 10
\Nend{bmatrix}*{[0,9, 0,1]} + 0)
= \NSoftmax}([1, 1])
=[0.5, 0.5]$

Jak wspomniano powyżej, wykonalibyśmy ten sam proces dla wielu różnych wejść bezkontekstowych i uśrednili parametry kalibracji, które działają najlepiej dla każdego wejścia bezkontekstowego, aby znaleźć najlepsze parametry kalibracji dla LLM. Oznacza to, że ostateczne parametry kalibracji prawdopodobnie nie odwzorują żadnego z wejść bezkontekstowych na dokładnie [0,5, 0,5].

### Inna metoda

Można też $b$ ustawić na $p}$, a $W$ na macierz tożsamości. Metoda ta sprawdza się
lepiej na zadaniach generowania niż klasyfikacji (@zhao2021calibrate).

## Takeaways

LLM są często predysponowane (stronnicze) do pewnych etykiet. Kalibracja może być wykorzystana do przeciwdziałania tej stronniczości.

