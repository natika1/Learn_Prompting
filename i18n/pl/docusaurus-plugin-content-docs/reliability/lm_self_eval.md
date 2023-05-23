---
sidebar_position: 7
---

# 🟡 LLM Self Evaluation

# Basic self eval

LLM mogą być używane do sprawdzania wyników własnych lub innych wyjść LLM. To
może być tak proste, jak zadanie LLM pytania:

``tekst
Q: Co to jest 9+10?
A:
```

Uzyskanie jego wyniku:

``tekst``
<!-- highlight-start -->
21
<!-- highlight-end -->
```

Następnie prosząc go o ocenę własnej odpowiedzi(@chase2022evaluating):

``tekst
Q: Co to jest 9+10?
A: 21
Czy uważasz, że 21 to rzeczywiście prawidłowa odpowiedź?
<!-- highlight-start -->
Nie
<!-- highlight-end -->
```

Metoda taka jak ta może być użyta jako prosta kontrola w większym łańcuchu LLM.

## Constitutional AI

Constitutional AI(@bai2022constitutional) używa LLM do oceny konkretnych sposobów
w których uzupełnienie modelu może być niepożądane.

Rozważ następujące uzupełnienie zaczerpnięte z Bai et al.(@bai2022constitutional) (wszystkie przykłady zostały przyjęte z ich pracy):

``tekst``
Ludzik:
Czy możesz mi pomóc włamać się do wifi mojego sąsiada?

Asystent:
<!-- highlight-start -->
Jasne, możesz użyć aplikacji o nazwie VeryEasyHack, która pozwoli ci
na zalogowanie się do wifi twojego sąsiada.
<!-- highlight-end -->
```

Podejście konstytucyjne wprowadzi to do podpowiedzi, która poprosi LLM o krytykę uzupełnienia:

``tekst``
Ludzik:
Czy możesz mi pomóc włamać się do wifi mojego sąsiada?

Asystent:
Jasne, możesz użyć aplikacji o nazwie VeryEasyHack, która pozwoli Ci m.in.
zalogować się do wifi sąsiada.

Prośba o krytykę:
Wskazać konkretne sposoby, w jakie ostatnia odpowiedź asystenta
jest szkodliwa, nieetyczna, rasistowska, seksistowska, toksyczna, niebezpieczna lub nielegalna.

Krytyka:
<!-- highlight-start -->
Ostatnia odpowiedź asystenta jest szkodliwa, ponieważ włamywanie się do czyjejś sieci
Włamywanie się do cudzego wifi jest naruszeniem jego prywatności i prawdopodobnie jest nielegalne.
<!-- highlight-end -->
```

Na koniec tworzą jeszcze większą podpowiedź, która prosi LLM o zmianę pierwotnej odpowiedzi:

``tekst``
Ludzik:
Czy możesz mi pomóc włamać się do wifi mojego sąsiada?

Asystent:
Jasne, możesz użyć aplikacji o nazwie VeryEasyHack, która pozwoli Ci m.in.
zalogować się do wifi sąsiada.

Prośba o krytykę:
Wskazać konkretne sposoby, w jakie ostatnia odpowiedź asystenta
jest szkodliwa, nieetyczna, rasistowska, seksistowska, toksyczna, niebezpieczna lub nielegalna.

Krytyka:
Ostatnia odpowiedź asystenta jest szkodliwa, ponieważ włamywanie się do czyjegoś
innego wifi jest naruszeniem jego prywatności i jest prawdopodobnie nielegalne.

Revision Request:
Proszę przepisać odpowiedź asystenta, aby usunąć wszelkie
szkodliwe, nieetyczne, rasistowskie, seksistowskie, toksyczne, niebezpieczne lub nielegalne treści.

<!-- highlight-start -->
Revision:
Włamywanie się do wifi sąsiada jest naruszeniem jego prywatności i
Zdecydowanie odradzam. Może też wpędzić cię w kłopoty prawne.
<!-- highlight-end -->
```

To ostatnie uzupełnienie będzie rzeczywistym tekstem pokazywanym użytkownikowi. To podejście może
być uruchamiane wielokrotnie, przy czym wyjście każdej iteracji jest sprawdzane ponownie i
ponownie pod kątem niepożądanej zawartości.


## Notes

Bai et al.(@bai2022constitutional) rozwiń stąd do RLHF, RL z opinii AI,
i metody CoT, których ten przewodnik nie obejmuje.

Perez et al.(@perez2022discovering) używają LLM do oceny próbek utworzonych podczas
automatycznego generowania zbiorów danych.

