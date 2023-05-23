---
sidebar_position: 3
---

# 🟢 Rozwiąż pytania dyskusyjne

import Auto from '@site/docs/assets/short_content_auto.png';

Z właściwą podpowiedzią, GPT-3 jest bardzo zdolny do pisania krótkich odpowiedzi. Aby to zademonstrować, przyjrzę się **rozwiązywaniu pytań dyskusyjnych**, które jest częstym cotygodniowym zadaniem na wielu kursach uniwersyteckich. Odpowiedź na pytanie dyskusyjne to zazwyczaj około 100-700 słów. Dłuższe treści mogą być nieco bardziej skomplikowane, ponieważ LLM mają ograniczoną pamięć i mają trudności ze zrozumieniem globalnego obrazu tego, co piszą (@jin2022plot).

Przyjrzyjmy się przykładowi podstawowego pytania dyskusyjnego:

> _"Jakie są najbardziej palące problemy środowiskowe, przed którymi stoi dziś nasza planeta, i jakie kroki mogą podjąć poszczególne osoby, aby pomóc w rozwiązaniu tych problemów?"_.

Możemy zamienić to w prostą podpowiedź dla GPT-3, poprzedzając ją <span className="yellow-highlight">Respond to the following:</span>.

<pre>.
    <span className="yellow-highlight">Odpowiedz na następujące pytania:</span><br/>
    Jakie są najbardziej palące problemy środowiskowe, przed którymi stoi dziś nasza planeta, <br/>i jakie kroki mogą podjąć jednostki, aby pomóc w rozwiązaniu tych problemów?
</pre>

Wyniki generowane za pomocą tej zachęty nie są spójne, a kilka z nich to tylko zdanie lub dwa. Typowa odpowiedź w dyskusji powinna mieć wiele akapitów, więc te wyniki nie są idealne. Dobra zachęta powinna dawać **specyficzne instrukcje dotyczące formatu i treści**. Chcesz usunąć niejednoznaczność w języku, aby poprawić spójność i jakość. Oto lepsza zachęta.

<pre>
    <span className="yellow-highlight">Napisz bardzo szczegółowy esej ze wstępem, ciałem i akapitami podsumowującymi, odpowiadający na następujące pytania:</span><br/>
    Jakie są najbardziej palące problemy środowiskowe, przed którymi stoi dziś nasza planeta,
    <br/>i jakie kroki mogą podjąć jednostki, aby pomóc w rozwiązaniu tych problemów?
</pre>

<iframe src="https://player.vimeo.com/video/778327269?h=77d739ae72&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479" width="600" height="400" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen title="przykład"></iframe>.

Druga zachęta generuje średnio dłuższe odpowiedzi o lepszej strukturze. Użycie terminu "esej" w tej zachęcie było celowe, ponieważ GPT-3 potrafi zrozumieć definicję eseju, a zatem jest bardziej prawdopodobne, że wygeneruje spójne, ustrukturyzowane odpowiedzi.

### Wiele pytań dyskusyjnych nie jest skutecznych w podpowiadaniu.

> _"Wojna secesyjna konfliktem o ekspansję? Zgadzaj się z nami i dlaczego?"_.

Oto prawdziwe pytanie dyskusyjne z kursu historii w college'u. Nie jest ono sformułowane poprawnie i jest zbyt otwarte. **Aby uzyskać dobre odpowiedzi w dyskusji, musisz przeformułować pytanie w dobrze zdefiniowaną zachętę.** Dobrze zdefiniowana zachęta dla powyższego pytania dyskusyjnego mogłaby brzmieć:

> _"Wyjaśnij przyczyny wojny secesyjnej i czy ekspansja odegrała rolę w konflikcie. Dołącz dowody na poparcie swojej tezy."_.

Teraz możemy dodać formatowanie i wskazówki kontekstowe.

<pre>
    <span className="yellow-highlight">Napisz bardzo szczegółową odpowiedź na dyskusję, w strukturze eseju, odpowiadając na następujący monit:</span><br/>
    Wyjaśnij przyczyny wojny secesyjnej i czy ekspansja odegrała rolę w konflikcie. <br/>Włącz dowody na poparcie swojej argumentacji.
</pre>

### Zautomatyzuj dobrze zdefiniowane przepisywanie zachęt z GPT-3

Powyższy przykład przepisywania został wygenerowany za pomocą programu OpenAI [ChatGPT](https://openai.com/blog/chatgpt/).

<div style={{textAlign: 'left'}}>.
  <img src={Auto} style={{szerokość: "500px"}} />
</div>

### Iteracja

Po stworzeniu efektywnej zachęty do pytania dyskusyjnego, musisz teraz dopracować wyniki generowane przez GPT-3. Może to oznaczać dostosowanie wyników do ograniczeń, takich jak liczba słów, lub połączenie koncepcji z różnych wygenerowanych wyników.

Prostą metodą iteracji jest wygenerowanie wielu danych wyjściowych i przejrzenie ich w celu zrozumienia koncepcji, które wykorzystuje GPT-3 oraz struktury, której się trzyma. Po ocenie danych wyjściowych możesz wybrać najbardziej odpowiednie dane wyjściowe i połączyć je w spójną odpowiedź.

Innym sposobem iteracji jest rozpoczęcie, a następnie **rozszerzenie krok po kroku**. Wymaga to więcej niż jednej zachęty: Podpowiedź startowa, aby napisać początkowy akapit lub tak, a następnie inne podpowiedzi, aby rozwinąć to, co już zostało napisane.

Oto potencjalne pytanie do dyskusji filozoficznej:

> _"Czy matematyka jest wymyślona czy odkryta? Użyj starannego rozumowania, aby wyjaśnić swoją odpowiedź."_.

Dodaj go do prostej zachęty, takiej jak ta:

<pre>.
    <span className="yellow-highlight">Napisz początkowy akapit odpowiadający na następujące pytania:</span>.
    <br/>Czy matematyka jest wymyślona czy odkryta? Użyj starannego rozumowania, aby wyjaśnić swoją odpowiedź
</pre>

Wygenerowałem kilka odpowiedzi i znalazłem jedną, która mi się spodobała:

<pre>.
    <span className="bluegreen-highlight">Wśród filozofów i matematyków toczy się wiele debat na temat tego, czy
    <br/>matematyka jest wymyślona czy odkryta. Niektórzy twierdzą, że pojęcia i zasady matematyczne istnieją
    <br/>niezależnie od ludzkich umysłów i dlatego można je uznać za odkryte, a nie wynalezione.
    <br/>Na przykład, pojęcie liczb, proporcji i kształtów geometrycznych są obserwowane w naturalnym
    <br/>świecie i mogą być wyabstrahowane i badane w sposób systematyczny.</span>
</pre>.

To jest całkiem dobry początek. Potem dołączyłem do tego kolejną zachętę do rozwinięcia:

<pre>.
<span className="yellow-highlight">Piszę szczegółowy krótki esej odpowiadający na następującą podpowiedź:</span>.
<br/>Czy matematyka jest wymyślona czy odkryta? Użyj starannego rozumowania, aby wyjaśnić swoją odpowiedź. <span className="yellow-highlight"><p/>Here is what I have so far:</span>Wśród filozofów i matematyków toczy się wiele dyskusji na temat tego, czy
<br/>matematyka jest wymyślona czy odkryta. Niektórzy twierdzą, że pojęcia i zasady matematyczne istnieją niezależnie od
<br/>od ludzkich umysłów i dlatego można je uznać za odkryte, a nie wynalezione. Na przykład.
<br/>koncepcje liczb, proporcji i kształtów geometrycznych są obserwowane w świecie przyrody i mogą być wyabstrahowane
<br/>i badać w sposób systematyczny. <p/><span className="yellow-highlight">Napisz kolejny akapit mojego eseju.</span>.
</pre>.

Wypróbuj ten monit o rozszerzeniu za pomocą poniższego dema (będziesz potrzebował swojego klucza API OpenAI)

<div trydyno-embed="" openai-model="text-davinci-003" initial-prompt="Piszę szczegółowy krótki esej odpowiadający na następującą zachętę: \˝Czy matematyka jest wymyślona czy odkryta? Użyj starannego rozumowania, aby wyjaśnić swoją odpowiedź. \Oto, co mam do tej pory: Wśród filozofów i matematyków toczy się wiele dyskusji na temat tego, czy matematyka jest wymyślona czy odkryta. Niektórzy twierdzą, że pojęcia i zasady matematyczne istnieją niezależnie od ludzkich umysłów i dlatego można je uznać za odkryte, a nie wynalezione. Na przykład pojęcie liczb, proporcji i kształtów geometrycznych są obserwowane w świecie przyrody i mogą być wyabstrahowane i badane w sposób systematyczny. \Napisz następny akapit mojego eseju." initial-response="Z drugiej strony niektórzy twierdzą, że matematyka jest w dużej mierze wynalazkiem ludzkiego umysłu. Zasady matematyczne oparte są na logicznym rozumowaniu, które jest cechą ludzkiego umysłu. Na przykład geometria euklidesowa opiera się na abstrakcyjnych aksjomatach i postulatach, które są przyjmowane jako prawdziwe bez dowodu. W związku z tym można twierdzić, że geometria jest raczej wynalazkiem ludzkiego umysłu niż odkryciem. Podobnie wzory matematyczne i równania są wykorzystywane do modelowania i przewidywania zjawisk fizycznych, które znów są wynikiem ludzkiego rozumowania." max-tokens="256" box-rows="11" model-temp="0.7" top-p="1"></div>
<br/>.

Wygenerowałem kilka rozszerzeń z tą podpowiedzią i wybrałem jedno, które mi się podobało, aby skończyć z następującym wynikiem końcowym:

<pre>.
    Wśród filozofów i matematyków toczy się wiele dyskusji na temat tego, czy
    <br/>matematyka jest wymyślona czy odkryta. Niektórzy twierdzą, że pojęcia i zasady matematyczne istnieją
    <br/>niezależnie od ludzkich umysłów i dlatego można je uznać za odkryte, a nie wynalezione.
    <br/>Na przykład, pojęcie liczb, proporcji i kształtów geometrycznych są obserwowane w naturalnym
    <br/>świata i mogą być wyabstrahowane i badane w sposób systematyczny.
    <span className="bluegreen-highlight">.
    <br/>.
    <br/>Z drugiej strony niektórzy twierdzą, że matematyka jest w dużej mierze wynalazkiem ludzkiego umysłu. Matematyczne
    <br/>zasady opierają się na logicznym rozumowaniu, które jest cechą ludzkiego umysłu. Na przykład,
    <br/>geometria euklidesowa opiera się na abstrakcyjnych aksjomatach i postulatach, które są przyjmowane jako prawdziwe bez
    <br/>dowodu. Jako taka, można twierdzić, że geometria jest raczej wynalazkiem ludzkiego umysłu niż
    <br/>odkryciem. Podobnie, wzory matematyczne i równania są używane do modelowania i przewidywania zjawisk fizycznych.
    <br/>zjawisk fizycznych, które znów są wynikiem ludzkiego rozumowania.
    </span>.
</pre>.

Używając podpowiedzi rozszerzenia, możemy pisać bardziej przyrostowo i iterować na każdym kroku. Jest to przydatne, gdy potrzebujemy **produkcji wyższej jakości i chcemy zmodyfikować kroki przyrostowe**.

Napisane przez [jayo78](https://twitter.com/jayo782).


