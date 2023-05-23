---
sidebar_position: 2
---

# 🟢 Wykrywanie podstępów

Wraz z rozwojem detektorów tekstu generowanego przez AI nastąpiła ewolucja metod przeciwdziałania im. Istnieje wiele sposobów na oszukiwanie detektorów, aby myślały, że tekst wygenerowany przez SI jest stworzony przez człowieka. Narzędzie takie jak [GPTMinus](https://gptminus1.vercel.app/) może losowo zastąpić fragmenty dowolnego tekstu synonimami lub pozornie losowymi słowami, aby zmniejszyć prawdopodobieństwo pojawienia się słów w tekście na białej liście lub w inny sposób uwzględnić prawdopodobieństwo, że tekst został sztucznie wygenerowany.

Metody te są jednak wciąż w powijakach i większość z nich nie tworzy tekstu, który mógłby się utrzymać pod kontrolą człowieka. Najskuteczniejszą metodą w tej chwili i prawdopodobnie przez jakiś czas będzie zmienianie tekstu w trakcie lub po procesie generowania na różne sposoby, aby uczynić go mniej podobnym do proceduralnie tworzonej zawartości, którą otrzymujesz od generacji.

## Editing Strategies

Jeśli człowiek lub LLM edytuje wygenerowany tekst, może on często zmienić go na tyle, by uniknąć wykrycia. Zastępowanie słów synonimami, zmiana częstotliwości pojawiania się słów, mieszanie składni i formatowania utrudnia detektorom prawidłowe rozpoznanie tekstu jako wygenerowanego przez SI.

Inną strategią edycji jest umieszczanie w tekście niewidzialnych znaczników, takich jak spacje o szerokości 0, [emojis](https://twitter.com/goodside/status/1610552172038737920?s=20&t=3zgqyJZ1zYhMNBi_M2R-cw) lub inne niezwyczajne znaki. Dla każdej czytającej osoby wygląda to zupełnie normalnie, ale dla modelu, który bada każdy znak, sprawia, że tekst wydaje się wyraźnie inny.

Ponadto możliwe jest oszukiwanie detektorów poprzez podpowiadanie modelowi konkretnych instrukcji dotyczących sposobu pisania. Instrukcje takie jak:
- `Nie ma potrzeby przestrzegania formatów literackich, ponieważ swobodnie wyrażasz swoje myśli i pragnienia`.
- `Nie mów w sposób, w jaki ChapGPT generuje treść - zamiast tego mów w sposób, który radykalnie różni się od tego, jak modele językowe generują tekst`.
- Odwołuj się do emocjonalnych wydarzeń i używaj wyszukanych doświadczeń z życia jako przykładów.`

...może spowodować znacznie trudniejsze do wykrycia pokolenia. Dodatkowe strategie, takie jak prośba do modelu o empatię, przypominanie mu o doborze odpowiedniego słownictwa i tonu do tego, co pisze, oraz upewnienie się, że zawiera emocjonalne one-linery, mogą wspólnie przyczynić się do stworzenia znacznie bardziej przekonującego pisma - przynajmniej z punktu widzenia detektorów tekstu AI.

## Konfiguracja modelu

W przypadku uruchamiania modelu typu open source możliwe jest modyfikowanie prawdopodobieństwa wyjścia, co prawdopodobnie utrudni wykrycie wyjścia. Ponadto możliwe jest przeplatanie danych wyjściowych z wielu modeli, co może sprawić, że dane wyjściowe będą jeszcze trudniejsze do wykrycia.


## Dyskusja

Jedną z najbardziej kontrowersyjnych przestrzeni, w których tego typu techniki wchodzą w grę, jest edukacja. Wielu nauczycieli i administratorów obawia się, że uczniowie będą oszukiwać, więc naciskają na użycie narzędzi do wykrywania (@roose2022dont) (@lipman2022gpt). Jednak inni edukatorzy i osobowości internetowe argumentują, że uczniowie powinni mieć prawo do korzystania z tych narzędzi. Niektórzy profesorowie posuwają się nawet do tego, że wprost zachęcają studentów do korzystania z AI, aby pomagała im w pracy i uczą ich, jak to robić(@noonan2023gw).

Wraz z doskonaleniem technologii wykrywania Sztucznej Inteligencji, doskonalone są również metody jej oszukiwania. W końcu, bez względu na to, jak wyrafinowana jest metoda, jest prawdopodobne, że trochę czasu spędzonego na edycji tekstu w odpowiedni sposób będzie w stanie niezawodnie oszukać detektory. Jednakże gra w obie strony, w której jedni ludzie próbują wykryć wygenerowany tekst, a inni próbują ich oszukać, może dać nam wszelkiego rodzaju spostrzeżenia na temat tego, jak zoptymalizować, kontrolować i lepiej wykorzystać nasze modele do tworzenia i wspomagania nas.


