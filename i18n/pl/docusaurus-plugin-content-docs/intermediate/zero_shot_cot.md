---
sidebar_position: 4
---

# 🟢 Zero Shot Chain of Thought


Zero Shot Chain of Thought (Zero-shot-CoT) prompting (@kojima2022large) jest
kontynuacją %%CoT prompting|CoT prompting%% (@wei2022chain), która wprowadza niesamowicie
prostą podpowiedź zerowego strzału. Odkrywają, że poprzez dołączenie słów "**Pomyślmy krok po kroku
krok po kroku.**" na końcu pytania, LLM są w stanie wygenerować łańcuch
myśli, które odpowiadają na pytanie. Z tego łańcucha myśli, są w stanie
wydobyć bardziej dokładne odpowiedzi.

import ZSImage from '@site/docs/assets/zero_shot.png';

<div style={{textAlign: 'center'}}>.
  <img src={ZSImage} style={{width: "500px"}} />
</div>

<div style={{textAlign: 'center'}}>
Zero Shot CoT (Kojima et al.)
</div>

Technicznie rzecz biorąc, pełny proces Zero-shot-CoT obejmuje dwie oddzielne podpowiedzi/kompletacje.
Na poniższym obrazku, górna bańka po lewej stronie generuje łańcuch myśli, podczas gdy górna bańka po
prawej przyjmuje dane wyjściowe z pierwszej podpowiedzi (w tym samą pierwszą podpowiedź),
i wydobywa odpowiedź z łańcucha myśli. Ta druga zachęta to zachęta typu _self augmented_.

import ZSProcessImage from '@site/docs/assets/zero_shot_example.png';

<div style={{textAlign: 'center'}}>.
  <img src={ZSProcessImage} style={{szerokość: "500px"}} />
</div>

<div style={{textAlign: 'center'}}>
Pełny proces Zero Shot CoT (Kojima i in.)
</div>

## Przykład.

Oto kilka dem (które wykonują tylko ekstrakcję rozumowania). To pierwsze
pokazuje GPT-3 (davinci-003), który nie radzi sobie z prostym pytaniem matematycznym, podczas gdy drugie demo używa podpowiedzi
Zero-shot-CoT i pomyślnie rozwiązuje problem. Zapraszamy do wprowadzenia swojego
OpenAI API key (kliknij Generate) i pobaw się przykładami. Zwróć uwagę, o ile prostsze
podpowiedź Zero-shot-CoT jest prostsza od podpowiedzi CoT.

#### Nieprawidłowo

<div trydyno-embed="" openai-model="text-davinci-003" initial-prompt="Jeśli Jan ma 5 gruszek, potem zjada 2, i kupuje jeszcze 5, a potem daje 3 swojemu przyjacielowi, to ile ma gruszek?" initial-response="Jan ma 8 gruszek." max-tokens="256" box-rows="3" model-temp="0.7" top-p="1"></div>


#### Prawidłowo

<div trydyno-embed="" openai-model="text-davinci-003" initial-prompt="Jeśli Jan ma 5 gruszek, następnie zjada 2, i kupuje jeszcze 5, po czym daje 3 swojemu przyjacielowi, to ile ma gruszek?" initial-response="Jan zaczyna z 5 gruszkami. Zjada 2 gruszki, zostawiając mu 3 gruszki. Kupuje jeszcze 5 gruszek, co daje mu łącznie 8 gruszek. Oddaje 3 gruszki swojemu przyjacielowi, pozostawiając mu tylko 5 gruszek." max-tokens="256" box-rows="5" model-temp="0.7" top-p="1"></div>

## Wyniki
Zero-shot-CoT był również skuteczny w poprawie wyników w zadaniach arytmetycznych, commonsense,
i rozumowania symbolicznego. Jednak, co nie jest zaskakujące, zazwyczaj nie był tak
jak podpowiedzi CoT. Ważnym przypadkiem użycia Zero-shot-CoT jest uzyskanie
kilku przykładów dla podpowiedzi CoT jest trudne.

# Ablations of Interest

Kojima i in. eksperymentują z wieloma różnymi podpowiedziami typu "Zero-shot-CoT
(np. "Rozwiążmy ten problem dzieląc go na kroki." lub "Pomyślmy o tym logicznie."), ale stwierdzają, że "Myślmy krok po kroku" jest najbardziej efektywne dla ich
wybranych zadań.



## Notes

Krok ekstrakcji często musi być specyficzny dla danego zadania, co czyni Zero-Shot-CoT mniej
generalizacją, niż wydaje się to na początku.

Anegdotycznie stwierdziłem, że podpowiedzi w stylu Zero-shot-CoT są czasami skuteczne
w poprawieniu długości ukończenia zadań generatywnych. Na przykład, rozważ
standardową podpowiedź `Napisz historię o żabie i grzybie, które zostają przyjaciółmi.`
Dodanie słów `Pomyślmy krok po kroku.` na końcu tej zachęty prowadzi do
znacznie dłuższe zakończenie.



