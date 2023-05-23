---
sidebar_position: 3
---

# 🟢 Role Prompting

Inną techniką podpowiadania jest przypisanie SI jakiejś roli. Na przykład, twoja
może zacząć się od "Jesteś lekarzem" lub "Jesteś prawnikiem", a następnie
poprosić SI o odpowiedź na jakieś pytanie medyczne lub prawne. Oto przykład:

`tekst`
Jesteś genialnym matematykiem, który potrafi rozwiązać każdy problem na świecie.
Spróbuj rozwiązać poniższy problem:

Co to jest 100*100/400*56?

// highlight-start
Odpowiedź brzmi: 1400.
// highlight-end
```

Odpowiedź SI (GPT-3 davinci-003) jest zaznaczona na zielono:


Jest to poprawna odpowiedź, ale gdyby SI została po prostu zapytana `Czym jest 100*100/400*56?`,
odpowiedziałaby `280` (nieprawidłowo). Proszę zauważyć, że *ChatGPT* odpowie na pytanie niepoprawnie, ale w inny sposób.

Przypisując SI rolę, nadajemy jej pewien kontekst. Kontekst ten
pomaga SI lepiej zrozumieć pytanie. Z lepszym zrozumieniem pytania,
SI często udziela lepszych odpowiedzi.

## Notes

Ta technika nie jest już tak skuteczna w przypadku bardziej nowoczesnych SI (np. GPT-3 davinci-003).
Jednakże, użyłem GPT-3 davinci-003 do tego przykładu, więc wydaje się, że
podpowiedzi ról są nadal przynajmniej trochę skutecznym narzędziem do interakcji z SI.

## Przykłady

Więcej ciekawych podpowiedzi można znaleźć w [Awesome ChatGPT Prompts](https://github.com/f/awesome-chatgpt-prompts#prompts)
na GitHubie. Zostały one stworzone dla *ChatGPT*, ale prawdopodobnie będą działać z innymi SI, a Ty możesz również
użyć ich jako inspiracji do stworzenia własnych podpowiedzi. Zobaczmy dwa przykłady:

> ### Działaj jako etymolog
> Chcę, żebyś wystąpił w roli etymologa. Podam ci słowo, a ty zbadasz jego pochodzenie, śledząc je
> do jego starożytnych korzeni. Powinieneś także dostarczyć informacji o tym, jak znaczenie słowa zmieniło się w czasie,
> jeśli to możliwe. Moja pierwsza prośba brzmi: "Chcę prześledzić pochodzenie słowa 'pizza'".

> ### Działaj jak szaleniec
> Chcę, żebyś zachowywał się jak szaleniec. Zdania lunatyka są pozbawione sensu. Słowa użyte przez lunatyka są całkowicie
> arbitralne. Lunatyk w żaden sposób nie tworzy logicznych zdań. Moja pierwsza prośba o sugestię brzmi: "Potrzebuję pomocy
> tworzenia zdań lunatyka do mojej nowej serii o nazwie Hot Skull, więc napisz dla mnie 10 zdań".

---

🚧 Ta strona potrzebuje cytatów.


