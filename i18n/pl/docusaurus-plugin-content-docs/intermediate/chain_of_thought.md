---
sidebar_position: 3
locale: en-us
styl: chicago
---

# 🟢 Chain of Thought Prompting

Łańcuch myśli (CoT) (@wei2022chain) jest niedawno opracowaną metodą podpowiadania.
która zachęca LLM do wyjaśnienia swojego rozumowania. Poniższy obrazek(@wei2022chain)
pokazuje %%few shot standard prompt|few shot standard prompt%% (po lewej) w porównaniu do chain of thought prompt (po prawej).


import CoTExample from '@site/docs/assets/chain_of_thought_example.png';

<div style={{textAlign: 'center'}}>.
  <img src={CoTExample} style={{szerokość: "750px"}} />
</div>

<div style={{textAlign: 'center'}}>
Regular Prompting vs CoT (Wei et al.)
</div>

Główna idea CoT polega na tym, że pokazując LLM kilka strzałów %%exemplars|exemplars%%, gdzie proces rozumowania jest wyjaśniony w exemplars, LLM pokaże również proces rozumowania.
w których proces rozumowania jest wyjaśniony w przykładach, LLM pokaże również proces rozumowania
podczas odpowiadania na podpowiedź. To wyjaśnienie rozumowania często prowadzi do bardziej dokładnych
wyników.

## Przykład.

Oto kilka demek. Pierwsze pokazuje GPT-3 (davinci-003)
nie radzi sobie z rozwiązaniem prostego zadania słownego. Drugie pokazuje GPT-3 (davinci-003), który z powodzeniem rozwiązuje to samo zadanie, używając podpowiedzi CoT.

#### Nieprawidłowo

<div trydyno-embed="" openai-model="text-davinci-003" initial-prompt="Który sposób dotarcia do pracy jest szybszy?" initial-response="Opcja 1: Jedź 1000 minutowym autobusem, potem półgodzinnym pociągiem, a na koniec 10 minut jazdy rowerem.\Opcja 2: Jedź 800 minut autobusem, potem pół godziny pociągiem, a na koniec 30 minut rowerem." initial-response="Opcja 1 jest szybszym sposobem dotarcia do pracy." max-tokens="256" box-rows="7" model-temp="0" top-p="0"></div>

#### Prawidłowo

<div trydyno-embed="" openai-model="text-davinci-003" initial-prompt="Który sposób dotarcia do domu jest szybszy?\NOpcja 1: Weź 10 minutowy autobus, następnie 40 minutowy autobus, a na koniec 10 minutowy pociąg.\NOpcja 2: Weź 90 minutowy pociąg, następnie 45 minutową przejażdżkę rowerem, a na koniec 10 minutowy autobus.\NOpcja 1 zajmie 10+40+10 = 60 minut.\NOpcja 2 zajmie 90+45+10=145 minut.\NPonieważ opcja 1 trwa 60 minut, a opcja 2 145 minut, opcja 1 jest szybsza.\NKtóra z nich jest szybszym sposobem dotarcia do pracy? \NOpcja 1: Jedź 1000 minut autobusem, potem półgodzinnym pociągiem, a na koniec 10 minut rowerem.\NOpcja 2: Jedź 800 minut autobusem, potem godzinnym pociągiem, a na koniec 30 minut rowerem." initial-response="Opcja 1 zajmie 1000+30+10 = 1040 minut.
Opcja 2 zajmie 800+60+30 = 890 minut.
Ponieważ opcja 2 zajmuje 890 minut, a opcja 1 zajmuje 1040 minut, opcja 2 jest szybsza." max-tokens="256" box-rows="18" model-temp="0" top-p="0"></div>

## Wyniki

Wykazano, że CoT jest skuteczny w poprawianiu wyników w zadaniach np.
arytmetyka, rozumowanie i rozumowanie symboliczne (@wei2022chain).
W szczególności, podpowiadany PaLM 540B(@chowdhery2022palm) osiąga 57% dokładności rozwiązania
w GSM8K(@cobbe2021training) (SOTA w tym czasie).

import PromptedPaLM from '@site/docs/assets/prompted_palm.png';

<div style={{textAlign: 'center'}}>.
  <img src={PromptedPaLM} style={{width: "300px"}} />
</div>

<div style={{textAlign: 'center'}}>
Porównanie modeli na benchmarku GSM8K (Wei i in.)
</div>

## Ograniczenia

Co ważne, według Wei i in. "CoT daje wzrost wydajności tylko wtedy, gdy jest stosowany z modelami o parametrach ∼100B". Mniejsze modele pisały nielogiczne łańcuchy myślowe, co prowadziło do gorszej dokładności niż standardowe podpowiadanie. Modele zazwyczaj uzyskują wzrost wydajności dzięki podpowiedziom CoT w sposób proporcjonalny do wielkości modelu.


## Notes

Żadne modele językowe nie zostały ~~hurt~~ finetuned w procesie pisania tego rozdziału 😊.

