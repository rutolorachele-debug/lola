---
name: lola-su-github
description: La cartella Lola ha una copia su GitHub (privata) e ogni commit si carica da solo
metadata:
  type: reference
---

Dal 2026-11-21 la cartella Lola ha una copia online nel repository privato
`github.com/rutolorachele-debug/lola` (account GitHub di Rachele:
**rutolorachele-debug**, lo stesso del portfolio). Scopo: se Rachele perde
il pc, non perde niente.

**Caricamento automatico:** il file `.git/hooks/post-commit` fa `git push`
dopo ogni commit. Se il push fallisce (niente internet) il commit resta sul
pc e stampa un avviso: lancia `git push` a mano.

**Attenzione:** quel file sta in `.git/hooks`, che NON va su GitHub. Su un
pc nuovo: `git clone https://github.com/rutolorachele-debug/lola.git` e poi
ricreare il file post-commit (una riga: `git push --quiet origin HEAD`).

**Creare un repository nuovo** su GitHub va fatto dal sito (Git non può):
il login di Git su questo pc serve solo a caricare. Il browser dell'app
non ha l'accesso a GitHub e l'estensione Chrome il 2026-11-21 non
rispondeva, quindi l'ha creato Rachele a mano. Vedi [[push-github-senza-gh]].
