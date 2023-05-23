---
sidebar_position: 10
---

# 🟢 Writing An Email

Pisanie e-maili może być czasochłonne, zwłaszcza gdy musisz najpierw przeczytać otrzymany e-mail. W tej sekcji omówimy przypadki użycia, począwszy od prostego maila informującego szefa, że jesteś dziś chory, po bardziej złożone wiadomości typu cold lead.

# Basic Sick Day Email

Wyobraź sobie, że budzisz się chory pewnego dnia i nie możesz iść do pracy (lub po prostu nie chcesz 😈). Oto prosty monit, który pisze maila do szefa z informacją, że jesteś chory.

<div trydyno-embed="" openai-model="text-davinci-003" initial-prompt="Moje imię: MarioNazwisko szefa: JanNapisz e-mail do mojego szefa, mówiąc, że będę dziś nieobecny w biurze, ponieważ jestem chory. " initial-response="Subject: Out of Office - Sick" Drogi Johnie,\NPiszę, aby poinformować, że będę dziś nieobecny w biurze z powodu choroby. Przepraszam za wszelkie niedogodności z tym związane. Będę na bieżąco informował o moich postępach i wrócę do biura, jak tylko poczuję się lepiej. Dziękuję za zrozumienie. Z poważaniem, Mario" max-tokens="256" box-rows="8" model-temp="0" top-p="0">
    <noscript>Failed to load Dyno Embed: JavaScript musi być włączony</noscript>.
</div>

Ten e-mail działa, ale jest dość nudny. Doprawmy go trochę!

## Modyfikatory stylu/instrukcje

Bardzo łatwo jest zmodyfikować styl wiadomości e-mail. Na przykład możesz poprosić SI, aby była "humorystyczna" lub poinstruować ją, aby "Dołączyła zabawny powód".

<div trydyno-embed="" openai-model="text-davinci-003" initial-prompt="Moje imię: Mario Imię szefa: John Napisz humorystyczny, ale profesjonalny e-mail do mojego szefa, mówiąc, że będę dziś poza biurem, ponieważ jestem chory. \Bądź zwięzły i zabawny. Dołącz zabawny powód:" initial-response="Drogi Johnie,\NPiszę, aby poinformować Cię, że będę dzisiaj nieobecny w biurze. Wiem, że powinienem pracować, ale nie mogłem oprzeć się syrenie śpiewce lokalnego sklepu z pączkami. Jestem pewien, że rozumiesz. Wrócę do biura jutro i nadrobię ten czas. Dzięki, Mario" max-tokens="256" box-rows="10" model-temp="0.7" top-p="1">
    <noscript>Failed to load Dyno Embed: JavaScript musi być włączony</noscript>.
</div>
<br/>

Oto inny przykład, który jest bardziej poważny/profesjonalny.

<div trydyno-embed="" openai-model="text-davinci-003" initial-prompt="Moje imię: Mario Imię szefa: Jan Napisz **poważny**, profesjonalny e-mail do mojego szefa, w którym napiszę, że nie będzie mnie dzisiaj w biurze, ponieważ jestem chory. \Bądź zwięzły:" initial-response="Subject: Out of Office - Sick ‖Drogi Janie,‖Piszę, aby poinformować, że będę dziś nieobecny w biurze z powodu choroby. Przepraszam za wszelkie niedogodności, jakie to może spowodować. Dziękuję za zrozumienie. Z poważaniem,Mario" max-tokens="256" box-rows="8" model-temp="0" top-p="0">
    <noscript>Failed to load Dyno Embed: JavaScript musi być włączony</noscript>.
</div>
<br/>

# Responding to an Email

Wyobraź sobie, że otrzymujesz od swojego szefa długi e-mail z dużą ilością informacji. Musisz odpowiedzieć na maila, ale nie masz czasu na przeczytanie całości. Możesz podpiąć maila do AI i poprosić ją o `Generowanie podsumowania tego i listy punktów akcji`.

<div trydyno-embed="" openai-model="text-davinci-003" initial-prompt="Drogi Mario,\NMam nadzieję, że dobrze się czujesz. Piszę, aby przekazać Ci kilka aktualizacji dotyczących naszej firmy i poprosić Cię o pomoc w rozwiązaniu problemu z interfejsem użytkownika (UI) oprogramowania, nad którym pracowałeś.\NJak wiesz, nasza firma koncentruje się na zapewnieniu przyjaznego doświadczenia dla naszych klientów i zidentyfikowaliśmy pewne problemy z UI oprogramowania. W szczególności, otrzymaliśmy informacje zwrotne od naszych użytkowników, że mają trudności z dostępem do niektórych funkcji i że interfejs użytkownika nie jest wystarczająco intuicyjny. Potrzebujemy Twojej pomocy, aby rozwiązać te problemy i dokonać ulepszeń interfejsu użytkownika oprogramowania. Może to oznaczać konieczność wprowadzenia zmian w układzie, projekcie lub funkcjonalności interfejsu użytkownika. Wierzymy, że Twoje doświadczenie w tworzeniu oprogramowania oraz znajomość oprogramowania sprawią, że będziesz idealną osobą, która pomoże nam w tym zadaniu. Jeśli potrzebujesz dodatkowych zasobów lub wsparcia, aby wykonać to zadanie, nie wahaj się dać mi znać. Dodatkowo, byłbym wdzięczny, gdybyś mógł podać mi szacunkowy czas, w którym spodziewasz się, że te modyfikacje zostaną ukończone. Jeśli masz jakieś pytania lub potrzebujesz dalszych wyjaśnień, proszę nie wahaj się ze mną skontaktować. Z niecierpliwością czekam na wiadomość zwrotną od Ciebie wkrótce.\NPozdrawiam,\NGeneruj podsumowanie i listę działań." initial-response="Summary: John is asking Mario's assistance in addressing user interface issues with the software Mario has been working on. Problemy dotyczą trudności z dostępem do niektórych funkcji oraz tego, że interfejs użytkownika nie jest wystarczająco intuicyjny. Ekspertyza Mario w zakresie rozwoju oprogramowania oraz jego znajomość czynią go idealną osobą do pomocy w tym zadaniu. Punkty akcji:\N- Dokonaj zmian w układzie, projekcie lub funkcjonalności interfejsu użytkownika \- Poproś o dodatkowe zasoby lub wsparcie, jeśli to konieczne \- Przedstaw szacowany czas ukończenia modyfikacji" max-tokens="256" box-rows="18" model-temp="0" top-p="0">
    <noscript>Failed to load Dyno Embed: JavaScript musi być włączony</noscript>.
</div>

<br/>Wtedy możesz użyć tego podsumowania do napisania maila z odpowiedzią.

<div trydyno-embed="" openai-model="text-davinci-003" initial-prompt="Streszczenie: John prosi Mario o pomoc w rozwiązaniu problemów z interfejsem użytkownika oprogramowania, nad którym pracował Mario. Problemy dotyczą trudności w dostępie do niektórych funkcji oraz tego, że interfejs użytkownika nie jest wystarczająco intuicyjny. Ekspertyza Mario w zakresie rozwoju oprogramowania oraz jego znajomość sprawiają, że jest on idealną osobą do pomocy w tym zadaniu.\NPunkty działania:\N- Dokonanie zmian w układzie, projekcie lub funkcjonalności interfejsu użytkownika?\NPoproszenie o dodatkowe zasoby lub wsparcie, jeśli jest to konieczne?\NPrzedstawienie szacunkowego czasu zakończenia modyfikacji.\NNNPisz e-mail z odpowiedzią od Mario, używając powyższego streszczenia e-maila:" initial-response="Drogi Janie,\NDziękuję za skontaktowanie się ze mną w sprawie problemów z interfejsem użytkownika w oprogramowaniu, nad którym pracowałem. Rozumiem znaczenie upewnienia się, że interfejs użytkownika jest intuicyjny i łatwy w użyciu, i cieszę się, że mogę pomóc. Zacznę wprowadzać zmiany w układzie, projekcie i funkcjonalności interfejsu użytkownika, aby rozwiązać problemy, o których wspomniałeś. Jeśli będę potrzebował dodatkowych zasobów lub wsparcia, dam Ci znać. Przedstawię również szacowany czas ukończenia modyfikacji. Proszę dać mi znać, jeśli masz jakiekolwiek pytania lub wątpliwości. Z poważaniem, Mario" max-tokens="256" box-rows="18" model-temp="0" top-p="0">
    <noscript>Failed to load Dyno Embed: JavaScript musi być włączony</noscript>.
</div>

<br/>Zauważ, że często można połączyć te dwa kroki w jeden. Możesz poprosić SI o wygenerowanie maila z odpowiedzią bezpośrednio z otrzymanego maila.

# Cold Emails

Zimne e-maile to e-maile wysyłane do osób, których nie znasz. Trudno jest uzyskać odpowiedź z zimnych e-maili, więc pomocne może być wysłanie wielu osobiście spersonalizowanych e-maili. Zobaczmy jak to zrobić z GPT-3(@bonta2022how).

<div trydyno-embed="" openai-model="text-davinci-003" initial-prompt="Nazwa firmy: Bark Inc Moje imię: Mike Napisać zimny e-mail z prośbą o pomoc" initial-response="Drogi Johnie,\NPiszę, aby poinformować Cię, że będę dzisiaj poza biurem. Wiem, że powinienem pracować, ale nie mogłem oprzeć się syrenie śpiewce lokalnego sklepu z pączkami. Jestem pewien, że rozumiesz. Wrócę do biura jutro i nadrobię ten czas. Dzięki, Zach" max-tokens="256" box-rows="10" model-temp="0" top-p="0">
    <noscript>Failed to load Dyno Embed: JavaScript musi być włączony</noscript>.
</div>

Jest to zgrabne, ale możemy zrobić to lepiej. Dodajmy trochę więcej informacji do podpowiedzi.

### Korzystanie z informacji nieustrukturyzowanych

Powiedzmy, że masz profil linkedin osoby, do której wysyłasz wiadomość e-mail. Możesz dodać te informacje do podpowiedzi, aby uczynić e-mail bardziej spersonalizowanym. Użyjmy [założyciela Strive'a na LinkedIn](https://www.linkedin.com/in/snpranav/) jako przykładu. Skopiujemy garść informacji z jego profilu i dodamy je do zachęty.

<div trydyno-embed="" openai-model="text-davinci-003" initial-prompt="Pranav Shikarpur 1st degree connection1stDeveloper Advocate. Problem Solver. Poprzednio: Współzałożyciel Strive, Intel ISEF Alum 
DoświadczenieDoświadczenie logo Thales Cloud Security 
Developer AdvocateDeveloper Advocate 
Thales Cloud SecurityThales Cloud Security 
Kwiecień 2022 - Obecny - 1 rokKwiecień 2022 - Obecny - 1 rok 
- Realizował go-to-market i zwiększał zaangażowanie deweloperów dla premiery nowego produktu Thales z zakresu szyfrowania danych.\Kierował przyjęciem produktu przez deweloperów na konferencjach RSA 2022 i KubeCon 2022. Przedstawił wykład na corocznej konferencji HashiCorp - HashiConf 2022 w Los Angeles - na temat "Securing Any Data Source". - Kierował przyjęciem produktu przez deweloperów na konferencji RSA 2022 i KubeCon 2022. - Przedstawił wykład na corocznej konferencji HashiCorp - HashiConf 2022 w Los Angeles - na temat "Securing Any Data Source" .... Zobacz więcej Umiejętności: Data Encryption Standard (DES) - Kryptografia - Cybersecurity - Tworzenie treści - Azure Kubernetes Service (AKS) - Google Kubernetes Engine (GKE)Umiejętności: Data Encryption Standard (DES) - Kryptografia - Cybersecurity - Tworzenie treści - Azure Kubernetes Service (AKS) - Google Kubernetes Engine (GKE)LogoStartup ShellDyrektor ds. Zasobów ZałożycielskichDyrektor ds. Zasobów ZałożycielskichListopad 2022 - obecny - 1 rok 2 mosListopad 2022 - obecny - 1 rok 2 mosCollege Park, Maryland, Stany ZjednoczoneCollege Park, Maryland, Stany Zjednoczone 
- Zamknięte partnerstwa zasobów założycielskich z różnymi firmami technologicznymi, takimi jak Vercel, MongoDB, itp.\Pozyskanie ponad $50,000 kredytów i zasobów dla założycieli w Startup Shell w ciągu 3 miesięcy. Zamknięte partnerstwa zasobów założycieli z różnymi firmami technologicznymi, takimi jak Vercel, MongoDB, itp. - Pozyskanie ponad $50,000 kredytów i zasobów dla założycieli w Startup Shell w ciągu 3 miesięcy.\NUmiejętności: Partnerstwa strategiczneUmiejętności: Strategic Partnerships LogoStrive NetworkCo-FounderCo-FounderCo-FounderCo-FounderCo-FounderCo-FounderCo-FounderCo-FounderCo-FounderCo-FriveStrive Założona pierwsza w Indiach kohortowa platforma edukacyjna dla kursów związanych z pasją. Zbudował platformę edukacyjną od podstaw i zarządzał ruchem na stronie internetowej w skali i nadzorował sprzedaż i marketing. Negocjował z 100X.VC i People Group, aby zebrać $50K seed funding dla Strive.- Założył pierwszą w Indiach platformę edukacyjną opartą na kohortach dla kursów związanych z pasją. Miała ponad 7 tysięcy aktywnych użytkowników miesięcznie. - Zbudował platformę edukacyjną od podstaw i zarządzał ruchem na stronie internetowej w skali i nadzorował sprzedaż i marketing. - Negocjował z 100X.VC i People Group, aby zebrać $50K seed funding dla Strive.... zobacz więcej Umiejętności: Go (język programowania) - Python (język programowania) - Product Management - Product Marketing - Next.js - Amazon EKSZajęcia i stowarzyszenia: Director of Founder Resources at Startup ShellAktualności i stowarzyszenia: Director of Founder Resources at Startup ShellZgłębiając piękno matematyki z praktycznością informatyki, napisz zimny e-mail do tego założyciela, pitchując mu nasz produkt, Nightfall, który jest neo-CRM. Mam na imię Max. Napisz wiadomość formalną, ale przystępną. Wspomnij o istotnych szczegółach z jego informacji na LinkedIn, aby pomóc w prezentacji produktu.Pranav Shikarpur Połączenie 1. stopnia1. Problem Solver. Poprzednio: Współzałożyciel Strive, Intel ISEF Alum - logoThales Cloud SecurityDeveloper AdvocateDeveloper AdvocateThales Cloud SecurityThales Cloud SecurityKwiecień 2022 - teraźniejszość - 1 rokKwiecień 2022 - teraźniejszość - 1 rokWykonał go-to-market i zwiększył zaangażowanie deweloperów dla premiery nowego produktu Thales z zakresu szyfrowania danych.\Kierował przyjęciem produktu przez deweloperów na konferencjach RSA 2022 i KubeCon 2022. Przedstawił wykład na corocznej konferencji HashiCorp - HashiConf 2022 w Los Angeles - na temat "Securing Any Data Source". - Kierował przyjęciem produktu przez deweloperów na konferencji RSA 2022 i KubeCon 2022. - Przedstawił wykład na corocznej konferencji HashiCorp - HashiConf 2022 w Los Angeles - na temat "Securing Any Data Source" .... Zobacz więcej Umiejętności: Data Encryption Standard (DES) - Kryptografia - Cybersecurity - Tworzenie treści - Azure Kubernetes Service (AKS) - Google Kubernetes Engine (GKE)Umiejętności: Data Encryption Standard (DES) - Kryptografia - Cybersecurity - Tworzenie treści - Azure Kubernetes Service (AKS) - Google Kubernetes Engine (GKE)LogoStartup ShellDyrektor ds. Zasobów ZałożycielskichDyrektor ds. Zasobów ZałożycielskichListopad 2022 - obecny - 1 rok 2 mosListopad 2022 - obecny - 1 rok 2 mosCollege Park, Maryland, Stany ZjednoczoneCollege Park, Maryland, Stany Zjednoczone 
- Zamknięte partnerstwa zasobów założycielskich z różnymi firmami technologicznymi, takimi jak Vercel, MongoDB, itp.\Pozyskanie ponad $50,000 kredytów i zasobów dla założycieli w Startup Shell w ciągu 3 miesięcy. Zamknięte partnerstwa zasobów założycieli z różnymi firmami technologicznymi, takimi jak Vercel, MongoDB, itp. - Pozyskanie ponad $50,000 kredytów i zasobów dla założycieli w Startup Shell w ciągu 3 miesięcy.\NUmiejętności: Partnerstwa strategiczneUmiejętności: Strategic Partnerships LogoStrive NetworkCo-FounderCo-FounderCo-FounderCo-FounderCo-FounderCo-FounderCo-FounderCo-FounderCo-FounderCo-FriveStrive Założona pierwsza w Indiach kohortowa platforma edukacyjna dla kursów związanych z pasją. Zbudował platformę edukacyjną od podstaw i zarządzał ruchem na stronie internetowej w skali i nadzorował sprzedaż i marketing. Negocjował z 100X.VC i People Group, aby zebrać $50K seed funding dla Strive.- Założył pierwszą w Indiach platformę edukacyjną opartą na kohortach dla kursów związanych z pasją. Miała ponad 7 tysięcy aktywnych użytkowników miesięcznie. - Zbudował platformę edukacyjną od podstaw i zarządzał ruchem na stronie internetowej w skali i nadzorował sprzedaż i marketing. - Negocjował z 100X.VC i People Group, aby zebrać $50K seed funding dla Strive.... zobacz więcej Umiejętności: Go (język programowania) - Python (język programowania) - Product Management - Product Marketing - Next.js - Amazon EKSZajęcia i stowarzyszenia: Director of Founder Resources at Startup ShellAktualności i stowarzyszenia: Director of Founder Resources at Startup ShellZgłębiając piękno matematyki z praktycznością informatyki, napisz zimny e-mail do tego założyciela, pitchując mu nasz produkt, Nightfall, który jest neo-CRM. Mam na imię Max. Napisz wiadomość formalną, ale przystępną. Wspomnij o istotnych szczegółach z jego powyższych informacji na LinkedIn, aby pomóc w zaprezentowaniu produktu." initial-response="Drogi Pranavie, Nazywam się Max i zwracam się do Ciebie, ponieważ uważam, że nasz produkt, Nightfall, może być dla Ciebie świetnym rozwiązaniem. Jako współzałożyciel Strive i dyrektor ds. zasobów założycielskich w Startup Shell, jestem pewien, że rozumiesz, jak ważne jest posiadanie niezawodnego CRM, który pomaga zarządzać relacjami z klientami. Nasz produkt został zaprojektowany tak, aby był przyjazny dla użytkownika i intuicyjny, dzięki czemu można skupić się na rozwoju firmy, nie martwiąc się o szczegóły techniczne.Myślę, że znajdziesz Nightfall być wielkim atutem dla swojej firmy. Jeśli jesteś zainteresowany, chętnie umówię się na rozmowę, aby omówić więcej.\" max-tokens="256" box-rows="39" model-temp="0" top-p="0">
    <noscript>Failed to load Dyno Embed: JavaScript musi być włączony</noscript>.
</div>

Super przydatne jest to, że LLM może przeciąć bałagan wszystkich informacji, które skopiowaliśmy z LinkedIn. Ten proces zimnego zasięgu może być również zautomatyzowany na większą skalę poprzez skrobanie LinkedIn dla odpowiednich informacji.


## Wniosek

LLM mogą pomóc Ci w pisaniu maili! Upewnij się, że czytasz to, co piszą przed wysłaniem 😉

## Więcej

- [Zapier](https://zapier.com/blog/use-openai-gpt-3-to-write-emails/)

