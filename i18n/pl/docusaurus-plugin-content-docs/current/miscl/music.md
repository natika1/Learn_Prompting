---
sidebar_position: 3
---

# 🟢 Music Generation

Modele generacji muzyki stają się coraz bardziej popularne i w końcu będą miały duży wpływ na przemysł muzyczny.

Modele generowania muzyki mogą tworzyć progresje akordów, melodie lub pełne utwory. Mogą strukturyzować i tworzyć muzykę w określonych gatunkach oraz komponować lub improwizować w stylu określonych artystów.

Jednakże, pomimo ogromnego potencjału modeli muzycznych, są one obecnie trudne do podpowiadania. Wygenerowane dane wyjściowe często nie są w pełni konfigurowalne przez podpowiedzi, w przeciwieństwie do modeli generowania obrazów czy tekstu.

## Riffusion
import riffusion from '@site/docs/assets/riffusion_phonk.png';

<div style={{textAlign: 'center'}}>.
  <img src={riffusion} style={{width: "500px"}} />
</div>

Riffusion(@Forsgren_Martiros_2022), dopracowana wersja Stable Diffusion, może być sterowana za pomocą podpowiedzi do generowania instrumentów i pseudo stylów, ale ma ograniczoną liczbę dostępnych beatów.

# Mubert

[Mubert](https://mubert.com/) wydaje się interpretować podpowiedzi poprzez analizę sentymentu, która łączy odpowiednią stylistykę muzyczną z podpowiedzią (szczegółowe kontrolowanie parametrów muzycznych poprzez podpowiedzi nie jest możliwe). Nie jest jasne, jak wiele z generowania wyników jest wykonywane przez AI.

## Inne

Istnieją próby użycia GPT-3 jako narzędzia Text-2-Music z rzeczywistymi podpowiedziami dotyczącymi elementów muzycznych na "mikro-poziomie" nut (zamiast raczej niejasnych podpowiedzi-analogii w stylu mubert & riffusion) (np. `zapisz nuty dla piosenki ludowej, która używa tylko A, B, C#, F# i G`). Jednakże, obecnie te próby są ograniczone do pojedynczych instrumentów.

Inne podejścia obejmują łańcuch modeli, który [konwertuje dowolny obraz na dźwięk, który go reprezentuje](https://huggingface.co/spaces/fffiloni/img-to-music) i podpowiadanie ChatGPT, aby wygenerował kod dla [bibliotek Pythona, które tworzą dźwięk](https://twitter.com/teropa/status/1598713756074246145).

## Notes

Podpowiadanie muzyki nie jest dobrze zbudowane... jeszcze. MusicLM wygląda obiecująco, ale nie jest jeszcze dostępny publicznie.


