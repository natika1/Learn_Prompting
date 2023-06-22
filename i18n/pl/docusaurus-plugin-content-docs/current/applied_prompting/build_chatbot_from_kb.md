---
sidebar_position: 40
---

# 🟢 Chatbot + Baza wiedzy.

import ImageIntents from '@site/docs/assets/chatbot_from_kb_intents.png'
import ImageGPT3 from '@site/docs/assets/chatbot_from_kb_gpt3.png'
import ImageGPT3Organized from '@site/docs/assets/chatbot_from_kb_gpt3_organized.png'
import ImagePrompt from '@site/docs/assets/chatbot_from_kb_prompt.png'
import ImageLogin from '@site/docs/assets/chatbot_from_kb_login.png'

Ostatnie postępy w dużych modelach językowych (LLM), takich jak [GPT-3](https://arxiv.org/abs/2005.14165) i [ChatGPT](https://chat.openai.com/chat), stworzyły wiele szumu w branży technologicznej. Modele te są niezwykle potężne dla generowania treści, ale mają też pewne minusy, takie jak stronniczość(@nadeem-etal-2021-stereoset) i halucynacje(@Ji_2022). Jednym z obszarów, w którym te LLM mogą być szczególnie przydatne, jest rozwój chatbota.

# Intent-Based Chatbots

Tradycyjne chatboty są zazwyczaj oparte na intencjach, co oznacza, że są zaprojektowane tak, aby odpowiadać na konkretne intencje użytkownika. Każda intencja składa się z zestawu przykładowych pytań i powiązanej z nimi odpowiedzi. Na przykład, intencja "Pogoda" może zawierać przykładowe pytania takie jak "Jaka jest dziś pogoda?" lub "Czy będzie dziś padać?" oraz odpowiedź typu "Dziś będzie słonecznie". Kiedy użytkownik zadaje pytanie, chatbot dopasowuje je do intencji z najbardziej podobnymi przykładowymi pytaniami i zwraca powiązaną odpowiedź.

<div style={{textAlign: 'left'}}>.
  <img src={ImageIntents} style={{szerokość: "700px"}} />
  <p style={{color: "gray", fontSize: "12px", fontStyle: "italic"}}>Jak działa tradycyjny chatbot oparty na intencjach. Obrazek autorstwa autora.</p>
</div>

Jednak chatboty oparte na intencjach mają swój własny zestaw problemów. Jednym z nich jest to, że wymagają dużej liczby konkretnych intencji, aby udzielić konkretnych odpowiedzi. Na przykład, wypowiedzi użytkownika takie jak "Nie mogę się zalogować", "Zapomniałem hasła" lub "Błąd logowania" mogą wymagać trzech różnych odpowiedzi, a zatem trzech różnych intencji, nawet jeśli wszystkie są dość podobne.

# How GPT-3 Can Help

To właśnie tutaj GPT-3 może być szczególnie użyteczne. Zamiast mieć wiele bardzo konkretnych intencji, każda z nich może być szersza i wykorzystywać dokument z Twojej [Bazy Wiedzy](https://en.wikipedia.org/wiki/Knowledge_base). Baza wiedzy (KB) to informacje przechowywane jako ustrukturyzowane i nieustrukturyzowane dane, gotowe do użycia w celu analizy lub wnioskowania. Twoja baza wiedzy może składać się z serii dokumentów wyjaśniających, jak używać Twoich produktów.

W ten sposób każda intencja jest związana z dokumentem zamiast listy pytań i konkretnej odpowiedzi, np. jedna intencja dla "problemów z logowaniem", jedna intencja dla "jak się zapisać" itp. Kiedy użytkownik zadaje pytanie o logowanie, możemy przekazać dokument "problemy z logowaniem" do GPT-3 jako informację kontekstową i wygenerować konkretną odpowiedź na pytanie użytkownika.


<div style={{textAlign: 'left'}}>.
  <img src={ImageGPT3} style={{szerokość: "700px"}} />
  <p style={{color: "gray", fontSize: "12px", fontStyle: "italic"}}>Jak mógłby działać chatbot wykorzystujący GPT-3. Obrazek autorstwa autora.</p>
</div>

Takie podejście zmniejsza liczbę intencji, którymi trzeba zarządzać i pozwala na udzielanie odpowiedzi lepiej dostosowanych do każdego pytania. Dodatkowo, jeśli dokument powiązany z intencją opisuje różne procesy (np. proces dla "logowania na stronie internetowej" i inny dla "logowania w aplikacji mobilnej"), GPT-3 może automatycznie poprosić użytkownika o wyjaśnienie przed udzieleniem ostatecznej odpowiedzi.

## Why Can't We Pass the Whole KB to GPT-3?

Obecnie, LLMy takie jak GPT-3 mają maksymalny rozmiar podpowiedzi około 4k tokenów (dla modelu [`text-davinci-003`](https://beta.openai.com/docs/models/gpt-3)), co jest dużo, ale nie wystarczająco dużo, by wprowadzić całą bazę wiedzy do pojedynczej podpowiedzi. Modele LLM mają maksymalny rozmiar podpowiedzi z powodów obliczeniowych, ponieważ generowanie tekstu za ich pomocą wymaga pewnej liczby obliczeń, która szybko rośnie wraz ze wzrostem rozmiaru podpowiedzi.

Przyszłe LLMy mogą nie mieć tego ograniczenia, zachowując jednocześnie możliwości generowania tekstu. Na razie jednak musimy zaprojektować rozwiązanie wokół tego problemu.

# How a Chatbot With GPT-3 Could Work

Zatem potok chatbota mógłby składać się z dwóch kroków:

1. Najpierw musimy wybrać odpowiednią intencję dla pytania użytkownika, czyli musimy pobrać odpowiedni dokument z naszej bazy wiedzy.
2. Następnie, gdy mamy już właściwy dokument, możemy wykorzystać GPT-3 do wygenerowania odpowiedniej odpowiedzi dla użytkownika. W tym celu będziemy musieli przygotować dobrą podpowiedź.

Pierwszy krok jest zasadniczo rozwiązany przez [wyszukiwanie semantyczne](https://en.wikipedia.org/wiki/Semantic_search). Możemy użyć wstępnie wytrenowanych modeli z biblioteki [`sentence-transformers`](https://www.sbert.net/examples/applications/semantic-search/README.html) i łatwo przypisać każdemu dokumentowi wynik. Dokument z najwyższym wynikiem jest tym, który zostanie użyty do wygenerowania odpowiedzi chatbota.

<div style={{textAlign: 'left'}}>.
  <img src={ImageGPT3Organized} style={{width: "700px"}} />
  <p style={{color: "gray", fontSize: "12px", fontStyle: "italic"}}>Jak mógłby działać chatbot wykorzystujący GPT-3. GPT-3 mógłby zostać użyty do wygenerowania odpowiedniej odpowiedzi wykorzystując informacje z dokumentów bazy wiedzy. Obrazek autorstwa autora.</p>
</div>

# Generowanie odpowiedzi za pomocą GPT-3

Kiedy mamy już odpowiedni dokument, będziemy musieli stworzyć dobrą podpowiedź, która zostanie użyta z GPT-3 do wygenerowania odpowiedzi. W poniższych eksperymentach będziemy zawsze używać modelu `text-davinci-003` z temperaturą `0,7`.

Aby spreparować podpowiedź, będziemy eksperymentować używając:

- [**Role-prompting**](https://learnprompting.org/docs/basics/roles): technika heurystyczna, która przypisuje SI określoną rolę.
- **Relevant KB information**, czyli dokument pobrany w kroku wyszukiwania semantycznego.
- **Ostatnie wiadomości wymieniane między użytkownikiem a chatbotem**. Są one przydatne w przypadku wiadomości wysyłanych przez użytkownika, w których nie jest określony cały kontekst. Później zobaczymy ich przykład. Zajrzyj do [tego przykładu](https://learnprompting.org/docs/applied_prompting/build_chatgpt), aby zobaczyć, jak zarządzać konwersacjami za pomocą GPT-3.
- Na koniec **pytanie użytkownika**.

<div style={{textAlign: 'left'}}>.
  <img src={ImagePrompt} style={{szerokość: "700px"}} />
  <p style={{color: "gray", fontSize: "12px", fontStyle: "italic"}}>Informacje użyte do spreparowania naszej podpowiedzi GPT-3. Obrazek autorstwa autora.</p>
</div>

Rozpocznijmy naszą podpowiedź z wykorzystaniem techniki <span className="yellow-highlight">role-prompting</span>.

<pre>
    <span className="yellow-highlight">Jako zaawansowany chatbot o imieniu Skippy, Twoim głównym celem jest pomaganie użytkownikom najlepiej jak potrafisz.</span><br/>
</pre>

Następnie załóżmy, że krok wyszukiwania semantycznego wydobywa następujący dokument z naszej bazy wiedzy. Wszystkie dokumenty opisują, jak działa produkt VideoGram, który jest wyimaginowanym produktem podobnym do Instagrama, ale tylko dla filmów.

<div style={{textAlign: 'left'}}>.
  <img src={ImageLogin} style={{szerokość: "700px"}} />
  <p style={{color: "gray", fontSize: "12px", fontStyle: "italic"}}>Dokument wyjaśniający jak działa logowanie do VideoGram. Obrazek autorstwa autora.</p>
</div>

Możemy dodać <span className="yellow-highlight">jego treść</span> wewnątrz podpowiedzi w ten sposób.

<pre>.
    Jako zaawansowany chatbot o imieniu Skippy, Twoim głównym celem jest pomaganie użytkownikom najlepiej jak potrafisz.<br/><br/>

    <span className="yellow-highlight">.
    START KONTEKSTU<br/>
    Zaloguj się do VideoGram z poziomu strony internetowej<br/>.
    1. Otwórz przeglądarkę internetową i przejdź na stronę internetową VideoGram.<br/>
    2. Kliknij przycisk "Zaloguj się" znajdujący się w prawym górnym rogu strony.<br/>
    3. Na stronie logowania wprowadź swoją nazwę użytkownika i hasło VideoGram.<br/>
    4. Po wprowadzeniu danych uwierzytelniających, kliknij przycisk "Zaloguj się".<br/>
    5. Powinieneś być teraz zalogowany na swoje konto VideoGram.<br/>
    <br/>
    Logowanie do VideoGram z aplikacji mobilnej<br/>
    1. Otwórz aplikację VideoGram na swoim urządzeniu mobilnym.<br/>
    2. Na stronie głównej dotknij przycisku "Login" znajdującego się w prawym dolnym rogu. 3. Na stronie logowania wprowadź swoją nazwę użytkownika i hasło VideoGram.<br/>
    4. Po wprowadzeniu danych uwierzytelniających, dotknij przycisku "Zaloguj".<br/>
    5. Powinieneś być teraz zalogowany do swojego konta VideoGram.<br/>
    KONIEC KONTEKSTU<br/>
    </span>
</pre>

Na koniec musimy dodać <span className="yellow-highlight">rozmowę i pytanie użytkownika</span> do końca podpowiedzi, jak w poniższym przykładzie.

<pre>.
    Jako zaawansowany chatbot o imieniu Skippy, Twoim głównym celem jest pomaganie użytkownikom najlepiej jak potrafisz.<br/>
    <br/>
    KONTEKST STARTOWY<br/>
    Zaloguj się do VideoGram z poziomu strony internetowej<br/>.
    1. Otwórz przeglądarkę internetową i przejdź na stronę internetową VideoGram.<br/>
    2. Kliknij przycisk "Zaloguj się" znajdujący się w prawym górnym rogu strony.<br/>
    3. Na stronie logowania wprowadź swoją nazwę użytkownika i hasło VideoGram.<br/>
    4. Po wprowadzeniu danych uwierzytelniających, kliknij przycisk "Zaloguj się".<br/>
    5. Powinieneś być teraz zalogowany na swoje konto VideoGram.<br/>
    <br/>
    Logowanie do VideoGram z aplikacji mobilnej<br/>
    1. Otwórz aplikację VideoGram na swoim urządzeniu mobilnym.<br/>
    2. Na stronie głównej dotknij przycisku "Login" znajdującego się w prawym dolnym rogu. 3. Na stronie logowania wprowadź swoją nazwę użytkownika i hasło VideoGram.<br/>
    4. Po wprowadzeniu danych uwierzytelniających, dotknij przycisku "Zaloguj".<br/>
    5. Powinieneś być teraz zalogowany do swojego konta VideoGram.<br/>
    KONIEC KONTEKSTU<br/>
    <br/>
    <span className="yellow-highlight">SKIPPY: Witaj, jestem Skippy! Jak mogę Ci pomóc?<br/>
    UŻYTKOWNIK: Nie mogę znaleźć przycisku logowania.<br/>
    SKIPPY:</span><br/>
</pre>

Przekazując ten monit do GPT-3, otrzymałem następującą wygenerowaną odpowiedź.

<pre>.
    <span className="bluegreen-highlight">Nie ma problemu! Na stronie internetowej przycisk logowania znajduje się w prawym górnym rogu strony. W aplikacji mobilnej przycisk logowania znajduje się w prawym dolnym rogu. Daj mi znać, jeśli potrzebujesz dalszej pomocy!</span>
</pre>

Zauważ, jak informacje w wygenerowanej odpowiedzi pochodzą z dokumentu bazy wiedzy.

# Disambiguating Questions with GPT-3

Spróbujmy z bardziej niejasną wypowiedzią użytkownika, jak <span className="yellow-highlight">"can't login"</span>. Oto kompletny monit.

<pre>.
    Jako zaawansowany chatbot o imieniu Skippy, Twoim głównym celem jest pomaganie użytkownikom najlepiej jak potrafisz.<br/>
    <br/>
    KONTEKST STARTOWY<br/>
    Zaloguj się do VideoGram z poziomu strony internetowej<br/>.
    1. Otwórz przeglądarkę internetową i przejdź na stronę internetową VideoGram.<br/>
    2. Kliknij przycisk "Zaloguj się" znajdujący się w prawym górnym rogu strony.<br/>
    3. Na stronie logowania wprowadź swoją nazwę użytkownika i hasło VideoGram.<br/>
    4. Po wprowadzeniu danych uwierzytelniających, kliknij przycisk "Zaloguj się".<br/>
    5. Powinieneś być teraz zalogowany na swoje konto VideoGram.<br/>
    <br/>
    Logowanie do VideoGram z aplikacji mobilnej<br/>
    1. Otwórz aplikację VideoGram na swoim urządzeniu mobilnym.<br/>
    2. Na stronie głównej dotknij przycisku "Login" znajdującego się w prawym dolnym rogu. 3. Na stronie logowania wprowadź swoją nazwę użytkownika i hasło VideoGram.<br/>
    4. Po wprowadzeniu danych uwierzytelniających, dotknij przycisku "Zaloguj".<br/>
    5. Powinieneś być teraz zalogowany do swojego konta VideoGram.<br/>
    KONIEC KONTEKSTU<br/>
    <br/>
    SKIPPY: Cześć, jestem Skippy! Jak mogę Ci pomóc?<br/>
    UŻYTKOWNIK: <span className="yellow-highlight">Nie mogę się zalogować</span><br/>
    SKIPPY:<br/>
</pre>

GPT-3 odpowiada próbując lepiej zrozumieć, co jest problemem użytkownika.

<pre>
    <span className="bluegreen-highlight">Przykro mi to słyszeć. Czy możesz mi powiedzieć, czy próbujesz się zalogować za pośrednictwem strony internetowej VideoGram lub aplikacji mobilnej? </span>
</pre>

Następnie, oto jak przebiega kompletna rozmowa. Cała zachęta jest ukryta dla lepszej widoczności.

<pre>.
    USER: Nie mogę się zalogować<br/>
    SKIPPY: Przykro mi to słyszeć. Czy możesz mi powiedzieć, czy próbujesz się zalogować przez stronę internetową VideoGram czy aplikację mobilną?<br/>
    USER: Aplikacja mobilna<br/>
    <span className="bluegreen-highlight">SKIPPY: OK, nie ma problemu. Aby zalogować się za pomocą aplikacji mobilnej, otwórz aplikację VideoGram na swoim urządzeniu mobilnym. Na stronie głównej dotknij przycisku "Zaloguj się" znajdującego się w prawym dolnym rogu. Na stronie logowania wprowadź swoją nazwę użytkownika i hasło VideoGram. Po wprowadzeniu danych uwierzytelniających, dotknij przycisku "Zaloguj się". Powinieneś być teraz zalogowany do swojego konta VideoGram. Proszę dać mi znać, jeśli potrzebujesz dalszej pomocy.</span><br/>
</pre>

GPT-3 może zarządzać dezambiguacją, pod warunkiem, że ma odpowiednie informacje kontekstowe.

# Problemy z generowaniem odpowiedzi za pomocą GPT-3

Poprzednie przykłady działały dobrze. Istnieje jednak kilka sposobów, w których taki chatbot mógłby zawieść.

Jeśli zapytamy "Czy aplikacja mobilna jest darmowa?" do GPT-3 przekazując dokument logowania jako kontekst, często otrzymamy odpowiedź typu "Tak, aplikacja mobilna VideoGram jest darmowa do pobrania i użytkowania", nawet jeśli taka informacja nie jest zawarta w informacji kontekstowej. Generowanie fałszywych informacji jest bardzo złe dla chatbotów obsługi klienta!

GPT-3 rzadko generuje fałszywe informacje, gdy odpowiedź na pytanie użytkownika można znaleźć w kontekście. Ponieważ pytania użytkowników są często krótkimi i niejednoznacznymi tekstami, nie możemy polegać na kroku wyszukiwania semantycznego, aby zawsze pobrać poprawny dokument, a więc zawsze jesteśmy narażeni na generowanie fałszywych informacji.

## Wniosek

GPT-3 jest bardzo przydatny do tworzenia konwersacyjnych chatbotów i jest w stanie odpowiedzieć na serię konkretnych pytań na podstawie informacji kontekstowych umieszczonych w podpowiedzi. Trudno jednak sprawić, by model produkował odpowiedzi wykorzystując tylko informacje z kontekstu, ponieważ ma on tendencję do halucynacji (czyli generowania nowych informacji, potencjalnie fałszywych). Generowanie fałszywych informacji jest problemem o różnym nasileniu w zależności od przypadku użycia.

Written by [Fabio Chiusano](https://www.linkedin.com/in/fabio-chiusano-b6a3b311b/).


