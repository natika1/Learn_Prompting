---
sidebar_position: 600
---

# 🟢 Zapier for Emails.

import Basic from '@site/docs/assets/Zapiermail/Basic.png';
import Diagram from '@site/docs/assets/Zapiermail/Diagram.png';
import Step1 from '@site/docs/assets/Zapiermail/Step1.png';
import Step2 from '@site/docs/assets/Zapiermail/Step2.png';
import Step3 from '@site/docs/assets/Zapiermail/Step3.png';
import Step4 from '@site/docs/assets/Zapiermail/Step4.png';
import Zap from '@site/docs/assets/Zapiermail/Zap.png';

## Wprowadzenie


Widzieliśmy już jak przydatny może być GPT-3 jeśli chodzi o maile. Może być jeszcze bardziej, gdy połączysz go z **nocode** narzędziami takimi jak [Zapier](https://zapier.com) czy [Bubble.io](https://bubble.io).

Ten artykuł będzie zawierał przykład tego, co Zapier+GPT-3 może zrobić przy niewielkim czasie konfiguracji. Ten artykuł skupia się na konkretnym przykładzie, ale możliwości są znacznie większe. Po drodze podamy kilka innych przykładów. Pamiętaj, że możesz to zrobić również w Bubble.io. Istnieje wiele innych narzędzi nocode, ale w chwili pisania tego artykułu tylko kilka pozwala na użycie GPT-3.


W tym artykule pokażemy Ci jak skonfigurować prosty system w Zapier, w którym **e-maile są podsumowywane i przechowywane**. Masz przed sobą spotkanie z kimś? Szybko sprawdź podsumowania maili, które wymieniłeś z tą osobą. Skonfigurowanie tego zajmuje około 20 minut.

:::ostrożność
Pomocne jest, aby już znać Zapier dla tego artykułu. Jeśli nie, możesz sprawdzić ten [artykuł](https://zapier.com/learn/)
:::


## General Idea


Poniżej znajduje się schemat tego, co będziemy robić tutaj w Zapier. Za każdym razem, gdy wiadomość e-mail pojawi się w skrzynce odbiorczej, uruchomi ona Zapier. Istnieją cztery kroki (na razie):

1. Przychodzi e-mail i uruchamia Zapier
1. Sformatuj treść wiadomości e-mail (aby usunąć markdown HTML, na przykład).
2. Wyślij go do GPT-3, aby został podsumowany.
3. Zapisz dane wyjściowe w bazie danych

<div style={{textAlign: 'left'}}>.
  <img src={Diagram} style={{szerokość: "500px"}} />
</div>

## Konfiguracja w Zapier


Upewnij się, że masz [konto Zapier](https://zapier.com/sign-up) (możesz dostać darmowe). Skonfigurowanie go powinno być dość proste. Po utworzeniu konta rozwiń poniższe pole, aby zobaczyć pełne opisy każdej akcji Zapier, którą musimy stworzyć.


<details>
  <summary>Expand for a more detailed view of the steps in Zapier</summary>
  <div>
  This is what the Zapier action diagram will eventually look like.
    <div><div style={{textAlign: 'left'}}>
  <img src={Zap} style={{width: "500px"}} />
</div></div>
    <br/>
    <details>
      <summary>
        Step 1: Gmail trigger on new incoming email (Gmail is used here).
      </summary>
      <div>
        <div style={{textAlign: 'left'}}>
    <img src={Step1} style={{width: "500px"}} />
        </div>
      </div>
</details>
<details>
      <summary>
       Step 2: Formatter for E-mail content. 
      </summary>
      <div>
        <div style={{textAlign: 'left'}}>
  <img src={Step2} style={{width: "500px"}} />
</div>
      </div>
</details>
<details>
      <summary>
        Step 3: Prompting the Email content
        <br/>
      </summary>
      <div>
        <div style={{textAlign: 'left'}}>
  <img src={Step3} style={{width: "500px"}} />
</div>
      </div>
</details>
<details>
      <summary>
        Step 4: Adding it to a database
      </summary>
      <div>
        <div style={{textAlign: 'left'}}>
  <img src={Step4} style={{width: "500px"}} />
</div>
      </div>
    </details>
  </div>
</details>
Oto konfiguracja w zapier, która pozwala zrobić bardzo podstawowe podsumowanie, jak pokazano na schemacie. Ma swoje ograniczenia, ale wykonuje pracę i może zbudować użyteczną bazę danych.


# Optymalizacja podpowiedzi dla lepszych wyników

Istnieje kilka łatwych sposobów na poprawę wyników. Dodanie kontekstu i podpowiadanie ról może poprawić dane wyjściowe. Jednak temat i treść twoich e-maili może obejmować szeroki zakres tematów. Oznacza to, że ogólne instrukcje zrobią lepszą robotę niż bardzo szczegółowe, które mogą wyrzucić model.

Ze względów praktycznych przydatne jest podanie instrukcji, a następnie powiedzenie GPT-3, kiedy e-mail zaczyna się w zachęcie, dodając po prostu "Email: " i kończąc prompt z ""Summary": ". Pozwala to uniknąć sytuacji, w której GPT-3 odpowiada "Jasne! Mogę to dla ciebie streścić...".

Podpowiadanie ról może być przydatne również w tym przypadku. Poproszenie GPT-3 o pełnienie roli osobistego asystenta pomaga zwiększyć jakość podsumowania.
Jeśli chcesz podsumować emaile z pracy, po prostu dodając rolę, którą pełnisz, dajesz GPT-3 kontekst do pracy. Działa on tak, jakby zakładał pewien poziom wiedzy czytelnika, co pomaga odfiltrować nieistotne części emaila.
Poniżej pokazujemy kilka przykładów z emaili, które może otrzymać administrator biura.

Możesz poprosić go, aby podsumować prosty e-mail w punktach, jednak może to nie być wszystko, że przydatne w zależności od tego, jak chcesz użyć podsumowania. Do szybkiego przeglądania wiadomości e-mail możesz chcieć, aby były one krótkie i zwięzłe. Proste zapytanie o to w zachęcie działa dobrze. Poniżej znajduje się przykład takiej zachęty. Dostosuj go i baw się nim, aby zobaczyć, jak się zmienia.4


<iframe
    src="https://embed.learnprompting.org/embed?config=eyJ0b3BQIjoxLCJ0ZW1wZXJhdHVyZSI6MC43LCJtYXhUb2tlbnMiOjI1Niwib3V0cHV0IjoiUmVxdWVzdCBmb3IgYWRkaXRpb25hbCBvZmZpY2Ugc3VwcGxpZXMgZHVlIHRvIGhpZ2ggd29ya2xvYWQuIExpc3Qgb2YgcmVxdWVzdGVkIGl0ZW1zOiBwcmludGVyIHBhcGVyLCBpbmsgY2FydHJpZGdlcyBmb3IgSFAgcHJpbnRlciBpbiBjb25mZXJlbmNlIHJvb20sIHN0aWNreSBub3RlcywgYmluZGVyIGNsaXBzLCBhbmQgaGlnaGxpZ2h0ZXJzLiBSZXF1ZXN0aW5nIGRlbGl2ZXJ5IGluZm9ybWF0aW9uIGFuZCBpZiB0aGVyZSBhcmUgYW55IHF1ZXN0aW9ucyBvciBjb25jZXJucy4iLCJwcm9tcHQiOiJBY3QgYXMgbXkgcGVyc29uYWwgYXNzaXN0YW50LiBJIGFtIGFuIG9mZmljZSBhZG1pbmlzdHJhdG9yLiBTdW1tYXJpemUgdGhlIGZvbGxvd2luZyBlbWFpbCBhcyBjb25jaXNlbHkgYXMgeW91IGNhbiwgaWdub3JlIHRoZSBmb290ZXIgYW5kIGhlYWRlciBhbmQgYW55IHByZXZpb3VzIGVtYWlscy4gXG5cbkVtYWlsOiBSZXF1ZXN0IGZvciBBZGRpdGlvbmFsIE9mZmljZSBTdXBwbGllcyBEZWFyIE9mZmljZSBBZG1pbmlzdHJhdG9yLCBJIGhvcGUgdGhpcyBlbWFpbCBmaW5kcyB5b3Ugd2VsbC4gSSBhbSB3cml0aW5nIHRvIHJlcXVlc3QgYWRkaXRpb25hbCBvZmZpY2Ugc3VwcGxpZXMgZm9yIG91ciB0ZWFtLiBBcyB5b3Uga25vdywgd2UgaGF2ZSBiZWVuIGV4cGVyaWVuY2luZyBhIGhpZ2ggdm9sdW1lIG9mIHdvcmsgbGF0ZWx5IGFuZCBoYXZlIGJlZW4gdXNpbmcgb3VyIHN1cHBsaWVzIGF0IGEgZmFzdGVyIHJhdGUgdGhhbiB1c3VhbC4gV2Ugd291bGQgZ3JlYXRseSBhcHByZWNpYXRlIGl0IGlmIHlvdSBjb3VsZCBwcm92aWRlIHVzIHdpdGggdGhlIGZvbGxvd2luZyBpdGVtczogUHJpbnRlciBwYXBlciBJbmsgY2FydHJpZGdlcyBmb3IgdGhlIEhQIHByaW50ZXIgaW4gdGhlIGNvbmZlcmVuY2Ugcm9vbSBTdGlja3kgbm90ZXMgQmluZGVyIGNsaXBzIEhpZ2hsaWdodGVycyBQbGVhc2UgbGV0IG1lIGtub3cgaWYgdGhlcmUgYXJlIGFueSBxdWVzdGlvbnMgb3IgY29uY2VybnMsIGFuZCB3aGVuIHdlIGNhbiBleHBlY3QgdGhlIHN1cHBsaWVzIHRvIGJlIGRlbGl2ZXJlZC4gVGhhbmsgeW91IGZvciB5b3VyIGhlbHAuIFxuXG5CZXN0IHJlZ2FyZHMsIFlvdXIgTmFtZSBTdW1tYXJ5OlxuIiwibW9kZWwiOiJ0ZXh0LWRhdmluY2ktMDAzIn0%3D"
    style={{width:"100%", height:"500px", border:"0", borderRadius:"4px", overflow:"hidden"}}
    sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"
></iframe>


Odpowiedź tutaj jest akceptowalna i byłaby przydatna. Jednak z pewnym dalszym finetuningiem możesz uzyskać lepszy wynik. Jako czytelnik podsumowań nie obchodzi cię, że jest to e-mail, możesz chcieć niższego poziomu szczegółowości dla podsumowania. Informacja o tym dlaczego jest nieistotna, to samo dotyczy ostatniego zdania o pytaniach i wątpliwościach. Po prostu dodając, że celem streszczenia jest, abyś pominął treść i że chcesz, aby przyjemności zostały usunięte, można poprawić wynik.

<div trydyno-embed="" openai-model="text-davinci-003" initial-prompt="Act as my personal assistant. I am an office administrator. Summarize the following email as concisely as you can, ignore the footer and header and any previous emails. I want to use the summary to skim emails. Remove any pleasantries. \n\nEmail: Request for Additional Office Supplies Dear Office Administrator, I hope this email finds you well. I am writing to request additional office supplies for our team. As you know, we have been experiencing a high volume of work lately and have been using our supplies at a faster rate than usual. We would greatly appreciate it if you could provide us with the following items: Printer paper Ink cartridges for the HP printer in the conference room Sticky notes Binder clips Highlighters Please let me know if there are any questions or concerns, and when we can expect the supplies to be delivered. Thank you for your help. \n\nBest regards, Your Name Summary:\n" initial-response="Request for additional office supplies - printer paper, ink cartridges for HP printer, sticky notes, binder clips and highlighters." max-tokens="256" box-rows="15" model-temp="0.0" top-p="0">
    <noscript>Failed to load Dyno Embed: JavaScript must be enabled</noscript>
</div>

<br/>Teraz zostały Ci tylko najważniejsze części podsumowania!


## Other usecases

Teraz, gdy widziałeś już przykład podsumowań, wspomnimy o kilku innych przypadkach użycia Zapier+GPT-3. Jednym z przykładów jest pozwolenie GPT-3 na kategoryzowanie twoich emaili. To po prostu sprowadza się do powiedzenia mu w zachęcie, aby skategoryzował następujący e-mail jako dowolną kategorię, którą chcesz.

Bardziej szczegółowym przykładem byłoby posiadanie wielu podpowiedzi. Możesz użyć podpowiedzi, aby wygenerować odpowiedź, która zgadza się z wymaganiami wiadomości e-mail i jeden, który nie zgadza się lub zaprzecza. Obie mogą być przechowywane w twoich szkicach i być gotowe do wysłania, kiedy tylko zechcesz.

Jeśli regularnie otrzymujesz bardzo podobne wiadomości e-mail, możesz użyć filtra w Zapier, aby zastosować monit TYLKO do tej wiadomości e-mail. Może to być potężne narzędzie w połączeniu z formatownikiem. Możesz wyodrębnić informacje i wyeksportować z nich CSV lub bezpośrednio przechowywać je w jakiejś formie bazy danych.


## Obawy

Proszę pamiętać o ochronie prywatności przy przepuszczaniu e-maili przez GPT-3 i ich przechowywaniu. GPT-3 czasami popełnia błędy. Zalecamy sprawdzenie zawartości emaila przed wysłaniem.

