---
sidebar_position: 50
---
# 🟢 Repetytorium

Powtarzanie tego samego słowa w podpowiedzi lub podobnych fraz może spowodować, że model
do podkreślenia tego słowa w wygenerowanym obrazie (@oppenlaender2022taxonomy). Na przykład, [@Phillip Isola](https://twitter.com/phillip_isola/status/1532189632217112577) wygenerował te wodospady za pomocą DALLE:

import bad_water from '@site/docs/assets/images_chapter/bad_water.jpg';
import good_water from '@site/docs/assets/images_chapter/good_water.jpg';
import planet from '@site/docs/assets/images_chapter/planet.png';
import planet_aliens from '@site/docs/assets/images_chapter/planet_aliens.png';


`Piękny obraz góry obok wodospadu.`.

<div style={{textAlign: 'center'}}>.
  <img src={bad_water} style={{width: "750px"}} />
</div>

`Bardzo bardzo bardzo bardzo bardzo bardzo bardzo bardzo bardzo bardzo bardzo bardzo piękny obraz góry obok wodospadu.`

<div style={{textAlign: 'center'}}>.
  <img src={good_water} style={{width: "750px"}} />
</div>

Nacisk na słowo `bardzo` wydaje się poprawiać jakość generacji! Powtórzenie może
być również używane do podkreślania terminów tematycznych. Na przykład, jeśli chcesz wygenerować obraz
planety z kosmitami, użycie podpowiedzi `Planeta z kosmitami kosmici kosmici kosmici kosmici kosmici kosmici kosmici` zwiększy prawdopodobieństwo, że kosmici znajdą się w wynikowym obrazie.
zwiększy prawdopodobieństwo, że obcy są na obrazie wynikowym. Poniższe obrazy zostały wykonane za pomocą Stable Diffusion.

`Planeta z kosmitami`
<div style={{textAlign: 'center'}}>.
  <img src={planeta} style={{width: "250px"}} />
</div>

`Planeta z kosmitami kosmitami kosmitami kosmitami kosmitami kosmitami kosmitami kosmitami`.

<div style={{textAlign: 'center'}}>.
  <img src={planet_aliens} style={{szerokość: "250px"}} />
</div>


## Notes

Metoda ta nie jest doskonała, a użycie wag (następny artykuł) jest często lepszym rozwiązaniem.

