---
sidebar_position: 4
---

# 🟢 Zbuduj ChatGPT z GPT-3

import Skippy from '@site/docs/assets/skippy_chatbot.png'
import SkippyHeader from '@site/docs/assets/skippy_chatbot_header.png'
import Therapy from '@site/docs/assets/therapy_chatbot.gif'
import ChatGPT from '@site/docs/assets/chatgpt_ui_diagram.png'

<div style={{textAlign: 'left'}}>.
  <img src={SkippyHeader} style={{szerokość: "700px"}} />
</div>

## Wprowadzenie

[ChatGPT](https://chat.openai.com/chat) wybuchł w ostatnim miesiącu, zyskując milion użytkowników w ciągu zaledwie tygodnia. Co zaskakujące, model bazowy, GPT-3 zadebiutował w 2020 roku i został udostępniony publicznie <a href="https://openai.com/blog/api-no-waitlist/">ponad rok temu!</a>.

Dla tych, którzy nie wiedzą, ChatGPT to nowy model językowy od OpenAI, który został dostrojony z GPT-3, aby być zoptymalizowanym do konwersacji (@chatgpt2022). Ma przyjazny dla użytkownika interfejs czatu, w którym możesz podać dane wejściowe i uzyskać odpowiedź od asystenta AI. Sprawdź to na [chat.openai.com](https://chat.openai.com/chat).

Podczas gdy wczesne wersje GPT-3 nie były tak zaawansowane jak obecna seria GPT-3.5, wciąż robiły wrażenie. Modele te były dostępne poprzez API i interfejs <a href="https://beta.openai.com/playground">playground web UI</a>, który pozwala na dostrojenie pewnych hiperparametrów konfiguracyjnych i podpowiedzi testowych. GPT-3 zyskał znaczną trakcję, ale nie zbliżył się do wiralności ChatGPT.

To, co sprawia, że ChatGPT jest tak udany, w porównaniu do GPT-3, to jego dostępność jako prostego asystenta AI dla przeciętnej osoby, niezależnie od jej wiedzy na temat nauki o danych, modeli językowych czy AI.  

W tym artykule omawiam jak chatboty takie jak ChatGPT mogą być zaimplementowane przy użyciu dużego modelu językowego jak GPT-3.

## Motywacja
Ten artykuł został napisany częściowo z powodu tweeta autorstwa <a href="https://twitter.com/goodside">Riley Goodside</a>, zwracającego uwagę na to, jak ChatGPT mógłby zostać wdrożony.

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Jak zrobić własny knock-off ChatGPT przy użyciu GPT-3 (text-davinci-003) - gdzie można dostosować zasady do swoich potrzeb, a dostęp do wynikowego chatbota przez API. <a href="https://t.co/9jHrs91VHW">pic.twitter.com/9jHrs91VHW</a></p>&mdash; Riley Goodside (@goodside) <a href="https://twitter.com/goodside/status/1607487283782995968?ref_src=twsrc%5Etfw">26 grudnia 2022</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

Podobnie jak inne modele z serii GPT-3.5, ChatGPT został wytrenowany przy użyciu [RLHF](https://huggingface.co/blog/rlhf), ale duża część jego skuteczności wynika z użycia **dobrej podpowiedzi**.

# The Prompt

<div style={{textAlign: 'left'}}>.
  <img src={Skippy} style={{width: "700px"}} />
  <p style={{color: "gray", fontSize: "12px", fontStyle: "italic"}}>Pełna podpowiedź chatbota Skippy z nagłówka artykułu</p>.
</div>

<a href="https://learnprompting.org/docs/basics/prompting">Prompting to proces instruowania SI, aby coś zrobiła. </a> Jak prawdopodobnie widziałeś w przykładach ChatGPT online, możesz zachęcić go do zrobienia czegokolwiek. Typowe przypadki użycia to podsumowanie tekstu, pisanie treści na podstawie opisu lub tworzenie takich rzeczy jak wiersze, przepisy i wiele innych.

<p></p>.

ChatGPT jest zarówno modelem językowym jak i interfejsem użytkownika. Komunikat wprowadzony przez użytkownika do interfejsu jest w rzeczywistości wstawiany do większego komunikatu, który zawiera całą rozmowę pomiędzy użytkownikiem a ChatGPT. Pozwala to modelowi językowemu zrozumieć kontekst rozmowy i odpowiednio na nią odpowiedzieć.

<div style={{textAlign: 'left'}}>.
  <img src={ChatGPT} style={{szerokość: "600px"}} />
  <p style={{color: "gray", fontSize: "12px", fontStyle: "italic"}}>Przykładowe wstawienie monitu użytkownika przed wysłaniem do modelu</p>.
</div>

Model językowy uzupełnia podpowiedź poprzez określenie, jakie słowa pojawią się w następnej kolejności na podstawie prawdopodobieństwa, którego nauczył się podczas treningu wstępnego (@jurafsky2009).

<p></p>

GPT-3 jest w stanie "uczyć się" na podstawie prostej instrukcji lub kilku przykładów w podpowiedzi. To ostatnie nazywane jest few-shot, lub in context learning (@brown2020language). W powyższym podpowiedzi chatbota, tworzę fikcyjnego chatbota o imieniu Skippy i instruuję go, aby udzielał odpowiedzi użytkownikom. GPT-3 odbiera format "back-and-forth", `USER: {user input}` i `SKIPPY: {skippy response}`. GPT-3 rozumie, że Skippy jest chatbotem, a poprzednie wymiany zdań są rozmową, więc kiedy podamy kolejne dane wejściowe użytkownika, "Skippy" odpowie.

### Zapamiętywanie

Wcześniejsze wymiany zdań pomiędzy Skippy'm a użytkownikiem są dołączane do następnej podpowiedzi. Za każdym razem, gdy podamy więcej danych od użytkownika i otrzymamy więcej danych od chatbota, podpowiedź rozszerza się o nową wymianę. W ten sposób chatboty takie jak Skippy i ChatGPT mogą **pamiętać poprzednie wejścia.** Istnieje jednak limit, jak wiele chatbot GPT-3 może zapamiętać.

Prompts mogą stać się masywne po kilku wymianach, zwłaszcza jeśli używamy chatbota do generowania długich odpowiedzi, takich jak posty na blogu. Prompts wysyłane do GPT-3 są zamieniane na tokeny, czyli pojedyncze słowa lub ich części. Istnieje limit <a href="https://help.openai.com/en/articles/4936856-what-are-tokens-and-how-to-count-them">4097 tokenów (około 3000 słów)</a> dla połączonej zachęty i wygenerowanej odpowiedzi dla modeli GPT-3, w tym ChatGPT.

### Parę przykładów

Istnieje wiele różnych przypadków użycia podpowiedzi chatbota, które przechowują poprzednie rozmowy. ChatGPT ma być uniwersalnym asystentem i z mojego doświadczenia wynika, że rzadko pyta o dalsze działania.

#### Terapeutyczny chatbot, który pyta o Twój dzień

Pomocne może być posiadanie chatbota, który aktywnie zadaje pytania i otrzymuje informacje zwrotne od użytkownika. Poniżej znajduje się przykładowy chatbot terapeutyczny, który będzie zadawał pytania i uzupełniał je, aby pomóc użytkownikowi w przemyśleniu jego dnia.

<div style={{textAlign: 'left'}}>.
  <img src={Terapia} style={{szerokość: "700px"}} />
  <p style={{color: "gray", fontSize: "12px", fontStyle: "italic"}}>Podpowiedź chatbota Terapii</p>.
</div>

#### Porozmawiaj z młodszym sobą, korzystając ze starych wpisów w dzienniku

<a href="https://twitter.com/michellehuang42">Michelle Huang</a> wykorzystała GPT-3 do przeprowadzenia rozmowy z młodszym sobą. Podpowiedź wykorzystuje pewien kontekst, w tym przypadku stare wpisy z dziennika, sparowane z formatem chatbota tam i z powrotem. GPT-3 jest w stanie naśladować osobowość na podstawie tych wpisów.

<p></p>

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">i trained an ai chatbot on my childhood journal entries - so that i could engage in real-time dialogue with my &quot;inner child&quot;<br/><br/>some reflections below:</p>&mdash; michelle huang (@michellehuang42) <a href="https://twitter.com/michellehuang42/status/1597005489413713921?ref_src=twsrc%5Etfw">27 listopada 2022</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>.

Prompt z Tweeta:
```markdown
Poniżej znajduje się rozmowa z Obecną Michelle (wiek [redakcja]) i Młodą Michelle (wiek 14 lat).

Młoda Michelle napisała następujące wpisy do dziennika:
[wpisy z dziennika tutaj]

Present Michelle: [tu wpisz swoje pytania]
```

Autor zauważa, że wpisy w dzienniku mogą osiągnąć limit tokenów. W takim przypadku można wybrać kilka wybranych wpisów lub spróbować podsumować kilka wpisów.

## Implementacja

Przejdę przez kodowanie prostego chatbota zasilanego GPT-3 w Pythonie. Włączenie GPT-3 do budowanej aplikacji jest niezwykle proste przy użyciu API OpenAI. Będziesz musiał stworzyć konto na OpenAI i uzyskać klucz API. Sprawdź ich dokumenty <a href="https://beta.openai.com/docs/introduction">tutaj.</a>.

Przegląd tego, co musimy zrobić:

1. Sformatuj dane wejściowe użytkownika w podpowiedzi chatbota dla GPT-3
2. Uzyskaj odpowiedź chatbota jako uzupełnienie z GPT-3
3. Zaktualizuj monit zarówno z danymi użytkownika jak i odpowiedzią chatbota
4. Pętla

Oto zachęta, której będę używał. Możemy użyć pythona do zastąpienia <historii rozmowy\> i <wejścia użytkownika\> z ich rzeczywistymi wartościami.

```python
chatbot_prompt = """
    Jako zaawansowany chatbot, Twoim głównym celem jest pomaganie użytkownikom w jak najlepszy sposób. Może to polegać na odpowiadaniu na pytania, dostarczaniu pomocnych informacji lub wykonywaniu zadań na podstawie danych wprowadzonych przez użytkownika. Aby skutecznie pomagać użytkownikom, ważne jest, aby Twoje odpowiedzi były szczegółowe i dokładne. Używaj przykładów i dowodów, aby wspierać swoje punkty i uzasadniać swoje zalecenia lub rozwiązania.

    <historia rozmowy>

    Użytkownik: <wejście użytkownika>
    Chatbot:"""
```

Śledzę zarówno następne dane wejściowe użytkownika, jak i poprzednią rozmowę. Nowe wejście/wyjście pomiędzy chatbotem a użytkownikiem jest dołączane w każdej pętli.
```python
import openai

openai.api_key = "YOUR API KEY HERE"
model_engine = "text-davinci-003"
chatbot_prompt = """
Jako zaawansowany chatbot, Twoim głównym celem jest pomaganie użytkownikom w jak najlepszy sposób. Może to polegać na odpowiadaniu na pytania, dostarczaniu pomocnych informacji lub wykonywaniu zadań na podstawie danych wprowadzonych przez użytkownika. Aby skutecznie pomagać użytkownikom, ważne jest, aby Twoje odpowiedzi były szczegółowe i dokładne. Używaj przykładów i dowodów, aby wspierać swoje punkty i uzasadniać swoje zalecenia lub rozwiązania.

<conversation history>

Użytkownik: <wejście użytkownika>
Chatbot:"""


def get_response(conversation_history, user_input):
    prompt = chatbot_prompt.replace(
        "<conversation_history>", conversation_history).replace("<user input>", user_input)

    # Uzyskaj odpowiedź z GPT-3
    response = openai.Completion.create(
        engine=model_engine, prompt=prompt, max_tokens=2048, n=1, stop=None, temperature=0.5)

    # Wyodrębnij odpowiedź z obiektu response
    response_text = response["choices"][0]["text"]

    chatbot_response = response_text.strip()

    return chatbot_response


def main():
    conversation_history = ""

    while True:
        user_input = input("> ")
        jeśli user_input == "exit":
            break
        chatbot_response = get_response(conversation_history, user_input)
        print(f "Chatbot: {chatbot_response}")
        conversation_history += f "Użytkownik: {user_input}Chatbot: {chatbot_response}"

main()
```


<a href="https://gist.github.com/jayo78/79d8834e6e31bf942c7b604e1611b68d">Tutaj link</a> do pełnego kodu prostego chatbota.

<p></p>

Teraz pozostaje tylko zbudować ładny front-end, z którym użytkownicy mogą wchodzić w interakcje!

Written by [jayo78](https://twitter.com/jayo782).

