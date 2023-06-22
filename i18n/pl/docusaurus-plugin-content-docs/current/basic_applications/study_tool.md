---
sidebar_position: 30
---

# 🟢 Study Buddy

Jednym z naszych ulubionych sposobów wykorzystania LLM jest narzędzie do nauki! W szczególności, jest to przydatne do wyjaśnienia mylących terminów, jak również quizzing cię na treści testu.

## Explaining Terms

Czytałem ostatnio podręcznik o Kaktusach(@nobel2002cacti) i zobaczyłem ten fragment:

`tekst`
Ze względu na przystosowania do warunków kserotermicznych i obecność **bezpośrednich lasów** w Pereskioideae, Cactaceae jest jedną z najciekawszych rodzin zarówno anatomicznie jak i morfologicznie.
```

Nie miałem pojęcia co oznacza **less derived woods**, a Google pokazało tylko artykuły badawcze na ten temat. Postanowiłem użyć ChatGPT, aby dowiedzieć się, co to znaczy. Podałem mu następujący prompt, czyli po prostu fragment książki i moje pytanie.

`tekst`
Ze względu na przystosowania do warunków kserotermicznych i obecność mniej pochodnych lasów w Pereskioideae, Cactaceae jest jedną z najbardziej interesujących rodzin zarówno anatomicznie jak i morfologicznie.

Co oznaczają mniej pochodne lasy?

// highlight-start
W tym kontekście "drewno mniej pochodne" odnosi się do przodka lub prymitywnej formy drewna znalezionej we wczesnej ewolucji roślin. Drewno to nie posiada wyspecjalizowanych struktur i cech, które rozwinęły się później u bardziej pochodnych lub zaawansowanych roślin. W podrodzinie Pereskioideae rodziny Cactaceae, drewno jest mniej pochodne w porównaniu z innymi podrodzinami i jest bardziej podobne do drewna występującego u roślin nie będących kaktusami. Uważa się, że mniej pochodne drewno u Pereskioideae jest adaptacją do bardziej wilgotnych i mniej kserotermicznych środowisk, w których rosną te rośliny w porównaniu z innymi kaktusami.
//highlight-end
```

Modelka szybko odpowiedziała na moje pytanie i mogłem kontynuować lekturę.

# Quizzing Yourself

Innym sposobem wykorzystania LLM jako narzędzia do nauki jest quizowanie siebie. Jeśli masz zbliżający się test z rachunku, możesz po prostu zapytać:

`tekst
Wygeneruj dla mnie 5 pytań do quizu Calculus I:

// highlight-start
1. Co to jest pochodna zależności y = x3?
2. Oszacuj całkę nieokreśloną z x3 + 5x2 + 7x + 4.
3. Jaka jest reguła iloczynu dla pochodnych?
4. Znajdź równanie prostej stycznej do y = x2 w punkcie (4, 16).
5. Jaka jest druga pochodna prostej y = x4?
//highlight-end
```

Jeśli studiujesz bardziej szczegółowy temat, być może będziesz musiał podać modelowi dodatkowe informacje, na przykład swoje notatki z zajęć!

``Tekst
3/20/2020 2:30 PM

Marketing Notatki z zajęć

- Omówione 4 P marketingu: Produkt, Cena, Miejsce, Promocja
- Różnica między B2C a B2B: B2C to rynek bezpośrednich konsumentów, B2B to rynek przedsiębiorstw.
- Różne rodzaje badań rynku: Ilościowe i jakościowe, takie jak ankiety i grupy fokusowe
- Strategie cenowe: Skimming, Penetracja, Konkurencja i Wartość
- Segmentacja: segmentacja bazy klientów według wieku, dochodu, itp.
- 4 rodzaje segmentacji: Demograficzna, Geograficzna, Psychograficzna i Behawioralna.
- Omówienie różnych narzędzi promocyjnych: Reklama, sprzedaż osobista, Public Relations, marketing bezpośredni, promocja sprzedaży

Wygeneruj dla mnie 5 pytań quizu marketingowego na podstawie moich notatek:

// highlight-start
1. Jakie są 4 P marketingu?
2. Jaka jest różnica między B2C a B2B?
3. Jakie są dwa rodzaje badań rynku?
4. Jakie są 4 rodzaje segmentacji?
5. Wymień 5 narzędzi promocyjnych.
//highlight-end
```

## Wniosek

Prawdopodobnie istnieją inne sposoby wykorzystania LLM do nauki. Wiele firm zajmujących się nauką, takich jak Duolingo i Quizlet, wdraża LLM do swoich produktów.

