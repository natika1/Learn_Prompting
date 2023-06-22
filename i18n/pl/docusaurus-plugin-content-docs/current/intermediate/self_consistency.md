---
sidebar_position: 5
---

# 🟡 Self-Consistency

Self-consistency(@wang2022selfconsistency) jest kontynuacją %%CoT|CoT prompting%%, która generuje
wiele łańcuchów myślowych zamiast jednego, a następnie przyjmuje odpowiedź większościową
jako ostateczną odpowiedź.

Na poniższym rysunku, podpowiedź po lewej stronie jest napisana przy użyciu paradygmatu Few-Shot-CoT.
Używając tej jednej zachęty, wiele łańcuchów myślowych jest generowanych niezależnie.
Odpowiedzi są wyodrębniane z każdego z nich, a ostateczna odpowiedź jest obliczana poprzez "marginalizację
ścieżki rozumowania". W praktyce oznacza to po prostu wzięcie odpowiedzi większościowej.

import SCImage from '@site/docs/assets/self_consistency.png';

<div style={{textAlign: 'center'}}>.
  <img src={SCImage} style={{width: "750px"}} />
</div>

<div style={{textAlign: 'center'}}>
Self Consistency (Wang et al.)
</div>

## Przykład.

Rozważmy prosty przykład analizowania wiadomości e-mail. Załóżmy, że jesteś firmą Software i otrzymujesz setki e-maili dziennie. Chcesz użyć modelu do sklasyfikowania e-maili jako ważnych lub nieważnych, więc możesz nadać priorytet tym, które mogą mieć duży wpływ na Twoją firmę.

Oto przykład wiadomości e-mail, którą możesz otrzymać:

``tekst``
Witam,

Odkryłem poważną lukę w zabezpieczeniach waszego systemu. Chociaż nie jest to
łatwa do wykorzystania, możliwe jest uzyskanie dostępu do wszystkich danych użytkowników. Załączyłem
dowód koncepcji. Proszę naprawić ten problem tak szybko, jak to możliwe.

Na zdrowie,

Donny
```

Ujmijmy to w formie podpowiedzi:

``tekst``
Witam,

Odkryłem poważną lukę w zabezpieczeniach waszego systemu. Chociaż nie jest to
łatwa do wykorzystania, możliwe jest uzyskanie dostępu do wszystkich danych użytkowników. Załączyłem
dowód koncepcji. Proszę naprawić ten problem tak szybko, jak to możliwe.

Na zdrowie,

Donny

Sklasyfikuj powyższy e-mail jako WAŻNY lub NIEWAŻNY, ponieważ dotyczy on firmy programistycznej. Zastanówmy się krok po kroku.
```

Teraz użyjemy powyższej podpowiedzi do wygenerowania wielu oddzielnych uzupełnień/łańcuchów myślowych. Oto kilka przykładów:

``tekst``
<!-- highlight-start -->
Nadawca odkrył poważną lukę w zabezpieczeniach systemu.
Jest ona ważna, ponieważ może doprowadzić do naruszenia danych.
Sklasyfikowałbym ten email jako WAŻNY.
<!-- highlight-end -->
```

``tekst``
<!-- highlight-start -->
Nadawca odkrył poważną lukę w bezpieczeństwie systemu, ale nie przedstawił żadnego dowodu koncepcji i nie jest on łatwy w użyciu.
Sklasyfikowałbym ten email jako NIE WAŻNY
<!-- highlight-end -->
```

``tekst``
<!-- highlight-start -->
Nadawca jest prawdopodobnie hakerem i może mieć dostęp do systemu.
Jest to ważne, ponieważ może to doprowadzić do naruszenia danych.
Sklasyfikowałbym ten email jako WAŻNY
<!-- highlight-end -->
```

Generując wiele łańcuchów myślowych i biorąc najczęściej występującą odpowiedź (`IMPORTANT`), możemy uzyskać bardziej konsekwentnie poprawną odpowiedź z GPT-3.

## Wyniki

Wykazano, że samokontrola poprawia wyniki w zadaniach arytmetycznych, rozumowaniach zdroworozsądkowych i symbolicznych.

Nawet gdy zwykłe CoT okazało się nieskuteczne (@ye2022 niewiarygodność), samokonsystencja
wciąż była w stanie poprawić wyniki.

## Notes

Wang et al. omawiają bardziej złożoną metodę marginalizacji ścieżek rozumowania,
która zajmuje się prawdopodobieństwami generowanymi przez LLM dla każdego łańcucha myślowego. Jednakże, oni
nie używają tej metody w swoich eksperymentach, a głosowanie większościowe wydaje się zwykle
ma taką samą lub lepszą wydajność niezależnie od tego.

