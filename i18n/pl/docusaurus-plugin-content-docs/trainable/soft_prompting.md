---
sidebar_position: 1
---

# 🔴 Soft Prompts

Dostrajanie podpowiedzi (@lester2021power), alternatywa dla dostrajania modelu (@khashabi2021prompt), zamraża wagi modelu i aktualizuje parametry podpowiedzi. Wynikowa podpowiedź jest "miękką podpowiedzią".


import Image from "../assets/prompt_tuning.png";

<div style={{textAlign: 'center'}}>.
  <img src={Image} style={{width: "500px"}} />
</div>

<div style={{textAlign: 'center'}}>
Model Tuning vs Prompt Tuning (Lester et al.)
</div>

Powyższy obrazek kontrastuje strojenie modelu z dostrajaniem podpowiedzi.
W strojeniu modelu, dostrajasz ten sam model na różnych zadaniach. To daje Ci
kilka różnych modeli, z którymi niekoniecznie można łatwo łączyć wejścia.

Z drugiej strony, strojenie podpowiedzi pozwala używać tego samego modelu do wszystkich zadań. Ty
Wystarczy tylko dołączyć odpowiednie podpowiedzi w czasie wnioskowania, co ułatwia
różnych zadań. Jest to prawie taka sama zaleta, jaką ma zwykłe podpowiadanie
ma. Dodatkowo, miękkie podpowiedzi wytrenowane dla jednego modelu w wielu zadaniach
w wielu zadaniach będą często miały tę samą długość tokena.

## Jak to działa

Aby zrozumieć podstawową logikę stojącą za miękkimi podpowiedziami, pomyślmy o tym, jak działa **modelowe wnioskowanie**
na danej podpowiedzi: `Co to jest 2+2?`.

1) Może być tokenizowane jako `co, 's, 2, +, 2, ?`.

2) Następnie każdy token zostanie przekonwertowany na wektor wartości.

3) Ten wektor wartości można uznać za parametry modelu. Model może być dalej
trenować, dostosowując jedynie wagi tych podpowiedzi.

Zauważ, że gdy tylko zaczniemy aktualizować te wagi, wektory tokenów nie będą już
już nie odpowiadają rzeczywistym osadzeniom ze słownika.

# Wyniki

Prompt tuning sprawdza się lepiej w przypadku większych modeli. Większe modele wymagają również mniej
soft tokenów zachęty. Niezależnie od tego, więcej niż 20 tokenów nie daje znaczącego wzrostu wydajności.

