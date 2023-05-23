---
sidebar_position: 3
---

# 🟡 LLMs that Reason and Act

ReAct(@yao2022react)(reason, act) jest paradygmatem umożliwiającym modelom językowym rozwiązywanie złożonych zadań za pomocą rozumowania w języku naturalnym.
zadań z wykorzystaniem rozumowania w języku naturalnym. ReAct jest zaprojektowany dla zadań, w których LLM jest
może wykonywać pewne działania. Na przykład, jak w systemie MRKL, LLM może być w stanie
wchodzić w interakcje z zewnętrznymi interfejsami API w celu uzyskania informacji. Po zadaniu pytania, moduł LLM
może zdecydować się na wykonanie akcji w celu pobrania informacji, a następnie odpowiedzieć na pytanie
na podstawie uzyskanych informacji.

Systemy ReAct mogą być pomyślane jako systemy MRKL, z dodatkową zdolnością do **rozumowania
o** działaniach, które mogą wykonać.

Zbadaj poniższy obraz. Pytanie w górnej ramce pochodzi z HotPotQA(@yang2018hotpotqa),
zbioru pytań, które wymagają złożonego rozumowania. ReAct jest w stanie odpowiedzieć na pytanie poprzez
najpierw rozumowanie o pytaniu (Myśl 1), a następnie wykonanie akcji (Czyn 1), aby wysłać zapytanie do Google.
do Google. Następnie otrzymuje obserwację (Obs 1) i kontynuuje tę pętlę myśli, działań, obserwacji
aż do osiągnięcia konkluzji (Akt 3).


import react_qa from '@site/docs/assets/react_qa.png';

<div style={{textAlign: 'center'}}>.
  <img src={react_qa} style={{szerokość: "500px"}} />
</div>

<div style={{textAlign: 'center'}}>
System ReAct (Yao i in.)
</div>


Czytelnicy znający uczenie wzmacniające mogą rozpoznać ten proces jako podobny do klasycznej
RL pętli stanu, działania, nagrody, stanu,... ReAct dostarcza pewnej formalizacji dla
w swoim artykule.


## Wyniki

Google wykorzystał PaLM(@chowdhery2022palm) LLM w eksperymentach z ReAct.
Porównania do standardowego podpowiadania (tylko pytanie), CoT i innych konfiguracji
pokazują, że wydajność ReAct jest obiecująca dla złożonych zadań rozumowania. Google
prowadzi również badania na zbiorze danych FEVER(@thorne2018fever), który obejmuje
ekstrakcję i weryfikację faktów.

import react_performance from '@site/docs/assets/react_performance.png';

<div style={{textAlign: 'center'}}>.
  <img src={react_performance} style={{szerokość: "500px"}} />
</div>

<div style={{textAlign: 'center'}}>
Wyniki badania ReAct (Yao i in.)
</div>



