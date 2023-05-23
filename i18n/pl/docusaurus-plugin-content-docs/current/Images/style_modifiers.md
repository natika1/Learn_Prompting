---
sidebar_position: 4
---
# 🟢 Modyfikatory stylu

Modyfikatory stylu są po prostu deskryptorami, które konsekwentnie
dają pewne style (np. "zabarwiony na czerwono", "zrobiony ze szkła", "wyrenderowany w Unity") (@oppenlaender2022taxonomy). Mogą one być łączone razem, aby
stworzyć jeszcze bardziej szczegółowe style. Mogą "zawierać informacje o okresach sztuki, szkołach i stylach, ale także o materiałach i mediach, technikach i artystach"(@oppenlaender2022taxonomy).

import pyramids from '@site/docs/assets/images_chapter/pyramids.png';
import red_pyramids from '@site/docs/assets/images_chapter/red_pyramids.png';

# Przykład

Oto kilka piramid wygenerowanych przez DALLE, z podpowiedzią `pyramid`.

<div style={{textAlign: 'center'}}>.
  <img src={piramidy} style={{width: "750px"}} />
</div>

Oto kilka piramid wygenerowanych przez DALLE, z podpowiedzią `Piramida ze szkła, wyrenderowana w Unity i zabarwiona na czerwono`, która wykorzystuje 3 modyfikatory stylu.

<div style={{textAlign: 'center'}}>.
  <img src={red_pyramids} style={{szerokość: "750px"}} />
</div>

Oto lista kilku przydatnych modyfikatorów stylu:

`tekst
photorealistic, by greg rutkowski, by christopher nolan, painting, digital painting, concept art, octane render, wide lens, 3D render, cinematic lighting, trending on ArtStation, trending on CGSociety, hyper realist, photo, natural light, film grain
```

## Notes

Oppenlaender et al.(@oppenlaender2022taxonomy) opisują deskryptor `rendered in ...` jako wzmacniacz jakości.
jako wzmacniacz jakości, ale nasza robocza definicja różni się, ponieważ ten modyfikator konsekwentnie generuje określony styl Unity (lub innego silnika renderującego). Jako taki, będziemy nazywać ten deskryptor modyfikatorem stylu.

