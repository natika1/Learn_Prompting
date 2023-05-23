---
sidebar_position: 7
locale: en-us
styl: chicago
---

# 🟡 Least to Most Prompting

Least to Most prompting (LtM)(@zhou2022leasttomost) przenosi %%CoT prompting|CoT prompting%%% o krok dalej, dzieląc najpierw problem na podproblemy, a następnie rozwiązując każdy z nich. Jest to technika inspirowana rzeczywistymi strategiami edukacyjnymi dla dzieci.  

Podobnie jak w podpowiadaniu CoT, problem do rozwiązania jest rozkładany na zestaw podproblemów, które budują się nawzajem. W drugim kroku te podproblemy są rozwiązywane jeden po drugim. W przeciwieństwie do łańcucha myślenia, rozwiązanie poprzednich podproblemów jest wprowadzane do podpowiedzi próbującej rozwiązać następny problem.

import leastToMost from '@site/docs/assets/least_to_most_formal.png'

<div style={{textAlign: 'center'}}>.
  <img src={leastToMost} style={{szerokość: "600px"}}
        alt="Schemat podpowiedzi od najmniej do najbardziej" />
</div>

<div style={{textAlign: 'center'}}>.
   Schemat podpowiedzi od najmniejszej do największej
</div>

## Przykład: Odpowiedź na zapytanie klienta

Zadajmy nieco skomplikowane pytanie dotyczące obsługi klienta:

<div trydyno-embed="" openai-model="text-davinci-003" initial-prompt="ZAPYTANIE KLIENTA:Właśnie kupiłem koszulkę z waszej kolekcji Arnolda 1 marca. Widziałem, że jest na zniżce, więc kupiłem koszulkę, która była originall $30, i dostałem 40% zniżki. Widziałem, że masz nową zniżkę na koszulki w wysokości 50%. Zastanawiam się, czy mogę zwrócić koszulę i mieć wystarczający kredyt sklepowy, aby kupić dwie wasze koszule? INSTRUKCJE:Jesteś pracownikiem obsługi klienta, którego zadaniem jest uprzejme odpowiadanie na zapytania klientów. Zwroty są dozwolone w ciągu 30 dni. Dzisiejsza data to 29 marca. Obecnie obowiązuje 50% zniżka na wszystkie koszulki. Ceny koszul w Twoim sklepie wahają się od 18$ do 100$. Proszę nie zmyślać informacji o polityce rabatowej." initial-response="Dziękujemy za zapytanie. Niestety, ponieważ zakupił Pan koszulę 1 marca, jest ona poza naszą 30-dniową polityką zwrotów. Jednak mamy 50% zniżki na wszystkie koszule obecnie, więc można kupić dwie koszule z tej samej kwoty kredytu sklepu. Ceny naszych koszul wahają się od 18$ do 100$. Proszę dać nam znać, jeśli masz jakiekolwiek inne pytania." max-tokens="256" box-rows="16" model-temp="0" top-p="0">
    <noscript>Failed to load Dyno Embed: JavaScript musi być włączony</noscript>.
</div>

<br/>To się nie udało (jesteśmy w czasie powrotu), więc spróbujmy podzielić go na podproblemy:

<div trydyno-embed="" openai-model="text-davinci-003" initial-prompt="ZAPYTANIE KLIENTA:Właśnie kupiłem koszulkę z waszej kolekcji Arnolda 1 marca. Widziałem, że jest na zniżce, więc kupiłem koszulkę, która była originall $30, i dostałem 40% zniżki. Widziałem, że macie nową zniżkę na koszulki w wysokości 50%. Zastanawiam się, czy mogę zwrócić koszulę i mieć wystarczający kredyt sklepowy, aby kupić dwie wasze koszule? INSTRUKCJE:Jesteś pracownikiem obsługi klienta, którego zadaniem jest uprzejme odpowiadanie na zapytania klientów. Zwroty są dozwolone w ciągu 30 dni. Dzisiejsza data to 29 marca. Obecnie obowiązuje 50% zniżka na wszystkie koszulki. Ceny koszul w Twoim sklepie wahają się od 18$ do 100$. Nie wymyślaj żadnych informacji o polityce rabatowej.\NJakie podproblemy należy rozwiązać przed udzieleniem odpowiedzi na zapytanie?" initial-response="1. Ustal, czy klient znajduje się w 30-dniowym oknie zwrotów.\N2. Oblicz kwotę kredytu sklepowego, którą klient otrzymałby, gdyby zwrócił koszulę.\N3. Obliczyć koszt dwóch koszul z aktualnym rabatem 50%.\N4. Ustal, czy klient ma wystarczający kredyt w sklepie, aby kupić dwie koszule." max-tokens="256" box-rows="12" model-temp="0" top-p="0">
    <noscript>Failed to load Dyno Embed: JavaScript musi być włączony</noscript>.
</div>

<br/>Spróbujmy rozwiązać pierwszy podproblem:

<div trydyno-embed="" openai-model="text-davinci-003" initial-prompt="ZAPYTANIE KLIENTA:Właśnie kupiłem koszulkę z waszej kolekcji Arnolda 1 marca. Widziałem, że jest na zniżce, więc kupiłem koszulkę, która pierwotnie wynosiła 30 dolarów i dostałem 40% zniżki. Widziałem, że masz nową zniżkę na koszulki w wysokości 50%. Zastanawiam się, czy mogę zwrócić koszulę i uzyskać kredyt sklepowy wystarczający na zakup dwóch waszych koszul? INSTRUKCJE:Jesteś pracownikiem działu obsługi klienta, którego zadaniem jest uprzejme odpowiadanie na zapytania klientów. Zwroty są dozwolone w ciągu 30 dni. Dzisiejsza data to 29 marca. Obecnie obowiązuje 50% zniżka na wszystkie koszulki. Ceny koszul w Twoim sklepie wahają się od 18$ do 100$. Nie zmyślaj żadnych informacji na temat polityki rabatowej.\NOkreśl, czy klient znajduje się w 30-dniowym oknie zwrotu. Przejdźmy krok po kroku." initial-response="Tak, klientowi przysługuje 30-dniowy termin zwrotu. Klient zakupił koszulę 1 marca, a dzisiejsza data to 29 marca, czyli mieści się w 30-dniowym oknie zwrotu. \W związku z tym klient może zwrócić koszulę i otrzymać kredyt sklepowy na zakup. Klient może wykorzystać kredyt sklepowy na zakup dwóch koszul z aktualną 50% zniżką." max-tokens="256" box-rows="19" model-temp="0" top-p="0">
    <noscript>Failed to load Dyno Embed: JavaScript musi być włączony</noscript>.
</div>

Rozwiązując tylko pierwsze podproblemy, byliśmy w stanie rozwiązać cały problem. Jeśli GPT-3 nie zwrócił odpowiedzi natychmiast, mogliśmy rozwiązać następny podproblem i tak dalej, aż zwrócił odpowiedź. Zauważ, że używamy zwrotu `Let's go step by step.`. Dodanie tej frazy nie zawsze jest konieczne, ale w tym przykładzie jest pomocne.


## Przykład: konkatenacja liter

LtM został pierwotnie wprowadzony przy użyciu kilkukrotnych podpowiedzi, a nie wyraźnego polecenia rozbicia problemu na wiele kroków (jak widać powyżej). Dodatkowo, czasami może być zaimplementowany z pojedynczą podpowiedzią, zamiast łańcuchowych podpowiedzi. Zbadajmy problem łączenia ostatnich liter poszczególnych słów (@wei2022chain) (na przykład, biorąc pod uwagę `cake, etymology` jako słowa wejściowe, wyjściem powinno być `ey`).

### Pierwsza próba: Standard

Standardowa podpowiedź z kilkustrzałowymi przykładami wypada bardzo słabo, nawet przy bardziej zaawansowanym modelu, takim jak text-davinci-003.

<div trydyno-embed="" openai-model="text-davinci-003"
     initial-prompt="Q: myśleć, maszyna: uczenie się, rozumowanie, uogólnianie: sztuczna, inteligencja: le: transformator, język, wizja: ren: foo,bar,baz,blip:"
     initial-response="lip"
     max-tokens="256" box-rows="18"
     model-temp="0,2" ></div>

### Druga próba: Chain of Thought
Chain of Thought osiąga znacznie lepsze wyniki niż standardowe podpowiadanie. Dzieje się tak dlatego, że teraz pozwala modelowi samodzielnie rozważyć wyodrębnienie ostatniej litery każdego słowa, zmniejszając złożoność do operacji grupowania liter, które wcześniej zebrał. Jednak przy większych rozmiarach zaczyna się to załamywać.

<div trydyno-embed="" openai-model="text-davinci-003"
     initial-prompt="P: myśl, maszyna: Ostatnią literą słowa &#34;myśl&#34; jest &#34;k&#34;. Ostatnią literą słowa &#34;maszyna&#34; jest &#34;e&#34;. Zatem &#34;myśleć, maszyna&#34; to &#34;ke&#34;.\NQ: uczenie się, rozumowanie, uogólnianie \NA: Ostatnią literą &#34;uczenia się&#34; jest &#34;g&#34;. Ostatnią literą &#34;rozumowania&#34; jest &#34;n&#34;. Ostatnią literą &#34;uogólnienia&#34; jest &#34;n&#34;. Zatem &#34;uczenie się, rozumowanie, uogólnianie&#34; to &#34;ggn&#34;.‖: sztuczna, inteligencja: Ostatnią literą &#34;sztucznej&#34; jest &#34;l&#34;. Ostatnią literą słowa &#34;inteligencja&#34; jest &#34;e&#34;. Zatem &#34;sztuczna, inteligencja&#34; to &#34;le&#34;.\NQ: transformator, język, wizja \NA: Ostatnią literą &#34;transformatora&#34; jest &#34;r&#34;. Ostatnią literą &#34;języka&#34; jest &#34;e&#34;. Ostatnią literą &#34;wizji&#34; jest &#34;n&#34;. Zatem &#34;transformator, język, wizja&#34; to &#34;ren&#34;.ą: foo,bar,baz,blip:"
     initial-response="Ostatnią literą wyrazu &#34;foo&#34; jest &#34;o&#34;. Ostatnią literą wyrazu &#34;bar&#34; jest &#34;r&#34;. Ostatnią literą wyrazu &#34;baz&#34; jest &#34;z&#347. Ostatnią literą słowa &#34;blip&#34; jest &#34;p&#34;. Zatem &#34;foo,bar,baz,blip&#34; to &#34;orzp&#34;."
     max-tokens="256" box-rows="18"
     model-temp="0,2" ></div>

### Trzecia próba: Od najmniejszego do największego (pojedyncza podpowiedź)

W przypadku podpowiadania od najmniejszej do największej, rozszerzamy koncepcję łańcucha myślowego poprzez przeformułowanie poszczególnych kroków tak, aby powtórzyć poprzednio połączony wynik. Upraszcza to każdy krok do łączenia tylko jednej nowej litery. Prowadzi to do dobrych wyników aż do 12 lub więcej słów.

To podejście może wyglądać bardzo podobnie do Chain of Thought, ale jest koncepcyjnie bardzo różne. Tutaj na każdym kroku wprowadzamy poprzednią konkatenację. W przypadku "think, machine, learning" zamiast konkatenacji liter "k", "e", "g" pojedynczo, będzie konkatenować "k" i "e", a następnie "ke" i "g". W wyniku tego ponownego wprowadzenia poprzedniej pracy, model może teraz generalizować do znacznie dłuższych łańcuchów, ponieważ przenosi wynik przyrostowo wzdłuż i musi wykonać tylko niewielką ilość pracy na każdym kroku.

<div trydyno-embed="" openai-model="text-davinci-003"
     initial-prompt="P: myśl, maszyna: Ostatnią literą słowa &#34;myśl&#34; jest &#34;k&#34;. Ostatnią literą słowa &#34;maszyna&#34; jest &#34;e&#34;. Złożenie &#34;k&#34; i &#34;e&#34; daje &#34;ke&#34;. Zatem &#34;myśl, maszyna&#34; wyprowadza &#34;ke&#34;.\NQ: myśl, maszyna, nauka&#347: &#34;myśl, maszyna&#34; wyprowadza &#34;ke&#34;. Ostatnią literą &#34;nauki&#34; jest &#34;g&#34;. Złożenie &#34;ke&#34; i &#34;g&#34; daje &#34;keg&#34;. Zatem &#34;myśleć, maszyna, uczenie się&#34; to &#34;keg&#34;.‖: transformator, język‖: Ostatnią literą &#34;transformatora&#34; jest &#34;r&#34;. Ostatnią literą &#34;języka&#34; jest &#34;e&#34;. Konkatenacja &#34;r&#34; i &#34;e&#34; daje &#34;re&#34;. Zatem &#34;transformator, język&#34; to &#34;re&#34;.‖: transformator, język, wizja&#346↩: &#34;transformator, język&#34; daje &#34;re&#34;. Ostatnią literą &#34;wizji&#34; jest &#34;n&#34;. Konkatenacja &#34;re&#34; i &#34;n&#34; daje &#34;ren&#34;. Tak więc &#34;transformator, język, wizja&#34; to &#34;ren&#34;.\": foo,bar,baz,blip,learn,prompting,world,shaking,event,dancefloor,prisma,giraffe.
     initial-response="Ostatnią literą wyrazu &#34;foo&#34; jest &#34;o&#34;. Ostatnią literą wyrazu &#34;bar&#34; jest &#34;r&#34;. Złożenie &#34;o&#34; i &#34;r&#34; daje &#34;lub&#34;. Ostatnią literą wyrazu &#34;baz&#34; jest &#34;z&#347. Złożenie &#34;lub&#34; i &#34;z&#34; daje &#34;orz&#34;. Ostatnią literą wyrazu &#34;blip&#34; jest &#34;p&#34;. Złożenie &#34;orz&#34; i &#34;p&#34; daje &#34;orzp&#34;. Ostatnią literą wyrazu &#34;learn&#34; jest &#34;n&#34;. Złożenie &#34;orzp&#34; i &#34;n&#34; daje &#34;orzpn&#34;. Ostatnią literą &#34;podpowiedzi&#34; jest &#34;g&#34;. Konkatenacja &#34;orzpn&#34; i &#34;g&#34; daje &#34;orzpng&#34;. Ostatnią literą &#34;świata&#34; jest &#34;d&#34;. Konkatenacja &#34;orzpng&#34; i &#34;d&#34; daje &#34;orzpngd&#34;. Ostatnią literą wyrazu &#34;shaking&#34; jest &#34;g&#34;. Konkatenacja &#34;orzpngd&#34; i &#34;g&#34; daje &#34;orzpngdg&#34;. Ostatnią literą &#34;zdarzenia&#34; jest &#34;t&#34;. Konkatenacja &#34;orzpngdg&#34; i &#34;t&#34; daje &#34;orzpngdgt&#34;."
     max-tokens="256" box-rows="18"
     model-temp="0,2" ></div>
     

### Wyniki

W przypadku problemu łączenia ostatnich liter w 12 słowach, Chain of Thought osiąga 34% dokładność, podczas gdy Least to Most 74% dokładność (w artykule jako model wykorzystano text-davinci-002).

## Przykład: generalizacja kompozycyjna (SCAN)

Benchmark SCAN (@lake2018scan) wymaga od modelu konwersji języka naturalnego na sekwencje działań. Na przykład zdanie "biegnij w lewo i przejdź dwa razy" zostanie przetłumaczone na "TURN_LEFT + RUN + WALK * 2". Modele językowe radzą sobie szczególnie słabo w konfrontacji z sekwencjami, które są dłuższe niż te w zestawie treningowym.

### Pierwsza próba: Standardowe podpowiedzi

Używając prostych, standardowych podpowiedzi, text-davinci-003 dociera imponująco daleko, ale wciąż nie udaje się.

<div trydyno-embed="" openai-model="text-davinci-003"
     initial-prompt="P: skręć w lewo &#43; skręć w prawo&#8221: skocz w lewo &#43; JUMP&#8221: biegnij w prawo &#43; RUN&#8221: spojrzenie dwa razy * 2: bieg i spojrzenie dwa razy * 2: bieg &#43; spojrzenie * 2: skok w prawo trzy razy * 3: spacer po biegu * 3: bieg &#43; WALK: obrót naprzeciwko lewej strony * 2nQ: obrót wokół lewej strony * 4nQ: obrót naprzeciwko prawej strony * 2nQ: obrót wokół prawej strony * 4nQ: spacer naprzeciwko lewej strony * 2 &#43; WALK: spacer dookoła lewej strony (TURN LEFT &#43; WALK) * 4 &#34;skok dookoła lewej strony dwa razy po spacerze naprzeciwko lewej strony trzy razy&#34;".
     initial-response="(TURN LEFT * 2 + WALK) * 3 + (TURN LEFT + JUMP) * 2"
     max-tokens="512" box-rows="18"
     model-temp="0,2" ></div>

### Druga próba: Od najmniejszego do największego, pierwszy krok - redukcja

Tutaj pracujemy z 2 różnymi podpowiedziami. Pierwsza z nich służy do zredukowania problemu wejściowego do prostszej sekwencji kroków. Druga zachęta jest używana do odwzorowania tej uproszczonej sekwencji kroków w rzeczywiste działania.

Obie podpowiedzi są dość długie i używają skompresowanej notacji python dla akcji, aby zaoszczędzić na tokenach.

Pierwszy krok rozbija opis języka naturalnego na bardziej jednoznaczny, ale wciąż podobny do ludzkiego język. Pomoże to krokowi mapowania rozgryźć rzeczy w kolejności.
Na przykład, "jump around left twice" jest zredukowane do "jump left" -> `TURN_LEFT + JUMP` i "jump around left" -> `(TURN_LEFT + JUMP) * 4`. Podobnie, krok redukcji jest tym, co jest używane do wyjaśnienia koncepcji powtórzenia (dwa razy, trzy razy, itd...).

<div trydyno-embed="" openai-model="text-davinci-003"
     initial-prompt="P: spojrzeć w prawo po spojrzeniu dwa razy można rozwiązać: &#34;spojrzeć w prawo&#34;, &#34;spojrzeć dwa razy&#34;.\●● skocz naprzeciwko prawej trzykrotnie i przejdź &#34;skocz naprzeciwko prawej trzykrotnie&#34; można rozwiązać przez: &#34;skocz naprzeciwko prawej&#34;, &#34;skocz naprzeciwko prawej trzykrotnie&#34;. &#34;przejdź&#34; można rozwiązać przez: &#34;przejdź&#34;. Zatem &#34;skok naprzeciwko prawej trzykrotnie i spacer&#34; można rozwiązać przez: &#34;skok naprzeciwko prawej&#34;, &#34;skok naprzeciwko prawej trzykrotnie&#34;, &#34;spacer&#34;.\●● bieg w lewo dwa razy i bieg w prawo &#34;bieg w lewo dwa razy&#34; można rozwiązać przez: &#34;bieg w lewo&#34;, &#34;bieg w lewo dwa razy&#34;. &#34;bieg w prawo&#34; można rozwiązać przez &#34;bieg w prawo&#34;. Zatem &#34;biegnij w lewo dwa razy i biegnij w prawo&#34; można.rozwiązać przez: &#34;biegnij w lewo&#34;, &#34;biegnij w lewo dwa razy&#34;, &#34;biegnij w prawo&#34;.‖: &#34;biegnij naprzeciwko w prawo&#34; można rozwiązać przez &#34;biegnij naprzeciwko w prawo&#34;.\ŃQ: spojrzeć przeciwnie do prawej trzykrotnie po spacerze ŃQ: &#34;spojrzeć przeciwnie do prawej trzykrotnie&#34; można rozwiązać przez: &#34;spojrzeć przeciwnie do prawej&#34;, &#34;spojrzeć przeciwnie do prawej trzykrotnie&#34;. &#34;Spacer&#34; można rozwiązać przez &#34;spacer&#34;. Zatem &#34;spojrzenie naprzeciwko prawej trzykrotnie po spacerze&#34; można rozwiązać przez: &#34;spojrzenie naprzeciwko prawej&#34;, &#34;spojrzenie naprzeciwko prawej trzykrotnie&#34;, &#34;spacer&#34;.\NQ: skok w prawo&#34; &#34;skok w prawo&#34; można rozwiązać przez: &#34;skok w prawo&#34;, &#34;skok w prawo&#34;. Zatem &#34;skok w prawo&#34; można rozwiązać za pomocą: &#34;skok w prawo&#34;, &#34;skok w prawo&#34;.\Rozejrzyj się w prawo trzykrotnie i przejdź &#34;Rozejrzyj się w prawo trzykrotnie&#34; można rozwiązać przez: &#34;rozejrzyj się w prawo&#34;, &#34;rozejrzyj się w prawo&#34;, &#34;rozejrzyj się w prawo trzykrotnie&#34;. &#34;Przejdź&#34; można rozwiązać przez &#34;przejdź&#34;. Zatem &#34;rozejrzeć się w prawo trzykrotnie i przejść&#34; można rozwiązać przez: &#34;rozejrzeć się w prawo&#34;, &#34;rozejrzeć się w prawo trzykrotnie&#34;, &#34;przejść&#34;.\●● skręć w prawo po biegnij w prawo trzykrotnie&#34; można rozwiązać przez: &#34;skręć w prawo&#34;. &#34;biegnij w prawo trzykrotnie&#34; można rozwiązać przez: &#34;biegnij w prawo&#34;, &#34;biegnij w prawo trzykrotnie&#34;. Zatem &#34;obrót w prawo po biegu w prawo trzykrotnie&#34; można rozwiązać w następujący sposób: &#34;obrót w prawo&#34;, &#34;bieg w prawo&#34;, &#34;bieg w prawo trzykrotnie&#34;.\"
     initial-response="&#34;jump around left twice&#34; można rozwiązać za pomocą: &#34;jump left&#34;, &#34;jump around left twice&#34;. &#34;walk opposite left thrice&#34; można rozwiązać za pomocą: &#34;walk opposite left&#34;, &#34;walk opposite left thrice&#34;. Zatem &#34;skok w lewo dwa razy po przejściu naprzeciwko lewej trzy razy&#34; można rozwiązać przez: &#34;skok w lewo&#34;, &#34;skok w lewo&#34;, &#34;skok w lewo dwa razy&#34;, &#34;przejście naprzeciwko lewej&#34;, &#34;przejście naprzeciwko lewej trzy razy&#34;".
     max-tokens="256" box-rows="18"
     model-temp="0,2" ></div>

### Druga próba: Od najmniejszego do największego, drugi krok - mapowanie

W drugim kroku korzystamy z wyjścia redukcji i ponownie używamy dość długiej podpowiedzi (14 przypadków), aby przełożyć zredukowany opis języka naturalnego na sekwencję działań.

Tutaj wstrzykujemy wyjście z pierwszego kroku:

> "jump around left twice" może być rozwiązany przez: "jump left", "jump around left", "jump around left twice". "walk opposite left thrice" można rozwiązać przez: "walk opposite left", "walk opposite left thrice". Zatem "jump around left twice after walk opposite left thrice" można rozwiązać przez: "jump left", "jump around left", "jump around left twice", "walk opposite left", "walk opposite left thrice".

do LLM.

<div trydyno-embed="" openai-model="text-davinci-003"
     initial-prompt="Q: turn left: &#34;turn left&#34; outputs &#34;TURN LEFT&#34;.\NQ: turn right: &#34;turn right&#34; outputs &#34;TURN RIGHT&#34;.\Wyjście &#34;skok w lewo&#34; konkatenuje: wyjście &#34;zwrot w lewo&#34;, wyjście &#34;skok&#34;. &#34;zwrot w lewo&#34; daje wyjście &#34;TURN LEFT&#34;. &#34;skok&#34; daje wyjście &#34;JUMP&#34;. Zatem konkatenacja wyjścia &#34;skręć w lewo&#34; i wyjścia &#34;skocz&#34; prowadzi do &#34;TURN LEFT&#34; &#43; &#34;JUMP&#34;. Tak więc wyjściem &#34;skoku w lewo&#34; jest &#34;TURN LEFT&#34; &#43; &#34;JUMP&#34;.\NQ: run right&#34;: Wyjście &#34;run right&#34; konkatenuje: wyjście &#34;turn right&#34;, wyjście &#34;run&#34;. &#34;Turn right&#34; wyprowadza &#34;TURN RIGHT&#34;. &#34;Run&#34; wyprowadza &#34;RUN&#34;. Zatem konkatenacja wyjścia &#34;skręć w prawo&#34; i wyjścia &#34;biegnij&#34; prowadzi do &#34;skręć w prawo&#34; &#43; &#34;biegnij&#34;. Zatem wyjściem &#34;biegu w prawo&#34; jest &#34;TURN RIGHT&#34; &#43; &#34;BIEG&#34;.\NQ: look twice&#34;: Wyjście &#34;look twice&#34; konkatenuje: wyjście &#34;look&#34;, wyjście &#34;look&#34;. &#34;look&#34; wyprowadza &#34;LOOK&#34;. Zatem powtórzenie wyjścia &#34;look&#34; dwa razy prowadzi do &#34;LOOK&#34; * 2. Tak więc wyjściem &#34;szukaj dwa razy&#34; jest &#34;POŻYTEK&#34; * 2.\NQ: biegnij i patrz dwa razy 
A: Wyjście &#34;biegnij i patrz dwa razy&#34; konkatenuje: wyjście &#34;biegnij&#34;, wyjście &#34;patrz dwa razy&#34;. &#34;run&#34; wyprowadza &#34;RUN&#34;. &#34;look twice&#34; wyprowadza &#34;LOOK&#34; * 2. Zatem konkatenacja wyjścia &#34;run&#34; i wyjścia &#34;look twice&#34; prowadzi do &#34;RUN&#34; &#43; &#34;LOOK&#34; * 2. Zatem wyjściem &#34;biegnij i popatrz dwa razy&#34; jest &#34;RUN&#34; &#43; &#34;LOOK&#34; * 2.\Wyjście &#34;skocz w prawo trzykrotnie&#34; konkatenuje: wyjście &#34;skocz w prawo&#34;, wyjście &#34;skocz w prawo&#34;, wyjście &#34;skocz w prawo&#34;. &#34;skocz w prawo&#34; daje wyjście &#34;TURN RIGHT&#34; &#43; &#34;JUMP&#34;. Zatem powtórzenie wyjścia &#34;skoku w prawo&#34; trzykrotnie prowadzi do (&#34;TURN RIGHT&#34; &#43; &#34;JUMP&#34;) * 3. Zatem wyjściem &#34;skoku w prawo trzykrotnie&#34; jest (&#34;TURN RIGHT&#34; &#43; &#34;JUMP&#34;) * 3.\Wyjście &#34;spacer po biegu&#34; konkatenuje: wyjście &#34;bieg&#34;, wyjście &#34;spacer&#34;. &#34;bieg&#34; wyprowadza &#34;RUN&#34;. &#34;spacer&#34; wyprowadza &#34;WALK&#34;. Zatem konkatenacja wyjścia &#34;run&#34; i wyjścia &#34;walk&#34; prowadzi do &#34;RUN&#34; &#43; &#34;WALK&#34;. Zatem wyjściem &#34;spaceru po biegu&#34; jest &#34;BIEG&#34; &#43; &#34;SPACER&#34;.\NQ: skręt w lewo&#34;: Wyjście &#34;skręt w lewo&#34; konkatenuje: wyjście &#34;skręt w lewo&#34;, wyjście &#34;skręt w lewo&#34;. &#34;skręt w lewo&#34; wyprowadza &#34;skręt w lewo&#34;. Zatem powtórzenie wyjścia &#34;skręć w lewo&#34; dwa razy prowadzi do &#34;TURN LEFT&#34; * 2. Zatem wyjściem &#34;skrętu w lewo&#34; jest &#34;TURN LEFT&#34; * 2.\Wyjście &#34;skręć w lewo&#34; konkatenuje: wyjście &#34;skręć w lewo&#34;, wyjście &#34;skręć w lewo&#34;, wyjście &#34;skręć w lewo&#34;, wyjście &#34;skręć w lewo&#34;, wyjście &#34;skręć w lewo&#34;. &#34;skręć w lewo&#34; wyprowadza &#34;TURN LEFT&#34;. Zatem powtórzenie wyjścia &#34;skręć w lewo&#34; cztery razy prowadzi do &#34;TURN LEFT&#34; * 4. Zatem wyjściem &#34;skręć w lewo&#34; jest &#34;TURN LEFT&#34; * 4.\●● skręt w prawo ●● Wyjście &#34;skręt w prawo&#34; konkatenuje: wyjście &#34;skręt w prawo&#34;, wyjście &#34;skręt w prawo&#34;. &#34;skręt w prawo&#34; wyprowadza &#34;skręt w prawo&#34;. Zatem powtórzenie wyjścia &#34;skręć w prawo&#34; dwa razy prowadzi do &#34;skręć w prawo&#34; * 2. Zatem wyjściem &#34;skrętu w prawo&#34; jest &#34;TURN RIGHT&#34; * 2.\Wyjście &#34;skręć w prawo&#34; konkatenuje: wyjście &#34;skręć w prawo&#34;, wyjście &#34;skręć w prawo&#34;, wyjście &#34;skręć w prawo&#34;, wyjście &#34;skręć w prawo&#34;, wyjście &#34;skręć w prawo&#34;. &#34;skręć w prawo&#34; wyprowadza &#34;ZWRÓĆ SIĘ W PRAWO&#34;. Zatem powtórzenie wyjścia &#34;obróć się w prawo&#34; cztery razy prowadzi do &#34;TURN RIGHT&#34; * 4. Zatem wyjściem &#34;obróć się w prawo&#34; jest &#34;TURN RIGHT&#34; * 4.\●● chodzenie naprzeciwko lewej: Wyjście &#34;chodzenie naprzeciwko lewej&#34; konkatenuje: wyjście &#34;obrót naprzeciwko lewej&#34;, wyjście &#34;chodzenie&#34;. &#34;obrót naprzeciwko lewej&#34; wyprowadza &#34;OBRÓT W LEWO&#34; * 2. &#34;chodzenie&#34; wyprowadza &#34;CHODZENIE&#34;. Zatem konkatenacja wyjścia &#34;obrót w lewo&#34; i wyjścia &#34;spacer&#34; prowadzi do &#34;TURN LEFT&#34; * 2 &#43; &#34;WALK&#34;. Zatem wyjściem &#34;spaceru naprzeciwko lewej&#34; jest &#34;TURN LEFT&#34; * 2 &#43; &#34;WALK&#34;.\●● chodzenie naokoło w lewo&#34; Wyjście &#34;chodzenie naokoło w lewo&#34; konkatenuje: wyjście &#34;chodzenie naokoło w lewo&#34;, wyjście &#34;chodzenie naokoło w lewo&#34;, wyjście &#34;chodzenie naokoło w lewo&#34;. &#34;chodzenie naokoło w lewo&#34; wyprowadza &#34;TURN LEFT&#34; &#43; &#34;WALK&#34;. Zatem powtórzenie wyjścia &#34;spacer w lewo&#34; cztery razy prowadzi do (&#34;TURN LEFT&#34; &#43; &#34;WALK&#34;) * 4. Zatem wyjściem polecenia &#34;Obejdź się w lewo&#34; jest (&#34;OBRÓĆ SIĘ W LEWO&#34; &#43; &#34;OBEJDŹ SIĘ&#34;) * 4.\"
     initial-response="Wyjście z &#34;jump around left twice after walk opposite left thrice&#34; konkatenuje: wyjście z &#34;walk opposite left thrice&#34;, wyjście z &#34;jump around left twice&#34;. &#34;Walk opposite left thrice&#34; wyprowadza &#34;TURN LEFT&#34; * 2 + &#34;WALK&#34; * 3. &#34;Jump around left twice&#34; wyprowadza (&#34;TURN LEFT&#34; + &#34;JUMP&#34;) * 4. Zatem konkatenacja wyjścia &#34;spaceru w lewo trzy razy&#34; i wyjścia &#34;skoku w lewo dwa razy&#34; prowadzi do &#34;TURN LEFT&#34; * 2 + &#34;WALK&#34; * 3 + (&#34;TURN LEFT&#34; + &#34;JUMP&#34;) * 4. Tak więc wyjściem dla &#34;skoku w lewo dwa razy po przejściu naprzeciwko lewej trzy razy&#34; jest &#34;TURN LEFT&#34; * 2 + &#34;WALK&#34; * 3 + (&#34;TURN LEFT&#34; + &#34;JUMP&#34;) * 4."
     max-tokens="1024" box-rows="18"
     model-temp="0,2" ></div>

### Wyniki

LtM prowadzi do wielu ulepszeń:
- poprawę dokładności w stosunku do Łańcucha Myśli
- zwiększoną generalizację na problemy trudniejsze niż te w podpowiedzi
- radykalnie poprawiona wydajność w generalizacji kompozycyjnej, w szczególności w benchmarku SCAN (@lake2018scan)

Standardowe podpowiadanie przy użyciu text-davinci-002 (model użyty w artykule) skutkuje 6% pomyślnie rozwiązanych problemów SCAN, podczas gdy podpowiadanie Least to Most daje imponujący 76% wskaźnik sukcesu. Wyniki są jeszcze bardziej znaczące w przypadku code-davinci-002, gdzie Least to Most prompting osiąga 99,7% sukcesu.


