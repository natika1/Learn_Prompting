---
sidebar_position: 7
---

# 🟢 What's in a Prompt?

Na poprzednich stronach omówiliśmy kilka różnych strategii podpowiadania.
Na tej stronie znajdziesz kilka ogólnych porad na temat tego, co jest ważne w podpowiedzi.


## "Ground Truth Matters Little"


Zaskakująco, gdy w podpowiedziach podajemy kilka strzałów %%exemplars|exemplars%%, rzeczywiste odpowiedzi (%%gold|gold_labels%%)
w exemplarzach nie mają znaczenia. Jak widać na poniższym rysunku, dostarczenie losowych
%%labels|labels%% w exemplarzach ledwie szkodzi wydajności(@min2022rethinking). "Demo" jest synonimem
z exemplar w tym obrazie.

import GoldUn from '@site/docs/assets/gold_unimportant.png';

<div style={{textAlign: 'center'}}>.
  <img src={GoldUn} style={{width: "750px"}} />
</div>

## Labelspace Matters

Nawet jeśli złote etykiety w egzemplifikacjach nie są ważne, to %%labelspace|labelspace%%.
jest.
Nawet dostarczenie losowych etykiet z przestrzeni etykiet pomaga LLM lepiej zrozumieć
przestrzeni etykiet i poprawia wyniki. Dodatkowo, prawidłowa reprezentacja
rozkład przestrzeni etykiet w przykładach jest ważny. Zamiast równomiernego
próbkowania z przestrzeni etykiet w przykładach, lepiej jest próbkować zgodnie z prawdziwym rozkładem etykiet.

## Format Matters

Być może najważniejszą częścią przykładów jest to, jak są one sformatowane. Ten
Format ten instruuje LLM, jak prawidłowo sformatować swoją odpowiedź na podpowiedź.

Na przykład, rozważ poniższe przykłady. Jako odpowiedzi użyto w nich wszystkich wielkich słów.
Nawet jeśli odpowiedzi są całkowicie błędne (2+2 to nie 50), GPT-3 poprawnie odpowiada na
na ostatnie pytanie i podąża za formatem pozostałych.

``tekst``
Co to jest 2+2?
PIĘĆDZIESIĄT
Ile to jest 20+5?
FORTY-THREE
Ile to jest 12+9?
// highlight-start
TWENTY-ONE
// highlight-end
```

## Notes

Od 4 do 8 przykładów jest dobrą liczbą do użycia dla kilku strzałów podpowiedzi(@min2022rethinking),
ale często pomocne może być umieszczenie jak największej ich liczby.

[^labelspace]: Zobacz [vocabulary reference](https://learnprompting.org/docs/vocabulary#labels), aby uzyskać więcej informacji.


