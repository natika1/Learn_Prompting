---
sidebar_position: 1
---

# 🟢 Wykrywanie tekstu wygenerowanego przez AI

Wykrywanie tekstu wygenerowanego przez SI to duży problem dla badaczy i edukatorów zajmujących się bezpieczeństwem,
między innymi. Narzędzia takie jak [GPTZero](https://gptzero.me), [detektor GPT2](https://openai-openai-detector.hf.space) oraz [detektory dwujęzyczne](https://github.com/Hello-SimpleAI/chatgpt-comparison-detection) odniosły znaczący sukces,
Można je jednak [oszukać](https://learnprompting.org/docs/miscl/trickery).

OpenAI i inni badacze(@bansal2022certified)(@gu2022watermarking) pracują nad wprowadzeniem statystycznego znaku wodnego do generowanego przez siebie tekstu, ale i to można oszukać modyfikując duże porcje tekstu.

Problem wykrywania tekstu przez AI będzie prawdopodobnie wyścigiem zbrojeń w miarę wprowadzania nowych modeli i nowych metod wykrywania. Wiele firm już zaczęło budować rozwiązania, które jak twierdzą są bardzo skuteczne, ale trudno to udowodnić, zwłaszcza, że modele zmieniają się w czasie.

W tym artykule omówimy niektóre z obecnych metod wykrywania tekstu generowanego przez AI, a w następnym kilka sposobów, które ludzie znaleźli, aby je oszukać.

# OpenAI Text Classifier

OpenAI Text Classifier](https://platform.openai.com/ai-text-classifier) jest dość dobrą próbą stworzenia uniwersalnego detektora tekstów AI.
Poprzez wytrenowanie modelu na dużej ilości danych wygenerowanych przez SI oraz tekstów napisanych przez człowieka o podobnej jakości, detektor jest w stanie obliczyć prawdopodobieństwo, że dany tekst został stworzony przez LLM.

Ma kilka ograniczeń - nie akceptuje żadnych zgłoszeń poniżej 1000 słów, tekst może być łatwo edytowany, aby zepsuć obliczenia prawdopodobieństwa, a ze względu na profesjonalnie skoncentrowany zestaw treningowy, ma więcej problemów z tekstem stworzonym przez dzieci lub osoby nie mówiące po angielsku.

W tej chwili oznacza on tekst ludzki jako wygenerowany przez SI tylko w 9% przypadków, a poprawnie identyfikuje tekst wygenerowany przez SI w ~26% przypadków. Wraz ze wzrostem mocy i zakresu modelu liczby te ulegną poprawie, ale może się okazać, że aby odpowiednio ocenić, czy tekst jest generowany, czy nie, potrzebne są bardziej szczegółowe detektory.

# The Watermark Method

Jedna z metod wykrywania tekstu wygenerowanego przez AI wymaga wprowadzenia statystycznego znaku wodnego podczas generowania tekstu. Techniki te mogą wykorzystywać "białą listę" LLM, która jest metodą określania, czy tekst został wygenerowany przez określony model AI. Znak wodny działa poprzez wybranie randomizowanego zestawu "zielonych" tokenów przed wygenerowaniem słowa, a następnie miękkie promowanie użycia wybranych tokenów podczas próbkowania. Te ważone wartości mają minimalny wpływ na jakość generacji, ale mogą być algorytmicznie wykryte przez inny LLM(@kirchenbauer2023watermarking).

Jest to intrygujący pomysł, ale wymaga, aby twórcy modelu zaimplementowali ten framework do swojego LLM. Jeśli model nie ma wbudowanego znaku wodnego, ta metoda nie będzie działać.

# DetectGPT

Metoda [DetectGPT](https://detectgpt.ericmitchell.ai/)(@mitchell2023detectgpt) jest w stanie wykryć tekst wygenerowany przez SI przy mniejszej ilości ustawień niż poprzednie koncepcje. Naukowcy odkryli, że generacje tekstu LLM mają tendencję do "zajmowania regionów o negatywnej krzywiźnie funkcji prawdopodobieństwa log modelu". Z tego powodu możliwe jest stworzenie opartego na krzywiźnie systemu do określania, czy blok tekstu został wygenerowany proceduralnie.

Działa poprzez obliczenie prawdopodobieństwa log z modelu, który został uznany za generujący tekst i porównanie ich z losowymi zmianami tekstu z innego, wstępnie wytrenowanego modelu języka ogólnego. W ten sposób DetectGPT jest w stanie zidentyfikować prawdopodobieństwo wygenerowania fragmentu przy użyciu samych krzywych prawdopodobieństwa!

## Uwaga

Dodatkowe omówienie tematu czujek i tego, jak ludzie je oszukują, można znaleźć w [tym artykule](https://learnprompting.org/docs/miscl/trickery).


