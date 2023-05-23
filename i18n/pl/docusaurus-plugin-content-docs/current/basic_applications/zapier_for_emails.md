---
sidebar_position: 600
---

# 🟢 Zapier for Emails.

import Basic from "../assets/Zapiermail/Basic.png";
import Diagram from "../assets/Zapiermail/Diagram.png";
import Step1 z "../assets/Zapiermail/Step1.png";
import Step2 z "../assets/Zapiermail/Step2.png";
import Step3 z "../assets/Zapiermail/Step3.png";
import Step4 z "../assets/Zapiermail/Step4.png";
import Zap z "../assets/Zapiermail/Zap.png";

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


<details>.
  <summary> Rozwiń, aby uzyskać bardziej szczegółowy widok kroków w Zapier</summary>.
  <div>.
  Oto, jak ostatecznie będzie wyglądał schemat działania Zapier.
    <div><div style={{textAlign: 'left'}}>
  <img src={Zap} style={{width: "500px"}} />
</div></div>
    <br/>
    <details>.
      <summary>.
        Krok 1: Wyzwalacz Gmaila na nowej przychodzącej wiadomości e-mail (używany jest tutaj Gmail).
      </summary>
      <div>
        <div style={{textAlign: 'left'}}>
    <img src={Step1} style={{width: "500px"}} />
        </div>
      </div>
    </detale>
    <details>
      <summary>
       Krok 2: Formatownik dla treści wiadomości e-mail.
      </summary>
      <div>.
        <div style={{textAlign: 'left'}}>.
  <img src={Krok2} style={{szerokość: "500px"}} />
</div>
      </div>
    </detale>
    <details>
      <summary>
        Krok 3: Prompting treści e-maila
        <br/>
      </summary>
      <div>.
        <div style={{textAlign: 'left'}}>.
  <img src={Krok3} style={{szerokość: "500px"}} />
</div>
      </div>
    </detale>
    <details>
      <summary>
        Krok 4: Dodanie do bazy danych
      </summary>
      <div>.
        <div style={{textAlign: 'left'}}>.
  <img src={Krok4} style={{szerokość: "500px"}} />
</div>
      </div>
    </detale>
  </div>
</details>
Oto konfiguracja w zapier, która pozwala zrobić bardzo podstawowe podsumowanie, jak pokazano na schemacie. Ma swoje ograniczenia, ale wykonuje pracę i może zbudować użyteczną bazę danych.


# Optymalizacja podpowiedzi dla lepszych wyników

Istnieje kilka łatwych sposobów na poprawę wyników. Dodanie kontekstu i podpowiadanie ról może poprawić dane wyjściowe. Jednak temat i treść twoich e-maili może obejmować szeroki zakres tematów. Oznacza to, że ogólne instrukcje zrobią lepszą robotę niż bardzo szczegółowe, które mogą wyrzucić model.

Ze względów praktycznych przydatne jest podanie instrukcji, a następnie powiedzenie GPT-3, kiedy e-mail zaczyna się w zachęcie, dodając po prostu "Email: " i kończąc prompt z ""Summary": ". Pozwala to uniknąć sytuacji, w której GPT-3 odpowiada "Jasne! Mogę to dla ciebie streścić...".

Podpowiadanie ról może być przydatne również w tym przypadku. Poproszenie GPT-3 o pełnienie roli osobistego asystenta pomaga zwiększyć jakość podsumowania.
Jeśli chcesz podsumować emaile z pracy, po prostu dodając rolę, którą pełnisz, dajesz GPT-3 kontekst do pracy. Działa on tak, jakby zakładał pewien poziom wiedzy czytelnika, co pomaga odfiltrować nieistotne części emaila.
Poniżej pokazujemy kilka przykładów z emaili, które może otrzymać administrator biura.

Możesz poprosić go, aby podsumować prosty e-mail w punktach, jednak może to nie być wszystko, że przydatne w zależności od tego, jak chcesz użyć podsumowania. Do szybkiego przeglądania wiadomości e-mail możesz chcieć, aby były one krótkie i zwięzłe. Proste zapytanie o to w zachęcie działa dobrze. Poniżej znajduje się przykład takiej zachęty. Dostosuj go i baw się nim, aby zobaczyć, jak się zmienia.

<div trydyno-embed="" openai-model="text-davinci-003" initial-prompt="Działaj jako mój osobisty asystent. Jestem administratorem biura. Podsumuj następujący e-mail tak zwięźle, jak tylko potrafisz, zignoruj stopkę i nagłówek oraz wszelkie poprzednie e-maile. \NEmail: Prośba o dodatkowe materiały biurowe Drogi administratorze biura, Mam nadzieję, że ten e-mail dobrze Cię zastanie. Piszę, aby poprosić o dodatkowe materiały biurowe dla naszego zespołu. Jak Pani wie, mamy ostatnio dużo pracy i zużywamy nasze materiały szybciej niż zwykle. Bylibyśmy bardzo wdzięczni, gdybyście mogli dostarczyć nam następujące pozycje: Papier do drukarki Wkłady atramentowe do drukarki HP w sali konferencyjnej Karteczki samoprzylepne Spinacze do segregatorów Zakreślacze Proszę dać mi znać, jeśli są jakieś pytania lub wątpliwości, oraz kiedy możemy spodziewać się dostawy materiałów eksploatacyjnych. Dziękuję za pomoc. \Pozdrawiam, Your Name Summary:\N" initial-response="Prośba o dodatkowe materiały biurowe ze względu na duże obciążenie pracą. Lista potrzebnych rzeczy: papier do drukarki, wkłady atramentowe do drukarki HP w sali konferencyjnej, karteczki samoprzylepne, spinacze do segregatorów i zakreślacze. Proszę o informacje na temat dostawy i czy są jakieś pytania lub wątpliwości." max-tokens="256" box-rows="15" model-temp="0.0" top-p="0">
    <noscript>Failed to load Dyno Embed: JavaScript musi być włączony</noscript>.
</div>

Odpowiedź tutaj jest akceptowalna i byłaby przydatna. Jednak z pewnym dalszym finetuningiem możesz uzyskać lepszy wynik. Jako czytelnik podsumowań nie obchodzi cię, że jest to e-mail, możesz chcieć niższego poziomu szczegółowości dla podsumowania. Informacja o tym dlaczego jest nieistotna, to samo dotyczy ostatniego zdania o pytaniach i wątpliwościach. Po prostu dodając, że celem streszczenia jest, abyś pominął treść i że chcesz, aby przyjemności zostały usunięte, można poprawić wynik.

<div trydyno-embed="" openai-model="text-davinci-003" initial-prompt="Działaj jako mój osobisty asystent. Jestem administratorem biura. Podsumuj następujący e-mail tak zwięźle, jak tylko możesz, ignorując stopkę i nagłówek oraz wszelkie poprzednie e-maile. Chcę używać streszczenia do przeglądania emaili. Usuń wszelkie przyjemności. \NEmail: Prośba o dodatkowe materiały biurowe Drogi Administratorze Biura, Mam nadzieję, że ten e-mail znajduje Cię dobrze. Piszę, aby poprosić o dodatkowe materiały biurowe dla naszego zespołu. Jak Pani wie, mamy ostatnio dużo pracy i zużywamy nasze materiały szybciej niż zwykle. Bylibyśmy bardzo wdzięczni, gdybyście mogli dostarczyć nam następujące pozycje: Papier do drukarki Wkłady atramentowe do drukarki HP w sali konferencyjnej Karteczki samoprzylepne Spinacze do segregatorów Zakreślacze Proszę dać mi znać, jeśli są jakieś pytania lub wątpliwości, oraz kiedy możemy spodziewać się dostawy materiałów eksploatacyjnych. Dziękuję za pomoc. \Pozdrawiam, Your Name Summary:\" initial-response="Prośba o dodatkowe materiały biurowe - papier do drukarki, wkłady atramentowe do drukarki HP, karteczki samoprzylepne, spinacze do segregatora i zakreślacze." max-tokens="256" box-rows="15" model-temp="0.0" top-p="0">.
    <noscript>Failed to load Dyno Embed: JavaScript musi być włączony</noscript>.
</div>


<br/>Teraz zostały Ci tylko najważniejsze części podsumowania!


## Other usecases

Teraz, gdy widziałeś już przykład podsumowań, wspomnimy o kilku innych przypadkach użycia Zapier+GPT-3. Jednym z przykładów jest pozwolenie GPT-3 na kategoryzowanie twoich emaili. To po prostu sprowadza się do powiedzenia mu w zachęcie, aby skategoryzował następujący e-mail jako dowolną kategorię, którą chcesz.

Bardziej szczegółowym przykładem byłoby posiadanie wielu podpowiedzi. Możesz użyć podpowiedzi, aby wygenerować odpowiedź, która zgadza się z wymaganiami wiadomości e-mail i jeden, który nie zgadza się lub zaprzecza. Obie mogą być przechowywane w twoich szkicach i być gotowe do wysłania, kiedy tylko zechcesz.

Jeśli regularnie otrzymujesz bardzo podobne wiadomości e-mail, możesz użyć filtra w Zapier, aby zastosować monit TYLKO do tej wiadomości e-mail. Może to być potężne narzędzie w połączeniu z formatownikiem. Możesz wyodrębnić informacje i wyeksportować z nich CSV lub bezpośrednio przechowywać je w jakiejś formie bazy danych.


## Obawy

Proszę pamiętać o ochronie prywatności przy przepuszczaniu e-maili przez GPT-3 i ich przechowywaniu. GPT-3 czasami popełnia błędy. Zalecamy sprawdzenie zawartości emaila przed wysłaniem.

