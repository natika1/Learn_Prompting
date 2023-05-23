---
sidebar_position: 60
---

# 🟢 Terminy ważone

Niektóre modele (Stable Diffusion, Midjourney, itp.) pozwalają na nadanie wagi terminom w podpowiedzi. Można to wykorzystać do podkreślenia pewnych słów lub fraz w wygenerowanym obrazie. Można
Może być również użyty do pomniejszenia znaczenia pewnych słów lub fraz w wygenerowanym obrazie. Rozważmy prosty przykład:

import mountains from '@site/docs/assets/images_chapter/mountains.png';
import mountains_no_trees from '@site/docs/assets/images_chapter/mountains_no_trees.png';
import planet from '@site/docs/assets/images_chapter/planets.png';


# Przykład

Oto kilka gór wygenerowanych przez Stable Diffusion, z podpowiedzią `mountain`.

<div style={{textAlign: 'center'}}>.
  <img src={mountains} style={{width: "350px"}} />
</div>

Jeśli jednak chcemy mieć góry bez drzew, możemy użyć zachęty `mountain | tree:-10`. Ponieważ ważyliśmy drzewa bardzo negatywnie, nie pojawiają się one w wygenerowanym obrazie.

<div style={{textAlign: 'center'}}>.
  <img src={góry_nie_drzewa} style={{szerokość: "350px"}} />
</div>

Terminy ważone mogą być łączone w bardziej skomplikowane podpowiedzi, np.
Planeta w kosmosie:10 | wybuchająca kolorem czerwonym, niebieskim i fioletowym:4 | kosmici:-10 | 4K, wysoka jakość

<div style={{textAlign: 'center'}}>.
  <img src={planety} style={{szerokość: "350px"}} />
</div>

## Notes

Przeczytaj więcej o ważeniu w niektórych zasobach na końcu tego rozdziału.

