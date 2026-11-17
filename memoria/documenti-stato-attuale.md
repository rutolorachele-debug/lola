---
name: documenti-stato-attuale
description: Quando Rachele corregge un documento (PRD, brief, testi), si riscrive allo stato attuale, senza cronologia
metadata:
  type: feedback
---

Quando Rachele corregge qualcosa in un documento di lavoro (PRD, brief,
system prompt, testi, schede di progetto), il documento si riscrive come se
fosse sempre stato così. Niente "prima era X, ora è Y", niente "sostituisce
quanto scritto in…", niente "aggiornato il…".

**Why:** con Claude le correzioni trasformano PRD e brief in cronologie di
progetto, e Rachele perde molto tempo a ripulirli (2026-11-17).

**How to apply:** la storia sta solo in due posti. Git (lo storico) tiene le
versioni vecchie. `canon/decisiones.md` e la sezione "Decisioni" di ogni
`estado.md` tengono il perché di una scelta, con una riga "Scartato" se
serve. Ovunque altrove: solo lo stato attuale. Negli appunti di memoria il
"Why" racconta la correzione, perché serve a non ripetere l'errore.
