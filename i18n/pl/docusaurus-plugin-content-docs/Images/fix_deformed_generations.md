---
sidebar_position: 90
---
# 🟢 Fix Deformed Generations

Zdeformowane generacje, szczególnie na częściach ludzkiego ciała (np. dłonie, stopy), są częstym problemem wielu modeli. Można sobie z tym poradzić do pewnego stopnia dzięki dobrym negatywnym podpowiedziom(@blake2022with). Poniższy przykład został zaadaptowany z [tego postu na Reddicie](https://www.reddit.com/r/StableDiffusion/comments/z7salo/with_the_right_prompt_stable_diffusion_20_can_do/).

## Przykład.

import good_pitt from '@site/docs/assets/images_chapter/good_pitt.png';
import bad_pitt from '@site/docs/assets/images_chapter/bad_pitt.png';

Używając Stable Diffusion v1.5 i poniższej podpowiedzi, generujemy ładny obraz Brada Pitta, oczywiście z wyjątkiem jego rąk!

`studio medium portrait of Brad Pitt waving his hands, detailed, film, studio lighting, 90mm lens, by Martin Schoeller:6`.

<div style={{textAlign: 'center'}}>.
  <img src={bad_pitt} style={{szerokość: "250px"}} />
</div>

Używając solidnej negatywnej podpowiedzi, możemy wygenerować znacznie bardziej przekonujące ręce.

`studyjny portret średni Brad Pitt macha rękami, szczegółowy, film, oświetlenie studyjne, obiektyw 90mm, autorstwa Martina Schoellera:6 | oszpecone, zdeformowane ręce, nieostry, ziarnisty, zepsuty, zezowaty, nieumarły, photoshopped, prześwietlony, niedoświetlony, lowres, zła anatomia, złe ręce, dodatkowe cyfry, mniej cyfr, złe cyfry, złe uszy, złe oczy, zła twarz, wykadrowany: -5`
<div style={{textAlign: 'center'}}>.
  <img src={good_pitt} style={{width: "250px"}} />
</div>

Użycie podobnej negatywnej podpowiedzi może pomóc również w przypadku innych części ciała. Niestety, ta technika nie jest spójna, więc być może będziesz musiał spróbować wielu pokoleń
zanim uzyskasz dobry wynik.
W przyszłości ten rodzaj podpowiedzi powinien być zbędny, ponieważ modele będą coraz lepsze.
Niemniej jednak, obecnie jest to bardzo przydatna technika.


# Notes

Ulepszone modele takie jak [Protogen](https://civitai.com/models/3666/protogen-x34-official-release) są często lepsze z rękami, stopami itp.

