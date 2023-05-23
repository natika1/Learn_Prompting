---
sidebar_position: 99
---
# 🟢 Midjourney

[Midjourney](https://www.midjourney.com) to generator obrazów AI, który działa poprzez interfejs bota Discorda, jak również aplikację internetową (planowana jest wersja API Midjourney). Proces generowania obrazów za pomocą Midjourney jest zgodny z tymi samymi podstawowymi zasadami, co inne generatory obrazów AI, w tym wykorzystanie podpowiedzi do prowadzenia procesu generowania.

Jedną z unikalnych cech Midjourney w porównaniu z innymi generatorami obrazów AI jest jego zdolność do tworzenia wizualnie uderzających i artystycznie skomponowanych obrazów. Przypisuje się to specjalistycznemu treningowi modelu, który umożliwia mu tworzenie wysokiej jakości obrazów o określonych parametrach artystycznych (więcej na ten temat w "Zaawansowane polecenia" > "Parametry").

Możesz eksperymentować z Midjourney Botem w [Learn Prompting Discord](http://learnprompting.org/discord) lub w [oficjalnym serwerze Midjourney Discord](https://discord.gg/midjourney).

import midjourney_astronaut from '@site/docs/assets/midjourney_astronaut.png';
import midjourney_astronaut_params from '@site/docs/assets/midjourney_astronaut_params.png';
import midjourney_astronaut_multi1 from '@site/docs/assets/midjourney_astronaut_multi1.png';
import midjourney_astronaut_multi2 from '@site/docs/assets/midjourney_astronaut_multi2.png';
import midjourney_astronaut_ip2 from '@site/docs/assets/midjourney_astronaut_ip2.png';

import midjourney_astronaut_params_a12 from '@site/docs/assets/midjourney_astronaut_params_a12.png';
import midjourney_astronaut_params_a169 from '@site/docs/assets/midjourney_astronaut_params_a169.png';

import midjourney_astronaut_params_c20 from '@site/docs/assets/midjourney_astronaut_params_c20.png';
import midjourney_astronaut_params_c80 from '@site/docs/assets/midjourney_astronaut_params_c80.png';

import midjourney_astronaut_params_q05 from '@site/docs/assets/midjourney_astronaut_params_q05.png';
import midjourney_astronaut_params_q2 from '@site/docs/assets/midjourney_astronaut_params_q2.png';

import midjourney_astronaut_params_s50 from '@site/docs/assets/midjourney_astronaut_params_s50.png';
import midjourney_astronaut_params_s900 from '@site/docs/assets/midjourney_astronaut_params_s900.png';

import midjourney_astronaut_params_sameseed from '@site/docs/assets/midjourney_astronaut_params_sameseed.png';
import midjourney_astronaut_params_seed123 from '@site/docs/assets/midjourney_astronaut_params_seed123.png';

import midjourney_astronaut_params_tile from '@site/docs/assets/midjourney_astronaut_params_tile.png';
import midjourney_astronaut_params_tilegrid from '@site/docs/assets/midjourney_astronaut_params_tilegrid.png';
import midjourney_astronaut_params_tilecomplete from '@site/docs/assets/midjourney_astronaut_params_tilecomplete.jpeg';

import midjourney_astronaut_params_v1 from '@site/docs/assets/midjourney_astronaut_params_v1.png';
import midjourney_astronaut_params_v2 from '@site/docs/assets/midjourney_astronaut_params_v2.png';
import midjourney_astronaut_params_v3 from '@site/docs/assets/midjourney_astronaut_params_v3.png';



# Basic Usage

Podstawową anatomią podpowiedzi z Midjourney jest `/imagine prompt: [IMAGE PROMPT] [--OPTIONAL PARAMETERS]`.

Na przykład: `/imagine prompt: astronaut on a horse`.


<div style={{textAlign: 'center'}}>.
  <img src={midjourney_astronaut} style={{width: "350px"}} />
</div>


Przykład z parametrami: `/imagine prompt: astronaut on a horse --ar 3:2 --c 70 --q 2 --seed 1000 `.

<div style={{textAlign: 'center'}}>.
  <img src={midjourney_astronaut_params} style={{width: "350px"}} />
</div>

W tym podstawowym przykładzie zastosowano następujące parametry:


`--ar 3:2` ustawia proporcje obrazu na 3:2

`--c 70` dodaje wartość chaosu równą 70, aby umożliwić Midjourney bardziej swobodną interpretację podpowiedzi (zakres wartości chaosu: 0 - 100)

`--seed 100` ustawia arbitralną wartość nasion, która może być użyta do ponownego wyrenderowania lub przerobienia obrazu później.


(dowiedz się więcej o parametrach Midjourney w "Advanced Prompts" > "Parameters")


# Zaawansowane podpowiedzi
Zaawansowane podpowiedzi w Midjourney wykorzystują parametry i specjalne techniki podpowiedzi wspierane przez algorytm Midjourney.

## Multi Prompts
Midjourney domyślnie interpretuje twój znak zachęty całościowo. Użycie podwójnego dwukropka `::` powoduje, że Midjourney interpretuje każdą część zachęty osobno.

Przykład:

`tekst`
/imagine prompt: astronaut and horse
```
<div style={{textAlign: 'center'}}>.
  <img src={midjourney_astronaut_multi1} style={{width: "350px"}} />
</div>

`tekst`
/imagine podpowiada: astronauta:: i koń
```
<div style={{textAlign: 'center'}}>.
  <img src={midjourney_astronaut_multi2} style={{width: "350px"}} />
</div>


## Sugestie dotyczące obrazów
Przesyłając obraz do Discorda i używając jego adresu URL w podpowiedzi, możesz poinstruować Midjourney, by użył tego obrazu do wpłynięcia na treść, styl i kompozycję twoich wyników.
Przykład:
[Astronauta (Źródło: Wikipedia)](https://en.wikipedia.org/wiki/Astronaut#/media/File:STS41B-35-1613_-_Bruce_McCandless_II_during_EVA_(Retusz).jpg)

``tekst``
/imagine prompt: [image URL], malarstwo impresjonistyczne
```
<div style={{textAlign: 'center'}}>.
  <img src={midjourney_astronaut_ip2} style={{width: "350px"}} />
</div>

## Parametry (v4)

Poniższe parametry są obsługiwane przez najnowszy model Midjourney (v4).

### Aspect Ratio:

`--ar [ratio]` zmienia domyślny stosunek (1:1) na nowy stosunek (obecnie maksymalny obsługiwany stosunek to 2:1)

Przykład: `astronauta na koniu --ar 16:9` i `astronauta na koniu --ar 1:2`.

<div style={{textAlign: 'center'}}>.
  <img src={midjourney_astronaut_params_a169} style={{width: "350px"}} />
  &nbsp;
   <img src={midjourney_astronaut_params_a12} style={{width: "175px"}} />
</div>


### Chaos:

`--c [wartość]` ustawia wartość chaosu, która określa jak bardzo Midjourney zmienia podpowiedź; im wyższa wartość chaosu tym bardziej niezwykłe i nieoczekiwane wyniki i kompozycje (zakres: 0 - 100)

Przykład: `astronauta na koniu --c20` i `astronauta na koniu --c 80`.

<div style={{textAlign: 'center'}}>.
  <img src={midjourney_astronaut_params_c20} style={{width: "350px"}} />
  &nbsp;
   <img src={midjourney_astronaut_params_c80} style={{szerokość: "350px"}} />
</div>


### Jakość:

`--q [wartość]` definiuje ile czasu zostanie poświęcone na wygenerowanie obrazu, co zwiększa jego jakość. Domyślnym ustawieniem jest "1". Wyższe wartości wykorzystują więcej minut GPU twojej subskrypcji (akceptuje wartości ".25", ".5" , "1" i "2")

Przykład: `astronauta na koniu --q .5` i `astronauta na koniu --q 2`.

<div style={{textAlign: 'center'}}>.
  <img src={midjourney_astronaut_params_q05} style={{width: "350px"}} />
  &nbsp;
   <img src={midjourney_astronaut_params_q2} style={{szerokość: "350px"}} />
</div>


### Seed:

`--seed [wartość]` ustawia numer nasion, który określa punkt początkowy (pole szumu) dla generacji obrazu. Nasiona dla każdego obrazu są generowane losowo, jeśli nie są określone parametrem seed. Użycie tej samej liczby nasion i podpowiedzi spowoduje powstanie podobnych obrazów.

Przykład: `astronauta na koniu --seed 123`.

<div style={{textAlign: 'center'}}>.
  <img src={midjourney_astronaut_params_seed123} style={{width: "350px"}} />
  &nbsp;
   <img src={midjourney_astronaut_params_seed123} style={{width: "350px"}} />
</div>


### Stylize:

`--stylize [wartość]` lub `--s [wartość]` wpływa na to jak mocno Midjourney stosuje swój algorytm artystyczny.  Niskie wartości tworzą obrazy, które ściśle odpowiadają podpowiedzi, wysokie wartości tworzą bardzo artystyczne obrazy, które są mniej związane z podpowiedzią. Domyślnie jest to 100, zakres wartości to 0 - 1000.
(Uwaga: możesz użyć polecenia `/settings` by zmienić domyślną wartość stylize z "🖌️ Style Med" (=`--s 100`) na "🖌️ Style Low" (=`--s 50`), "🖌️ Style High" (=`--s 250`) lub "🖌️ Style Very High" (=`--s 750`)).

Przykład: `astronauta na koniu --s 50` i `astronauta na koniu --s 900`.

<div style={{textAlign: 'center'}}>.
  <img src={midjourney_astronaut_params_s50} style={{width: "350px"}} />
  &nbsp;
   <img src={midjourney_astronaut_params_s900} style={{szerokość: "350px"}} />
</div>


### Wersja:
`--v [numer wersji]` lub `--version [numer wersji]` pozwalają na dostęp do wcześniejszych modeli Midjourney (1-3).

Przykład: `--v 1`, `--v 2` i `--v 3`.

<div style={{textAlign: 'center'}}>.
  <img src={midjourney_astronaut_params_v1} style={{width: "220px"}} />
  &nbsp;
   <img src={midjourney_astronaut_params_v2} style={{szerokość: "220px"}} />
   &nbsp;
      <img src={midjourney_astronaut_params_v3} style={{szerokość: "220px"}} />
</div>


## Parametry (poprzednie modele)

### Same Seed

`--sameseed`: podczas gdy parametr `--seed` wytwarza pojedyncze pole szumu zastosowane na wszystkich obrazach w siatce początkowej, parametr sameseed stosuje ten sam szum początkowy do wszystkich obrazów w siatce początkowej, więc wytworzy bardzo podobne obrazy.

Przykład: `astronauta na koniu --sameseed --v 3`.

<div style={{textAlign: 'center'}}>.
  <img src={midjourney_astronaut_params_sameseed} style={{width: "350px"}} />
</div>


### Płytka

`--tile` generuje obrazy, które mogą być używane jako powtarzające się płytki do tworzenia bezszwowych wzorów dla tkanin, tapet i tekstur (działa tylko z modelami 1 - 3)

Przykład: `astronauta na koniu --tile --v 3`.

<div style={{textAlign: 'center'}}>.
  <img src={midjourney_astronaut_params_tilegrid} style={{width: "220px"}} />
  &nbsp;
  <img src={midjourney_astronaut_params_tile} style={{szerokość: "220px"}} />
  &nbsp;
  <img src={midjourney_astronaut_params_tilecomplete} style={{szerokość: "220px"}} />
</div>


### Video

`--video` tworzy krótki film z generowania siatki obrazu. Reakcja za pomocą emoji ✉️ pozwala Midjourney Botowi wysłać Ci DM z linkiem do filmu.

Przykład: `astronauta na koniu --video --v 3`.

<div style={{textAlign: 'center'}}>.
 <video width="320" height="240" autoplay muted>.
  <source src="https://i.mj.run/27c89699-d96d-4834-b6fa-b022a453eb28/video.mp4" type="video/mp4">
</source>
</video>
</div>



## Linki

[Oficjalna dokumentacja Midjourney](https://docs.midjourney.com/)

