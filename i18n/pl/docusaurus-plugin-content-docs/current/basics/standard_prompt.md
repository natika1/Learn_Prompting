---
sidebar_position: 3
---

# 🟢 A "Standard" Prompt

Do tej pory słyszeliśmy o kilku różnych formatach podpowiedzi.
Podążając za Kojima et al. (@kojima2022large), będziemy odnosić się do podpowiedzi, które składają się
składające się wyłącznie z pytania, jako "standardowe" podpowiedzi. Uważamy również, że podpowiedzi, które składają się wyłącznie z
pytania, które są w formacie QA, są "standardowymi" podpowiedziami.

#### Dlaczego miałoby mnie to obchodzić?

Wiele artykułów, na które się powołujemy, używa tego terminu. Definiujemy go, abyśmy mogli omówić
nowe typy podpowiedzi w przeciwieństwie do standardowych podpowiedzi.

### Dwa przykłady standardowych podpowiedzi:


_Standard Prompt_
```
Co jest stolicą Francji?
```

_Standardowa prompta w formacie QA_.
```
P: Co jest stolicą Francji?

A:
```

# Few Shot Standard Prompts

Nieliczne wystrzałowe standardowe podpowiedzi(@liu2021pretrain) to właśnie standardowe podpowiedzi, które mają _przykłady_.
w nich. Przykłady to przykłady zadania, które dana podpowiedź próbuje rozwiązać,
które są zawarte w samej zachęcie (@brown2020language). W badaniach, nieliczne nakręcone standardowe podpowiedzi
są czasem określane po prostu jako standardowe podpowiedzi (choć w tym przewodniku staramy się tego nie robić).

### Dwa przykłady kilku strzałów standardowych podpowiedzi:

_Kilka strzałów Standard Prompt_.

```
Co jest stolicą Hiszpanii?
Madryt
Co jest stolicą Włoch?
Rzym
Co jest stolicą Francji?
```

_Few Shot Standard Prompt w formacie QA_.
```
P: Co jest stolicą Hiszpanii?
A: Madryt
Q: Co jest stolicą Włoch?
A: Rzym
Q: Co jest stolicą Francji?
A:
```

Podpowiedzi typu "kilka strzałów" ułatwiają uczenie "kilku strzałów" AKA "w kontekście", co jest
zdolność do uczenia się bez aktualizacji parametrów (@zhao2021calibrate).



