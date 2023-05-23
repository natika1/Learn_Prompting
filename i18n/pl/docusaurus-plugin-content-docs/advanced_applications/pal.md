---
sidebar_position: 4
---

# 🟡 Kod jako rozumowanie

[Program-aided Language Models (PAL)](https://reasonwithpal.com)(@gao2022pal) są kolejnym przykładem systemu MRKL.
Po otrzymaniu pytania, PAL-y są w stanie **zapisać kod**, który rozwiązuje to pytanie. Wysyłają
kod do programowego runtime'u, aby uzyskać wynik. PAL działa w przeciwieństwie do CoT; pośrednim
rozumowania jest kod, podczas gdy CoT jest językiem naturalnym.

import image from '@site/docs/assets/pal.png';

<div style={{textAlign: 'center'}}>.
  <img src={image} style={{width: "500px"}} />
</div>

<div style={{textAlign: 'center'}}>
Przykład PAL (Gao i in.)
</div>


Ważną rzeczą do zauważenia jest to, że PAL faktycznie łączy język naturalny (NL) i kod.
Na powyższym obrazku, na niebiesko są rozumowania w języku naturalnym, które generuje PAL. Chociaż
nie jest pokazane na obrazku, PAL faktycznie generuje "\" przed każdą linią rozumowania NL, tak aby
aby były one interpretowane jako komentarze przez programowy runtime.

## Przykład.

Przyjrzyjmy się przykładowi rozwiązywania przez PAL pytania matematycznego. Używam podpowiedzi 3-strzałowej,
która jest uproszczoną wersją [tej](https://github.com/reasoning-machines/pal/blob/main/pal/prompt/math_prompts.py)(@gao2022pal).

Użyję do tego langchain, pakietu Pythona służącego do łańcuchowania funkcjonalności LLM. Najpierw należy wykonać kilka instalacji:

``python
!pip install langchain==0.0.26
!pip install openai
from langchain.llms import OpenAI
importować os
os.environ["OPENAI_API_KEY"] = "sk-YOUR_KEY_HERE"
```

Następnie możemy stworzyć instancję GPT-3 davinci-002 (wywołanie API dzieje się, gdy używamy tego obiektu)
```
llm = OpenAI(model_name='text-davinci-002', temperature=0)
```

Oto kilkustrzałowa podpowiedź:

``python
MATH_PROMPT = '''
P: W serwerowni znajdowało się dziewięć komputerów. Każdego dnia, od poniedziałku do czwartku, instalowano pięć kolejnych komputerów. Ile komputerów znajduje się teraz w serwerowni?

# rozwiązanie w języku Python:
"""W serwerowni znajdowało się dziewięć komputerów. Każdego dnia, od poniedziałku do czwartku, instalowano pięć kolejnych komputerów. Ile komputerów znajduje się teraz w serwerowni?""
computers_initial = 9
computers_per_day = 5
num_days = 4 # 4 dni między poniedziałkiem a czwartkiem
computers_added = computers_per_day * num_days
computers_total = computers_initial + computers_added
result = computers_total
return result


P: Shawn ma pięć zabawek. Na święta dostał od mamy i taty po dwie zabawki. Ile zabawek ma teraz?

# rozwiązanie w Pythonie:
"""Shawn ma pięć zabawek. Na święta dostał po dwie zabawki od mamy i taty. Ile zabawek ma teraz?""
toys_initial = 5
mama_zabawki = 2
dad_toys = 2
total_received = mama_toys + tata_toys
total_toys = toys_initial + total_received
wynik = total_toys


P: Jason miał 20 lizaków. Dał Denny'emu kilka lizaków. Teraz Jason ma 12 lizaków. Ile lizaków Jason dał Denny'emu?

# rozwiązanie w Pythonie:
"""Jason miał 20 lizaków. Dał Denny'emu kilka lizaków. Teraz Jason ma 12 lizaków. Ile lizaków Jason dał Denny'emu?""
jason_lollipops_initial = 20
jason_lollipops_after = 12
denny_lollipops = jason_lollipops_initial - jason_lollipops_after
wynik = denny_lollipops

P: {question}

# rozwiązanie w języku Python:
'''
```

Teraz możemy przekazać połączony prompt do GPT-3.

```
llm_out = llm(MATH_PROMPT.format(pytanie=question))
print(llm_out)
```

Dane wyjściowe to:

<pre>.
<span className="bluegreen-highlight">.
"""Emma wzięła 60 minutowy lot samolotem do Seattle. Następnie wzięła 2 godziny jazdy pociągiem do portland, a potem 30 minut jazdy autobusem do vancouver. Ile czasu zajęło jej dotarcie do vancouver?"""<br/>.

plane_ride = 60<br/>
train_ride = 2 * 60 # 2 godziny w minutach<br/>
bus_ride = 30<br/>
total_time = plane_ride + train_ride + bus_ride<br/>
wynik = total_time
</span>
</pre>

Wreszcie możemy przekazać ten kod do runtime Pythona, aby uzyskać odpowiedź:

``python
exec(llm_out)
print(result)
```

Wyjściem jest **210**, co jest prawidłowe.

Zobacz notatnik Jupyter dla tego przykładu [tutaj](https://github.com/trigaten/Learn_Prompting/tree/main/docs/code_examples/PAL.ipynb).

## Więcej

Zobacz także [przykład kolabu PAL](https://colab.research.google.com/drive/1u4_RsdI0E79PCMDdcPiJUzYhdnjoXeXc?usp=sharing#scrollTo=Ba0ycacK4i1V).

