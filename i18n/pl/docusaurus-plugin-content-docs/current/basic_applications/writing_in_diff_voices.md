---
sidebar_position: 60
---

# 🟢 Różne style pisania

Sztuczne inteligencje takie jak [ChatGPT](https://chat.openai.com/chat) są znane z tworzenia esejów i artykułów na blogi w mgnieniu oka. Ale często artykuły, które produkują są ogólne i suche. Musisz zrobić coś ekstra, aby nadać słowom trochę ducha lub pizzazz.
Jednym z najszybszych sposobów, aby to zrobić jest określenie stylu pisania lub nazwanie znanego autora w podpowiedzi.     
Powiedzmy, że chcesz akapit o znaczeniu przyjaźni.
Ogólna zachęta, taka jak "Napisz mi akapit o znaczeniu przyjaźni", przyniesie ogólną odpowiedź z ChatGPT.  

import friendship from '../assets/basic_applications/Generic_Friendship.png';
import friendship_informal from '../assets/basic_applications/Friendship_Informal.png';
import friendship_mark from '../assets/basic_applications/Friendship_Mark_Twain.png';
import friendship_chris from '../assets/basic_applications/Friendship_Chris_Rock.png';
import friendship_millennial from '../assets/basic_applications/Friendship_Millennial.png';


<div style={{textAlign: 'center'}}>.
  <img src={friendship} style={{width: "750px"}} />
</div>

Blah. To jest takie nijakie.
Wyniki zmieniają się, gdy dodajesz specyfikacje, takie jak "**Proszę pisać w nieformalnym, konwersacyjnym stylu.**". ChatGPT wychodzi z czymś takim:

<div style={{textAlign: 'center'}}>.
  <img src={friendship_informal} style={{width: "750px"}} />
</div>

To trochę lepiej.

A jeśli masz ochotę na odrobinę fantazji, możesz poprosić ChatGPT o napisanie w stylu jednego z wielkich literatów, jak Mark Twain:

<div style={{textAlign: 'center'}}>.
  <img src={friendship_mark} style={{width: "750px"}} />
</div>

Tekst teraz zaczyna śpiewać.
Ale to nie musi być znany autor. Możesz użyć znanych osób, jak Chris Rock.

<div style={{textAlign: 'center'}}>.
  <img src={friendship_chris} style={{width: "750px"}} />
</div>

Albo jak to jest z tymi "millenialsami"?

<div style={{textAlign: 'center'}}>.
  <img src={friendship_millennial} style={{width: "750px"}} />
</div>

# Copy Your Writing Style


A co jeśli chcesz, aby GPT-3 napisał maila lub bloga w **twoim** stylu?

Wystarczy, że pokażemy mu jakieś wcześniejsze treści, które napisałeś. Oto przykład, w którym pokazujemy GPT-3 kilka e-maili, które "Dr Rodriguez" napisał w przeszłości i prosimy go o napisanie nowego e-maila w tym samym stylu do nowego pacjenta, pana Inuez.

<div trydyno-embed="" openai-model="text-davinci-003" initial-prompt="Email #1: Subject - Appointment ConfirmationDrogi Johnie,\NChciałem potwierdzić Twoją wizytę u mnie, Dr. Smith, 1 maja 2023 o 14:30 w HealthFirst Clinic. Proszę przybyć 15 minut wcześniej, aby wypełnić wszelkie niezbędne dokumenty i przynieść listę wszystkich leków, które Pan obecnie przyjmuje. Jeśli musi Pani przełożyć lub odwołać wizytę, prosimy o poinformowanie nas o tym z co najmniej 24-godzinnym wyprzedzeniem. Jeśli ma Pani jakieś pytania lub wątpliwości przed wizytą, prosimy o kontakt z nami. Z wyrazami szacunku, Dr RodriguezEmail #2: Temat - Wyniki badańDroga Jane,\NPiszę, aby poinformować Panią, że przyszły Pani ostatnie wyniki badań krwi. Twój poziom cholesterolu jest w normie, ale poziom witaminy D jest niski. Na podstawie tych wyników zalecam również umówienie się na wizytę kontrolną za 3 miesiące w celu ponownego zbadania poziomu witaminy D. Jeśli masz jakiekolwiek pytania lub wątpliwości, prosimy o kontakt z nami. Dziękuję, doktorze RodriguezEmail #3: Temat - Wizyta kontrolnaDrogi Marku, Chciałam sprawdzić, jak się czujesz po naszej ostatniej wizycie. Jeśli nadal odczuwasz ból pleców lub masz jakieś nowe obawy, proszę daj mi znać, abyśmy mogli je omówić podczas najbliższej wizyty. Następna wizyta jest zaplanowana na 15 czerwca 2023 roku o godzinie 10:00 w City Health Clinic. Proszę dać nam znać, jeśli trzeba przełożyć lub odwołać.\NDoktorze Rodriguez, proszę napisać e-mail w stylu powyższych e-maili do pana Inuez, z pytaniem, czy 5 października 2023 r. można umówić się na badanie:" initial-response="Subject - Checkup Appointment,\NDrogi panie Inuez,\NMam nadzieję, że ta wiadomość jest dla pana dobra. Piszę, żeby zapytać, czy 5 października 2023 roku będzie można umówić się na wizytę kontrolną ze mną, dr Rodriguezem. Podczas wizyty omówimy pańskie problemy zdrowotne i wszelkie zmiany w historii choroby. Proszę przyjść 15 minut wcześniej, aby wypełnić wszelkie niezbędne dokumenty i przynieść listę wszystkich leków, które obecnie przyjmujesz. Jeśli 5 października nie pasuje do Ciebie, proszę daj mi znać i możemy znaleźć inny termin, który będzie dla Ciebie lepszy. Dziękuję, Dr Rodriguez" max-tokens="256" box-rows="18" model-temp="0" top-p="0">
    <noscript>Failed to load Dyno Embed: JavaScript musi być włączony</noscript>.
</div>
 

<br/>Możesz wprowadzić dowolny tekst, który napisałeś w przeszłości (e-maile, raporty, blogi itp.), a GPT-3/ChatGPT zazwyczaj będzie w stanie skopiować twój styl. Im więcej tekstu umieścisz, tym lepiej skopiuje twój styl.

