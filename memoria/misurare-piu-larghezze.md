---
name: misurare-piu-larghezze
description: prima di dire dove sta un elemento del sito, misurarlo sulla pagina vera a più larghezze, mai dedurlo da un numero nel CSS
metadata:
  type: feedback
---

Prima di spiegare a Rachele dove sta un elemento (e quindi qual è il problema), misurarlo sulla pagina vera a 2-3 larghezze (es. 1280, 1440, 1536), non dedurlo da un valore nel CSS.

**Why:** punto 31 (2026-11-19): ho detto "la chat è a 450 fissi, quindi a 1536 è spostata a sinistra" leggendo solo `--chat-left`. Era falso: il contenitore `.stage` è largo al massimo 1440 e centrato, quindi sopra 1440 la chat era già centrata. Rachele ha approvato una correzione basata su una spiegazione sbagliata.

**How to apply:** misura con `getBoundingClientRect` e controlla il contenitore (offsetParent) prima di proporre. Collegato a [[layout-parlare-di-bordi]].
