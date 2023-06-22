---
sidebar_position: 90
---

# 📙 Słownik Pojęć

Na tej stronie znajduje się lista terminów i pojęć, których będziemy używać w trakcie tego kursu.

#### Duże modele językowe (LLM), wstępnie przygotowane modele językowe (PLM) (@branch2022evaluating), modele językowe (LM) i modele fundamentalne

Wszystkie te terminy odnoszą się mniej więcej do tego samego: dużych SI (sieci neuronowych), które zazwyczaj zostały wytrenowane
na ogromnej ilości tekstu.

#### Maskowane modele językowe (MLM)

MLM to rodzaj modelu NLP, który posiada specjalny token, zwykle `[MASK]`, który jest
zastąpiony słowem ze słownika. Następnie model przewiduje słowo, które
zostało zamaskowane. Na przykład, jeśli zdanie brzmi "Pies jest [MASK] kotem", model
przewidzi "gonienie" z dużym prawdopodobieństwem.

#### Etykiety

Pojęcie etykiet najlepiej zrozumieć na przykładzie.

Powiedzmy, że chcemy sklasyfikować pewne Tweety jako średnie lub nie średnie. Jeśli mamy listę tweetów i odpowiadającą im
odpowiadającą im *etykietę* (średnia lub nie średnia), możemy wytrenować model do klasyfikowania
czy tweety są średnie czy nie. Etykiety są zazwyczaj tylko możliwościami dla
klasyfikacji.

#### Label Space

Wszystkie możliwe etykiety dla danego zadania ("średnia" i "nie średnia" dla powyższego przykładu).

#### Analiza nastrojów
 
Analiza sentymentów to zadanie polegające na klasyfikacji tekstu na pozytywne, negatywne lub inne sentymenty.

#### "Model" vs. "AI" vs. "LLM"

Terminy te są używane w tym kursie nieco zamiennie, ale nie zawsze oznaczają to samo.
nie zawsze oznaczają to samo. LLM są rodzajem AI, jak zauważono powyżej, ale nie wszystkie AI są LLM.
Kiedy wspominamy o modelach w tym kursie, odnosimy się do modeli AI. Jako takie, w tym kursie,
można uznać, że terminy "model" i "AI" są zamienne.

#### Uczenie maszynowe (ML)

ML to dziedzina nauki, która skupia się na algorytmach, które
potrafią uczyć się na podstawie danych. ML jest poddziedziną AI.

#### Werbalizator

W klasyfikacji, werbalizatory są mapami z etykiet do słów w
słownictwie modelu językowego (@schick2020exploiting). Na przykład, rozważmy
wykonanie klasyfikacji sentymentu z następującą podpowiedzią:

``tekst``
Tweet: "I love hotpockets"
Jaki jest sentyment tego tweeta? Powiedz "pos" lub "neg".
```

Tutaj werbalizator jest odwzorowaniem z etykiet konceptualnych `pozytywnych` i `negatywnych` na tokeny `pos` i `neg`.

#### Reinforcement Learning from Human Feedback (RLHF)

RLHF jest metodą precyzyjnego dostrajania LLM zgodnie z danymi dotyczącymi preferencji człowieka.

<!-- %%RemarkAutoGlossary::list_all% -->.


