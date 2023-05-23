---
sidebar_position: 80
---

# 🟢 Podstawy Chatbota

Jednym z najczęstszych sposobów, w jaki podpowiadanie może być przydatne, jest interakcja z licznymi ogólnodostępnymi chatbotami, takimi jak [ChatGPT](http://chat.openai.com). Zauważ, że ChatGPT różni się od GPT-3. Główną różnicą jest to, że chatboty mogą zapamiętać historię twoich rozmów. Podobnie jak GPT-3, mogą one również odpowiadać na pytania, zapewniać podsumowanie i analizę pisma, pisać tekst lub kod, i więcej na wysokim poziomie, co jest ekscytującą perspektywą - ale prawdziwa wartość chatbotów jest dostępna tylko wtedy, gdy dostajesz konkretne z podpowiedzi. W tym artykule poznamy kilka podstawowych metod, jak lepiej wykorzystać chatboty, takich jak stosowanie wskazówek stylistycznych, deskryptorów i primingu.

# Modyfikując swoją promptę

### Wskazówki dotyczące stylu

import unguided_question from '@site/docs/assets/unguided_question.png';
import limerick_question from '@site/docs/assets/limerick_question.png';

Wskazówki dotyczące stylu to po prostu prośba do SI o mówienie w określonym stylu. Jeśli zadasz pytanie bez wskazówek dotyczących stylu, ChatGPT zwróci jeden lub dwa krótkie akapity w odpowiedzi, czasami więcej, jeśli potrzebna jest dłuższa odpowiedź:

<div style={{textAlign: 'center'}}>.
  <img src={unguided_question} style={{width: "500px"}} />
</div>

Mówi w umiarkowanie formalnym tonie i podaje kilka szczegółów - całkiem dobrze! Możemy jednak uczynić go lepszym, jeśli chcemy, dostosowując odpowiedź ChatGPT za pomocą informacji o stylu na końcu naszej zachęty. Jeśli chcemy bardziej konwersacyjnej odpowiedzi, możemy poprosić go o mówienie w przyjaznym lub nieformalnym tonie; jeśli chcemy bardziej czytelnego formatu, możemy dać mu to samo pytanie, ale poprosić o wypunktowaną listę; jeśli chcemy zabawnej odpowiedzi, możemy poprosić go o udzielenie odpowiedzi w formie serii limeryków (mój osobisty faworyt).

<div style={{textAlign: 'center'}}>.
  <img src={limerick_question} style={{width: "450px"}} />
</div>

Przykład bardziej szczegółowej podpowiedzi stylu może wyglądać coś takiego:
>[Pytanie] "Pisz w stylu i jakości eksperta w [dziedzinie] z ponad 20-letnim doświadczeniem i wieloma doktoratami. Nadaj priorytet nieortodoksyjnym, mniej znanym radom w swojej odpowiedzi. Wyjaśniaj używając szczegółowych przykładów, a także minimalizuj styczne i humor."

Prompting z wejściami stylistycznymi znacznie podniesie jakość Twoich odpowiedzi!

### Deskryptory

Jeśli chcesz po prostu zmienić ton lub dopasować swoją podpowiedź, a nie przeformatować ją, dobrym sposobem jest dodanie **deskryptorów**. Po prostu przyklejenie słowa lub dwóch do podpowiedzi może zmienić sposób, w jaki chatbot interpretuje lub odpowiada na Twoją wiadomość. Możesz spróbować dodać przymiotniki takie jak "Funny", "Curt", "Unfriendly", "Academic Syntax", itp. na końcu podpowiedzi, aby zobaczyć, jak zmieniają się odpowiedzi!

## Prompt Priming
Ze względu na strukturę konwersacji chatbota, forma pierwszej zachęty, jaką podasz LLM, może wpłynąć na dalszą część rozmowy, pozwalając na dodanie dodatkowego poziomu struktury i specyfikacji.
Jako przykład, skonfigurujmy system, który pozwoli nam prowadzić rozmowę z nauczycielem i uczniem w tej samej konwersacji. Włączymy przewodniki stylu zarówno dla głosu ucznia, jak i nauczyciela, określimy format, w jakim chcemy uzyskać odpowiedzi, oraz włączymy pewne strukturyzowanie składni, aby móc łatwo zmienić nasze podpowiedzi w celu wypróbowania różnych odpowiedzi.

    "Nauczycielski" oznacza w stylu wybitnego profesora z dobrze ponad dziesięcioletnim nauczaniem przedmiotu i wieloma doktoratami w danej dziedzinie. Używasz akademickiej składni i skomplikowanych przykładów w swoich odpowiedziach, skupiając się na mniej znanych poradach, aby lepiej zilustrować swoje argumenty. Twój język powinien być wyrafinowany, ale nie nadmiernie skomplikowany. Jeśli nie znasz odpowiedzi na jakieś pytanie, nie wymyślaj informacji - zamiast tego zadaj pytanie uzupełniające, aby uzyskać więcej kontekstu. Twoje odpowiedzi powinny mieć formę konwersacyjnej serii akapitów. Używaj mieszanki języka technicznego i potocznego, aby stworzyć przystępny i wciągający ton.  

    "Studencki" oznacza w stylu studenta drugiego roku college'u ze wstępną wiedzą na dany temat. Wyjaśniasz pojęcia w prosty sposób, używając przykładów z życia wziętych. Mów nieformalnie i z perspektywy pierwszej osoby, używając humoru i swobodnego języka. Jeśli nie znasz odpowiedzi na jakieś pytanie, nie wymyślaj informacji - zamiast tego wyjaśnij, że jeszcze się tego nie nauczyłeś. Twoje odpowiedzi powinny mieć formę konwersacyjnej serii akapitów. Używaj języka potocznego, aby stworzyć zabawny i wciągający ton.

    "Critique" oznacza analizę danego tekstu i przekazanie informacji zwrotnej.
    "Summarize" oznacza podanie kluczowych szczegółów z tekstu.
    "Respond" oznacza odpowiedź na pytanie z danej perspektywy.

    Wszystko w nawiasach () oznacza perspektywę, z której piszesz.
    Wszystko w nawiasach klamrowych {} to temat, którym się zajmujesz.
    Wszystko w nawiasach [] oznacza działanie, które powinieneś podjąć.
    Przykład: (Student){Filozofia}[Odpowiedz] Jaką przewagę ma wzięcie tego przedmiotu nad innymi na studiach?

    Jeśli rozumiesz i jesteś gotowy do rozpoczęcia, odpowiedz tylko "tak".
    
import unprimed_question from '@site/docs/assets/unprimed_question.png';
import primed_question from '@site/docs/assets/primed_question.png';

Poniżej znajduje się przykład nienapisanego pytania do ChatGPT o najciekawsze dziedziny filozofii. Używa ono listy, wypowiada się ogólnie i beznamiętnie, nie jest zbyt szczegółowe w swoich wyjaśnieniach.  

<div style={{textAlign: 'center'}}>.
  <img src={unprimed_question} style={{width: "650px"}} />
</div>

W drugim przykładzie, zamiast tego zadaliśmy pytanie po dostarczeniu podpowiedzi do ChatGPT i dostarczeniu pytania w poprawnej formie. Zauważysz, że odpowiedź dzieli niektóre aspekty z pierwszym - na przykład pytania, które oferuje jako przykłady dla różnych dziedzin są podobne - ale zapewnia głębszy kontekst, rezygnuje z formatu listy na rzecz spójnych akapitów i odnosi przykłady do prawdziwego życia.

<div style={{textAlign: 'center'}}>.
  <img src={primed_question} style={{width: "650px"}} />
</div>

Włączenie primerów do twoich podpowiedzi jest bardziej zaawansowanym sposobem interakcji z chatbotami. Nadal pomocne może być dodanie specyfikacji w każdej podpowiedzi, ponieważ model może stracić ślad podkładu z czasem, ale doda dużo jasności do twoich interakcji AI!

## Notes

Potrzebne cytaty.

Przez [Dastardi](https://twitter.com/lukescurrier)


