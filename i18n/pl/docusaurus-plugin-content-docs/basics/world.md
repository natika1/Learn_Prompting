---
sidebar_position: 200
---
# 🟢 Zrozumieć umysły AI

Witaj czytelniku, gratuluję przebrnięcia przez rozdział intro. Jesteś na świetny początek w tej bardzo ekscytującej dziedzinie. Jest kilka prostych rzeczy, które powinieneś wiedzieć o różnych AI i jak działają, zanim zaczniesz czytać resztę kursu.

import music_image from '@site/docs/assets/music+image.png';

<div style={{textAlign: 'center'}}>.
  <img src={music_image} style={{width: "850px"}} />
</div>

<div style={{textAlign: 'center'}}>
  Dźwięk generowany na podstawie obrazu.
</div>

# Different AIs

Tysiące, jeśli nie miliony SI istnieją. Niektóre są lepsze od innych. Różne SI mogą tworzyć [obrazy](https://openai.com/product/dall-e-2), [muzykę](https://google-research.github.io/seanet/musiclm/examples/), [tekst](https://platform.openai.com/playground), a nawet [filmy](https://makeavideo.studio/). Zauważ, że to wszystko są *generatywne* SI, czyli takie, które *tworzą* rzeczy. Istnieją również *dyskryminacyjne* SI, czyli takie, które *klasyfikują* rzeczy. Na przykład, możesz użyć klasyfikatora obrazu, aby stwierdzić, czy obraz jest kotem czy psem. W tym kursie nie będziemy używać żadnych dyskryminacyjnych SI.


Tylko kilka generatywnych AI jest obecnie wystarczająco zaawansowanych, aby być szczególnie przydatnymi w inżynierii podpowiedzi. W tym kursie używamy głównie GPT-3 i ChatGPT. Jak wspomnieliśmy na ostatniej stronie, ChatGPT jest botem czatowym, podczas gdy GPT-3 nim nie jest. **Zazwyczaj będą one produkować różne odpowiedzi, gdy zostaną zadane to samo pytanie**. Jeśli jesteś deweloperem, polecam użyć GPT-3, ponieważ jest bardziej powtarzalny. Jeśli nie jesteś programistą, polecam użycie [ChatGPT](https://learnprompting.org/docs/category/%EF%B8%8F-image-prompting), ponieważ jest łatwiejszy w użyciu. Większość technik w tym kursie może być zastosowana do obu SI. Jednak niektóre z nich będą dotyczyły tylko GPT-3, więc zachęcamy do używania GPT-3, jeśli chcesz wykorzystać wszystkie techniki z tego kursu.

W części dotyczącej generowania obrazów użyjemy również [Stabilnej dyfuzji](https://beta.dreamstudio.ai/home) i [DALLE](https://openai.com/product/dall-e-2). Zobacz więcej odpowiednich AI [tutaj](https://learnprompting.org/docs/products#chatbots).

# How these AIs work

Ta sekcja opisuje aspekty popularnych generatywnych **tekstowych** SI. Te SI mają mózgi, które składają się z miliardów sztucznych neuronów. Sposób, w jaki te neurony są zbudowane, nazywa się architekturą transformatorową. Jest to dość złożony typ sieci neuronowej. To, co powinieneś zrozumieć, to:

1. Te SI to po prostu funkcje matematyczne. Zamiast $f(x) = x^2$, są bardziej jak f(tysiące zmiennych) = tysiące możliwych wyjść.
2. Te AI rozumieją zdania poprzez rozbicie ich na słowa/subsłowia zwane tokenami (np. AI może przeczytać `I don't like` jako `"I", "don", "'t" "like"`). Każdy token jest następnie konwertowany na listę liczb, aby SI mogła go przetworzyć.
3. Te AI przewidują następne słowo/token w zdaniu na podstawie poprzednich słów/tokenów (np. AI może przewidzieć `apples` po `I don't like`). Każdy napisany przez nie token opiera się na poprzednich tokenach, które widziały i napisały; za każdym razem, gdy piszą nowy token, robią pauzę, by zastanowić się, jaki powinien być następny token.
4. Te AI patrzą na każdy token w tym samym czasie. Nie czytają od lewej do prawej lub od prawej do lewej, jak robią to ludzie.

Proszę zrozumieć, że słowa "myśleć", "mózg" i "neuron" to zoomorfizmy, które są w zasadzie metaforami tego, co model faktycznie robi. Te modele tak naprawdę nie myślą, to tylko funkcje matematyczne. Nie są w rzeczywistości mózgami, są tylko sztucznymi sieciami neuronowymi. Nie są w rzeczywistości biologicznymi neuronami, są tylko liczbami.

Jest to obszar aktywnych badań i filozofii. Ten opis jest raczej cyniczny w stosunku do ich natury i ma na celu złagodzenie popularnego w mediach przedstawienia SI jako istot, które myślą/działają jak ludzie. To powiedziawszy, jeśli chcesz zantropomorfizować SI, proszę bardzo! Wydaje się, że większość ludzi to robi i może to być nawet pomocne w nauce.


## Notes

- [d2l.ai](https://www.d2l.ai) to dobre źródło wiedzy o tym, jak działa AI

- Proszę zauważyć, że autorzy w rzeczywistości lubią jabłka. Są przepyszne.


