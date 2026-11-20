---
name: commit-solo-righe-mie
description: Prima di un commit guardare il diff di ogni file; se dentro ci sono modifiche non mie, salvare solo le mie righe
metadata:
  type: feedback
---

Prima di `git add` su un file già modificato, guardare `git diff <file>`.
Se dentro ci sono modifiche che non ho fatto io (un'altra chat lavora
sullo stesso file), salvo solo le mie righe: una patch con il mio pezzo e
`git apply --cached`, il resto resta nel file senza commit.

**Perché:** il 2026-11-20, aggiungendo i video Pillowtalk, il commit del
Portfolio si è portato dietro una sezione nuova del system prompt scritta in
un'altra chat. Me ne sono accorta dai numeri del commit (30 righe invece di
6) e l'ho rifatto prima del push.

**Come applicarlo:** dopo ogni commit, `git show --stat HEAD`: le righe
devono tornare con quelle che ho cambiato io.
