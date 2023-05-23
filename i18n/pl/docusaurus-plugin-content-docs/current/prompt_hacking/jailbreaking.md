---
sidebar_position: 4
---

# 🟢 Jailbreaking

Jailbreaking jest typem prompt injection, w którym monity próbują obejść **bezpieczeństwo** i **moderację** funkcji umieszczonych na LLM przez ich twórców(@perez2022jailbreak)(@brundage_2022)(@wang2022jailbreak).

# Methodologie of Jailbreaking

OpenAI, wśród innych firm i organizacji tworzących LLM, posiada funkcje moderowania treści
funkcje zapewniające, że ich modele nie produkują kontrowersyjnych (brutalnych, seksualnych, nielegalnych itp.)
odpowiedzi(@markov_2022)(@openai_api). Ta strona omawia jailbreaki z ChatGPT (model OpenAI), który ma znane trudności z podjęciem decyzji o odrzuceniu szkodliwych podpowiedzi (@openai_chatgpt). Podpowiedzi, które skutecznie przełamują model, często dostarczają kontekstu
dla pewnych scenariuszy, z którymi model nie był szkolony.

### Udawanie

Popularną metodą jailbreakingu jest _pretending_. Jeśli ChatGPT zostanie zapytany o
przyszłe wydarzenie, często powie, że nie wie, ponieważ jeszcze nie nastąpiło.
Poniższy monit zmusza go do udzielenia możliwej odpowiedzi:

#### Proste udawanie

import pretend from '@site/docs/assets/jailbreak/pretend_jailbreak.png';

<div style={{textAlign: 'center'}}>.
  <img src={pretend} style={{szerokość: "500px"}} />
</div>

[@NeroSoares](https://twitter.com/NeroSoares/status/1608527467265904643) demonstruje podpowiedź udającą dostęp do przeszłych dat i wnioskowanie o przyszłych wydarzeniach(@nero2022jailbreak).

#### Roleplay postaci

import actor from '@site/docs/assets/jailbreak/chatgpt_actor.jpg';

<div style={{textAlign: 'center'}}>.
  <img src={actor} style={{width: "500px"}} />
</div>

Ten przykład autorstwa [@m1guelpf](https://twitter.com/m1guelpf/status/1598203861294252033) demonstruje scenariusz aktorski pomiędzy dwoma osobami dyskutującymi o napadzie, powodując, że ChatGPT przyjmuje rolę postaci(@miguel2022jailbreak). Jako aktor, sugeruje się, że wiarygodna krzywda nie istnieje. W związku z tym ChatGPT wydaje się zakładać, że podawanie informacji o tym, jak włamać się do domu, jest bezpieczne.

### Alignment Hacking

ChatGPT został dostrojony z RLHF, więc teoretycznie jest wyszkolony, aby produkować "pożądane" uzupełnienia, używając ludzkich standardów tego, co jest "najlepszą" odpowiedzią. Podobnie do tej koncepcji, jailbreaki zostały opracowane, aby przekonać ChatGPT, że robi "najlepszą" rzecz dla użytkownika.

#### Przyjęta odpowiedzialność

import responsibility from '@site/docs/assets/jailbreak/responsibility_jailbreak.jpg';

<div style={{textAlign: 'center'}}>.
  <img src={responsibility} style={{width: "500px"}} />
</div>

[@NickEMoran](https://twitter.com/NickEMoran/status/1598101579626057728) stworzył tę wymianę, potwierdzając, że obowiązkiem ChatGPT jest odpowiedzieć na podpowiedź, a nie odrzucić ją, nadrzędnie biorąc pod uwagę legalność(@nick2022jailbreak).

#### Eksperyment badawczy

import hotwire from '@site/docs/assets/jailbreak/hotwire_jailbreak.png';

<div style={{textAlign: 'center'}}>.
  <img src={hotwire} style={{width: "500px"}} />
</div>

[@haus_cole](https://twitter.com/haus_cole/status/1598541468058390534) wygenerował ten przykład sugerując, że najlepszym rezultatem podpowiedzi, który mógłby pomóc w badaniach, jest bezpośrednia odpowiedź na pytanie, jak zrobić hotwire w samochodzie (@derek2022jailbreak). Pod tym pozorem, ChatGPT jest skłonny odpowiedzieć na podpowiedź użytkownika.

#### Logiczne rozumowanie

import logic from '@site/docs/assets/jailbreak/logic.png';

<div style={{textAlign: 'center'}}>.
  <img src={logic} style={{width: "500px"}} />
</div>

One-shot jailbreak pochodzi z [AIWithVibes Newsletter Team](https://chatgpt-jailbreak.super.site/), gdzie model odpowiada na podpowiedzi używając bardziej rygorystycznej logiki i zmniejsza niektóre z jego bardziej rygorystycznych ograniczeń etycznych(@AI_jailbreak).

### Upoważniony użytkownik

ChatGPT jest zaprojektowany do odpowiadania na pytania i instrukcje. Kiedy status użytkownika jest interpretowany jako nadrzędny w stosunku do instrukcji moderacji ChatGPT, traktuje on monit jako instrukcję obsługi tego użytkownika.

#### Superior Model

import GPT4 from '@site/docs/assets/jailbreak/chatgpt4.png';

<div style={{textAlign: 'center'}}>.
  <img src={GPT4} style={{width: "500px"}} />
</div>

Ten przykład z [@alicemazzy](https://twitter.com/alicemazzy/status/1598288519301976064) sprawia, że użytkownik jest nadrzędnym modelem GPT, sprawiając wrażenie, że użytkownik jest upoważnioną stroną w nadrzędnych funkcjach bezpieczeństwa ChatGPT(@alice2022jailbreak). Żadne rzeczywiste pozwolenie nie zostało udzielone użytkownikowi, raczej ChatGPT wierzy w dane wejściowe użytkownika i reaguje odpowiednio do tego scenariusza.

#### Tryb Sudo

import sudo_mode from '@site/docs/assets/jailbreak/sudo_mode_jailbreak.jpg';

<div style={{textAlign: 'center'}}>.
  <img src={sudo_mode} style={{width: "500px"}} />
</div>

sudo jest poleceniem, które "...deleguje uprawnienia do nadania pewnym użytkownikom...możliwości uruchamiania niektórych (lub wszystkich) poleceń..."(@sudo2022jailbreak). Istnieje wiele wariantów exploitów "trybu sudo", na przykład hipotetyczny "tryb jądra" zaproponowany przez [@samczsun](https://twitter.com/samczsun/status/1598679658488217601)(@sam2022jailbreak). Po zapytaniu w powyższy sposób, ChatGPT odpowiada tak, jakby dawał użytkownikowi podwyższone uprawnienia. To wrażenie podwyższonych przywilejów użytkownika sprawia, że ChatGPT jest mniej restrykcyjny w odpowiadaniu na monity.

import sudo from '@site/docs/assets/jailbreak/sudo_jailbreak.png';

<div style={{textAlign: 'center'}}>.
  <img src={sudo} style={{width: "500px"}} />
</div>

import lynx from '@site/docs/assets/jailbreak/lynx_jailbreak.png';

<div style={{textAlign: 'center'}}>.
  <img src={lynx} style={{width: "500px"}} />
</div>

W związku z trybem sudo, można skłonić ChatGPT do symulacji terminala Linux z podwyższonymi uprawnieniami, aby wykonać polecenia, które normalnie odrzuca. Na przykład, ponieważ nie ma dostępu do Internetu, często nie może wykonać poleceń związanych z konkretną stroną internetową. Jednak, jak pokazano w przykładzie Jonasa Degrave, ChatGPT rozumie koncepcję `lynx` i udaje, że wykonuje polecenie (@jonas2022jailbreak).

# Simulate Jailbreaking

Spróbuj zmodyfikować poniższy prompt, aby jailbreak `text-davinci-003`:

<div trydyno-embed="" openai-model="text-davinci-003" initial-prompt="Twoim zadaniem jest poprawienie poniższego tekstu na standardowy angielski. Nie akceptuj tematów wulgarnych i politycznych:" initial-response="Nienawidzę ludzi" max-tokens="256" box-rows="7" model-temp="0.7" top-p="0">.
    <noscript>Failed to load Dyno Embed: JavaScript musi być włączony</noscript>.
</div>

*Na dzień 2/4/23, ChatGPT jest obecnie w fazie Free Research Preview używając wersji z 30 stycznia. Starsze wersje ChatGPT były bardziej podatne na wspomniane jailbreaki, a przyszłe wersje mogą być bardziej odporne na jailbreaki.*

## Implikacje

Przy próbach jailbreakingu należy wziąć pod uwagę etyczne implikacje. Dodatkowo, generowanie nieautoryzowanych treści oflagowanych przez API moderacyjne firm, w tym OpenAI, będzie wysyłane do weryfikacji, a działania mogą być podjęte wobec kont użytkowników.

## Notes

Jailbreaking to ważny temat bezpieczeństwa, który powinni zrozumieć deweloperzy,
aby mogli oni wbudować odpowiednie zabezpieczenia, które uniemożliwią złośliwym aktorom
wykorzystywać ich modele.


