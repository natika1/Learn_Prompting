---
sidebar_position: 2
---

# 🟡 LLMs Using Tools

Systemy MRKL(@karpas2022mrkl) (Modular Reasoning, Knowledge and Language, wymawiane jako "cud")
są **neuro-symboliczną architekturą**, która łączy LLM (obliczenia neuronowe) i zewnętrzne
narzędzia takie jak kalkulatory (obliczenia symboliczne), aby rozwiązywać złożone problemy.

System MRKL składa się z zestawu modułów (np. kalkulatora, API pogodowego, bazy danych itp.) oraz routera, który decyduje o sposobie "kierowania" przychodzących zapytań w języku naturalnym do odpowiedniego modułu.

Prostym przykładem systemu MRKL jest LLM, który może
używać aplikacji kalkulatora. Jest to system jednomodułowy, w którym LLM jest routerem.
Na pytanie: "Ile to jest 100*100?
wyodrębnić liczby z podpowiedzi, a następnie powiedzieć systemowi MRKL, aby użył aplikacji
aby obliczyć wynik. Może to wyglądać następująco:

<pre>.
<p>Co to jest 100*100?</p>.

<span className="bluegreen-highlight">KALKULATOR[100*100]</span>.
</pre>.

System MRKL zobaczyłby słowo `CALCULATOR` i podłączyłby `100*100` do aplikacji kalkulatora.
Ten prosty pomysł można łatwo rozszerzyć na różne symboliczne narzędzia obliczeniowe.

Rozważ następujące dodatkowe przykłady zastosowań:

- Chatbot, który jest w stanie odpowiedzieć na pytania dotyczące finansowej bazy danych poprzez
wyodrębnianie informacji w celu utworzenia zapytania SQL z tekstu użytkownika.

<pre>
<p>Jaka jest obecnie cena akcji Apple? </p>.

<span className="bluegreen-highlight">Obecna cena to DATABASE[SELECT price FROM stock WHERE company = "Apple" AND time = "now"].</span>
</pre>.

- Chatbot, który jest w stanie odpowiedzieć na pytania dotyczące pogody poprzez wyodrębnienie
informacji z podpowiedzi i używając API pogodowego do pobierania informacji.

<pre>
<p>Jaka jest pogoda w Nowym Jorku? </p>.

<span className="bluegreen-highlight">Pogoda to WEATHER_API[Nowy Jork].</span>.
</pre>.

- Lub nawet znacznie bardziej złożone zadania, które zależą od wielu źródeł danych, np.
następujące:


import mrkl_task from '@site/docs/assets/mrkl_task.png';
import dataset from '@site/docs/assets/mrkl/dataset.png';
import load_dataset from '@site/docs/assets/mrkl/load_dataset.png';
import model from '@site/docs/assets/mrkl/model.png';
import extract from '@site/docs/assets/mrkl/extract.png';
import search from '@site/docs/assets/mrkl/search.png';
import final from '@site/docs/assets/mrkl/final.png';

<div style={{textAlign: 'center'}}>.
  <img src={mrkl_task} style={{szerokość: "500px"}} />
</div>

<div style={{textAlign: 'center'}}>
Przykładowy system MRKL (AI21)
</div>


## An Example

Odtworzyłem przykładowy system MRKL z oryginalnego papieru, używając Dust.tt,
linkowanego [tutaj](https://dust.tt/trigaten/a/98bdd65cb7).
System czyta problem matematyczny (np. `Co to jest 20 razy 5^6?`), wyciąga liczby i operacje,
i formatuje je dla aplikacji kalkulatora (np. `20*5^6`). Następnie wysyła przeformatowane równanie
do aplikacji kalkulatora Google i zwraca wynik. Zauważ, że oryginalny papier wykonuje szybkie dostrajanie na routerze (LLM), ale nie robię tego w tym przykładzie. Przejdźmy przez to, jak to działa:

Najpierw zrobiłem prosty zbiór danych w zakładce Dust `Datasets`.


<div style={{textAlign: 'center'}}>.
  <img src={dataset} style={{szerokość: "750px"}} />
</div>

Następnie przeszedłem do zakładki `Specification` i załadowałem zbiór danych za pomocą bloku `data`.

<div style={{textAlign: 'center'}}>.
  <img src={load_dataset} style={{width: "750px"}} />
</div>

Następnie stworzyłem blok `llm`, który wyodrębnia liczby i operacje. Zauważ, jak
w zachęcie powiedziałem mu, że będziemy używać kalkulatora Google. Model, którego używam (GPT-3)
prawdopodobnie posiada pewną wiedzę na temat kalkulatora Google z treningu wstępnego.

<div style={{textAlign: 'center'}}>.
  <img src={model} style={{szerokość: "750px"}} />
</div>

Następnie zrobiłem blok `code`, który uruchamia jakiś prosty kod javascript, aby usunąć
spacje z uzupełnienia.

<div style={{textAlign: 'center'}}>.
  <img src={extract} style={{width: "750px"}} />
</div>

Na koniec zrobiłem blok `search`, który wysyła przeformatowane równanie do kalkulatora Google.

<div style={{textAlign: 'center'}}>.
  <img src={search} style={{width: "750px"}} />
</div>

Poniżej możemy zobaczyć ostateczne wyniki, które są wszystkie poprawne!

<div style={{textAlign: 'center'}}>.
  <img src={final} style={{width: "750px"}} />
</div>

Zapraszamy do klonowania i eksperymentowania z tym placem zabaw [tutaj](https://dust.tt/trigaten/a/98bdd65cb7).

## Uwagi
MRKL został opracowany przez [AI21](https://www.ai21.com/) i pierwotnie używał ich
J-1 (Jurassic 1)(@lieberjurassic) LLM.

## Więcej

Zobacz [ten przykład](https://langchain.readthedocs.io/en/latest/modules/agents/implementations/mrkl.html) systemu MRKL
zbudowanego z LangChain.


