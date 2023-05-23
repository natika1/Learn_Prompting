---
sidebar_position: 1
---

# 🟢 Wstęp

Szczególnym wyzwaniem jest znalezienie najlepszej zachęty do stworzenia idealnego obrazu.
Badania nad metodami, które to umożliwiają, nie są tak rozwinięte jak w przypadku podpowiedzi tekstowych. Ta
może wynikać z nieodłącznych wyzwań związanych z tworzeniem obiektów, które są zasadniczo subiektywne
i często brakuje dobrych wskaźników dokładności. Nie należy się jednak obawiać, gdyż podpowiedzi obrazkowe
społeczność (@parsons2022dalleprompt) dokonała wielkich odkryć dotyczących sposobów podpowiadania różnych modeli obrazów (@rombach2021highresolution) (@ramesh2022hierarchical).

Ten przewodnik obejmuje podstawowe techniki podpowiadania obrazu, ale gorąco zachęcamy
zachęcamy do zapoznania się z materiałami zamieszczonymi na końcu rozdziału.
Dodatkowo, poniżej przedstawiamy przykład całego procesu podpowiadania obrazu.


## Przykład.

Tutaj przejdę przez przykład, jak stworzyłem obrazy na stronę główną tego kursu.
Eksperymentowałem z stylem low poly w projekcie dotyczącym głębokiego uczenia się z wzmocnieniem
neuronowego pola radiacyjnego. Spodobał mi się styl low poly i chciałem go wykorzystać
dla obrazów tego kursu.

Chciałem astronautę, rakietę i komputer do zdjęć na pierwszej stronie.

Zrobiłem kilka badań, jak tworzyć obrazy low poly, na [r/StableDiffusion](https://www.reddit.com/r/StableDiffusion/)
i innych stronach, ale nie znalazłem nic super pomocnego.

Postanowiłem po prostu zacząć od DALLE i podpowiedzi `Low poly white and blue rocket shooting to the moon in front of a sparse green meadow` i zobaczyć co się stanie.

import rockets1 from '@site/docs/assets/rockets_dalle_1.png';
import rockets2 from '@site/docs/assets/rockets_dalle_2.png';
import computer_1 from '@site/docs/assets/computer_dalle_1.png';
import astronauta_1 from '@site/docs/assets/astronauta_dalle_1.png'
import astronauta_2 from '@site/docs/assets/astronauta_sd_1.png'
import rocket_sd_1 from '@site/docs/assets/rocket_sd_1.png';
import rocket_final from '../../static/img/rocket.png';
import laptop_sd_1 from '@site/docs/assets/laptop_sd_1.png';
import gemstone_sd_1 from '@site/docs/assets/gemstone_sd_1.png';
import gemstone_sd_2 from '@site/docs/assets/gemstone_sd_2.png';
import gemstone_sd_3 from '@site/docs/assets/gemstone_sd_3.png';
import focus_final from '../../static/img/computer.png';
import astronaut_final from '../../static/img/astronaut.png';

<div style={{textAlign: 'center'}}>.
  <img src={rockets1} style={{szerokość: "750px"}} />
</div>


<div style={{textAlign: 'center'}}>.
  <img src={rockets2} style={{szerokość: "750px"}} />
</div>

Pomyślałem, że te wyniki były całkiem przyzwoite jak na pierwszą próbę; szczególnie podobała mi się
dolna lewa rakieta.

Następnie chciałem mieć komputer w tym samym stylu: `Low poly biały i niebieski komputer siedzący na skąpej zielonej łące`.

<div style={{textAlign: 'center'}}>.
  <img src={komputer_1} style={{szerokość: "750px"}} />
</div>

W końcu potrzebowałem astronauty! Niskiej jakości biało-niebieski astronauta siedzący na zielonej łące z górami niskiej jakości w tle wydawał się wystarczający.

<div style={{textAlign: 'center'}}>.
  <img src={astronauta_1} style={{szerokość: "750px"}} />
</div>

Wydawało mi się, że druga jest przyzwoita.

Teraz miałem astronautę, rakietę i komputer. Byłem z nich zadowolony,
więc umieściłem je na pierwszej stronie. Po kilku dniach i uwagach moich przyjaciół
zdałem sobie sprawę, że styl nie jest spójny 😔.


Zrobiłem trochę więcej badań na [r/StableDiffusion](https://www.reddit.com/r/StableDiffusion/) i znalazłem ludzi używających słowa izometryczny. Postanowiłem to wypróbować, używając Stable Diffusion zamiast DALLE.
Zdałem sobie również sprawę, że muszę dodać więcej modyfikatorów do mojej podpowiedzi
aby ograniczyć styl. Wypróbowałem tę podpowiedź:
`Świat low poly, z astronautą w białym kombinezonie i niebieskiej przyłbicy siedzącym na skąpej, zielonej łące z górami low poly w tle. Wysoce szczegółowy, izometryczny, 4K`.

<div style={{textAlign: 'center'}}>.
  <img src={astronauta_2} style={{szerokość: "250px"}} />
</div>

Nie były one zbyt dobre, więc postanowiłem zacząć od rakiety.

`Świat low poly, z biało-niebieską rakietą wysadzaną z rzadkiej zielonej łąki z górami low poly w tle. Wysoce szczegółowy, izometryczny, 4K`.

<div style={{textAlign: 'center'}}>.
  <img src={rocket_sd_1} style={{szerokość: "250px"}} />
</div>

Nie są one szczególnie dobre, ale po odrobinie iteracji tutaj, skończyłem z

<div style={{textAlign: 'center'}}>.
  <img src={rocket_final} style={{szerokość: "250px"}} />
</div>

Teraz potrzebowałem lepszego laptopa

`Świat low poly, z biało-niebieskim laptopem siedzącym na skąpej, zielonej łące z górami low poly w tle. Ekran jest całkowicie niebieski. Wysoko szczegółowy, izometryczny, 4K`.

<div style={{textAlign: 'center'}}>.
  <img src={laptop_sd_1} style={{szerokość: "250px"}} />
</div>

Otrzymałem trochę niespójne wyniki; podoba mi się prawy dolny, ale postanowiłem pójść w innym kierunku.

`Świat low poly, ze świecącym biało-niebieskim kamieniem szlachetnym siedzącym na skąpej zielonej łące z górami low poly w tle. Wysoce szczegółowy, izometryczny, 4K`.

<div style={{textAlign: 'center'}}>.
  <img src={gemstone_sd_1} style={{width: "250px"}} />
</div>

To nie było całkiem w porządku. Spróbujmy czegoś magicznego i świecącego.

`Świat low poly, ze świecącym białym i niebieskim kamieniem szlachetnym magicznie unoszącym się na środku ekranu nad skąpą zieloną łąką z górami low poly w tle. Wysoce szczegółowy, izometryczny, 4K`.

<div style={{textAlign: 'center'}}>.
  <img src={gemstone_sd_2} style={{width: "250px"}} />
</div>

Te mi się podobały, ale chciałem mieć kamień na środku ekranu.

`Świat low poly, ze świecącym niebieskim kamieniem szlachetnym magicznie unoszącym się na środku ekranu nad skąpą zieloną łąką z górami low poly w tle. Wysoce szczegółowy, izometryczny, 4K`.

<div style={{textAlign: 'center'}}>.
  <img src={gemstone_sd_3} style={{width: "250px"}} />
</div>

Gdzieś tutaj wykorzystałem zdolność SD do tego, aby poprzedni obrazek miał jakiś wpływ na przyszłe obrazy.
I w ten sposób doszedłem do:

<div style={{textAlign: 'center'}}>.
  <img src={focus_final} style={{szerokość: "250px"}} />
</div>

W końcu trafiłem na astronautę.

`Świat low poly, w którym astronauta w białym apartamencie i niebieskiej przyłbicy siedzi na skąpej, zielonej łące z górami low poly w tle. Wysoce szczegółowy, izometryczny, 4K`.

<div style={{textAlign: 'center'}}>.
  <img src={astronauta_final} style={{szerokość: "250px"}} />
</div>

W tym momencie byłem wystarczająco zadowolony ze spójności stylu pomiędzy moimi trzema obrazami, aby użyć ich na stronie internetowej.
na stronie internetowej. Najważniejszym wnioskiem dla mnie było to, że był to bardzo iteracyjny, wymagający badań proces,
i musiałem modyfikować swoje oczekiwania i pomysły w miarę eksperymentowania z różnymi podpowiedziami i modelami.

