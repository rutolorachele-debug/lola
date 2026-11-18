---
name: provare-chat-senza-ia
description: Come provare la chat del portfolio nel browser senza chiamare la IA e senza salvare conversazioni
metadata:
  type: reference
---

Per provare come la chat del portfolio mostra una risposta, nel browser di
Lola si sostituisce `window.fetch` per `/api/chat` con una risposta finta
JSON `{ parts: [testo], fullText, cierre: false, reserva: false, cv: false }`.
Funziona in locale e online.

**Perché:** niente costo della IA e nessuna conversazione finta salvata nei
log di Rachele.

**Come applicarlo:** nel browser di Lola l'animazione di apertura resta
ferma finché non si fa uno screenshot, e il primo clic o Invio la salta
invece di spedire. Prima fare uno screenshot, poi scrivere e inviare con il
pulsante. Non è un bug del sito. Vedi [[push-github-senza-gh]] per pubblicare.
