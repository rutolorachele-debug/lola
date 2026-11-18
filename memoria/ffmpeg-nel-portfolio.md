---
name: ffmpeg-nel-portfolio
description: Per modificare video e immagini c'è ffmpeg dentro il progetto Portfolio, anche se non è installato nel sistema
metadata:
  type: reference
---

`ffmpeg` non è installato nel sistema (`where ffmpeg` non trova niente), ma
c'è nel progetto Portfolio: `Portfolio\claude\node_modules\ffmpeg-static\ffmpeg.exe`.
Serve per convertire, ridurre o sfocare video (con questo sono stati fatti i
video web di Glovo).

**Perché:** il 2026-11-18 Lola ha detto a Rachele "il computer non ha lo
strumento", dopo aver cercato solo nel sistema. Era falso e ha quasi
cambiato una decisione di design.

**Come applicarlo:** prima di dire che uno strumento manca, cercarlo anche
nei `node_modules` del progetto.
