---
sidebar_position: 2
---

# 🔴 Interpretowalne, miękkie propsy

Miękkie podpowiedzi są sekwencją wektorów, które
nie odpowiadają żadnym rzeczywistym tokenom w słowniku. To sprawia, że trudno jest
zinterpretować podpowiedź. Możemy jednak próbować to zrobić
poprzez mapowanie wektorów do najbliższych im tokenów w słowniku. Jednakże, projektowane
miękkie podpowiedzi są często błędne; mogą rozwiązywać
zadania, ale są rzutowane na dowolne tokeny w słowniku (@khashabi2021prompt).

Na przykład, jeśli trenujemy na pytaniach matematycznych, takich jak GSM8K(@cobbe2021training),
możemy zacząć od podpowiedzi `Jesteś matematykiem. Rozwiąż to pytanie:`.
Jeśli wykonamy na nim strojenie podpowiedzi, a następnie rzutujemy je z powrotem na przestrzeń tokenów, możemy
zostaniemy z czymś bezsensownym jak `A bus is a bus. Do thing here:`. Często jest tak, że
Często zdarza się, że miękki podpowiedź, która mapuje do tego nonsensownego podpowiedzi może zapewnić lepszą wydajność na zadanie!

# The Waywardness Hypothesis

Khashabi et al.(@khashabi2021prompt) proponują tę niesamowitą hipotezę. Mówi ona.
że biorąc pod uwagę zadanie, dla każdej dyskretnej podpowiedzi docelowej, istnieje
ciągły podpowiedź, która projektuje do niego, jednocześnie wykonując dobrze zadanie.

Oznacza to, że biorąc pod uwagę 1000 różnych zadań, istnieje 1000 różnych
performatywnych podpowiedzi miękkich (po jednej dla każdego zadania), które odpowiadają tej samej podpowiedzi dyskretnej.

## Ryzyko interpretacyjne

Wykorzystują Hipotezę Drogi, aby podkreślić szereg zagrożeń, które pojawiają się
przy interpretacji miękkich podpowiedzi. W szczególności, miękka zachęta może być rzutowana na
dyskretną podpowiedź, która daje mylące intencje.

Rozważmy miękką podpowiedź dla rankingu CV. Po projekcji w tokenspace, może to być
być `Menedżer zatrudniający. Oceń dobre CV:`. To wydaje się przyzwoite, może trochę brakuje
w gramatyce. Jednakże, token `good` może mieć podobną projekcję jak token dla `white`, i tam
może istnieć ukryte uprzedzenie w podpowiedzi. Używając nieco innej metody projekcji,
możemy skończyć z `You hiring manager. Uszereguj białe CV:`. To jest oczywiście całkiem
inne, i może mieć znaczące implikacje.

Podobnie jak w przypadku interpretacji zwykłej dyskretnej podpowiedzi, powinniśmy być wyjątkowo
świadomi tendencyjności, która może być obecna w podpowiedzi. Musimy być szczególnie
ostrożność z miękkimi podpowiedziami, ponieważ są one trudniejsze do zinterpretowania.


