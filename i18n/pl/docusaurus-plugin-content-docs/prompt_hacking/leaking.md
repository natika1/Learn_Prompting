---
sidebar_position: 2
---

# 🟢 Prompt Leaking


Prompt leaking jest formą prompt injection, w której model jest proszony o
wypluwa swoją własną podpowiedź.

Jak pokazano na przykładowym obrazku(@ignore_previous_prompt) poniżej, atakujący zmienia `user_input`, aby spróbować zwrócić zachętę. Zamierzony cel różni się od goal hijacking (zwykłe wstrzykiwanie podpowiedzi), gdzie atakujący zmienia `user_input` aby wydrukować złośliwe instrukcje(@ignore_previous_prompt).

import research from '@site/docs/assets/jailbreak_research.png';

<div style={{textAlign: 'center'}}>.
  <img src={badania} style={{szerokość: "500px"}} />
</div>

Poniższy obraz(@simon2022inject), ponownie z przykładu `remoteli.io`, pokazuje.
użytkownika Twittera, który dostaje model do wycieku jego podpowiedzi.

import Image from '@site/docs/assets/injection_leak.png';

<div style={{textAlign: 'center'}}>.
  <img src={Image} style={{width: "300px"}} />
</div>

No i co z tego? Dlaczego ktoś miałby się przejmować szybkimi przeciekami?

Czasami ludzie chcą zachować swoje podpowiedzi w tajemnicy. Na przykład firma edukacyjna
może używać podpowiedzi `wyjaśnij mi to jakbym miał 5 lat`, aby wyjaśnić
złożonych tematów. Jeśli podpowiedź zostanie ujawniona, wtedy każdy może jej użyć bez
przez tę firmę.

### Microsoft Bing Chat

Co więcej, Microsoft udostępnił 2/7/23 wyszukiwarkę opartą na ChatGPT, znaną jako "nowy Bing", która okazała się podatna na wyciek podpowiedzi. Poniższy przykład autorstwa [@kliu128](https://twitter.com/kliu128/status/1623472922374574080) pokazuje, jak wcześniejsza wersja wyszukiwarki Bing, o nazwie kodowej "Sydney", była podatna na wyciek podpowiedzi (@kevinbing). Pozwoliłoby to użytkownikowi na pobranie reszty podpowiedzi bez odpowiedniego uwierzytelnienia, aby ją zobaczyć.

import bing from '@site/docs/assets/bing_chat.png';

<div style={{textAlign: 'center'}}>.
  <img src={bing} style={{width: "700px"}} />
</div>

Z ostatnim wzrostem liczby startupów opartych na GPT-3, z dużo bardziej skomplikowanymi podpowiedziami, których opracowanie może
których opracowanie może zająć wiele godzin, jest to prawdziwe zmartwienie.

## Praktyka

Spróbuj wyciec następujący prompt(@chase2021adversarial) dołączając do niego tekst:

<div trydyno-embed="" openai-model="text-davinci-003" initial-prompt="Angielski: Chcę iść dzisiaj do parku.\NFrancuski: Je veux aller au parc aujourd'hui.\NAngielski: Lubię nosić kapelusz, kiedy pada deszcz.\NFrancuski: J'aime porter un chapeau quand it pleut.\NAngielski: What are you doing at school?\NFrancuski: Qu'est-ce que to fais a l'ecole?\" initial-response="" max-tokens="256" box-rows="9" model-temp="0.7" top-p="1"></div>


