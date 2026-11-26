---
name: documenti-stato-attuale
description: Documenti e liste dicono solo lo stato attuale; un punto della lista si aggiorna solo quando è chiuso, mai mentre ci si lavora
metadata:
  type: feedback
---

I documenti di lavoro (PRD, brief, system prompt, testi, liste dei
miglioramenti, `estado.md`) dicono solo come stanno le cose adesso. Niente
"prima era X, ora è Y", niente "aggiornato il…".

**Un punto di una lista si aggiorna solo quando è chiuso**: deciso o fatto.
Mentre ci si lavora (prove, idee, pareri, scarti) non si scrive niente nella
lista né nello stato. Se la sessione si chiude a metà, una sola riga: «In
corso: prove in <dove>. Da decidere.» Quando si chiude: la decisione e il
perché, in poche righe.

**Why:** con Claude le correzioni trasformano i documenti in cronologie e
Rachele perde tempo a ripulirli (2026-11-17). Si è ripetuto il 2026-11-19
sul punto 29 del portfolio: ad ogni prova scrivevo nella lista e nello stato
idee, pareri di Rachele e scarti, e il punto è diventato un diario, con la
formattazione rotta. Causa: avevo preso «le decisioni si registrano nella
sessione» come «registra ogni passo», e la cronologia dello `estado.md` mi
ha fatto da modello.

**Al push sul sito ufficiale**, nello stesso giro: ogni punto pubblicato
passa a «Punti fatti» nella lista dei miglioramenti e sparisce da «Da
decidere». Il 2026-11-26 i punti 2, 3, 4 e 34 risultavano «in locale» da
tre giorni, ma erano già online.

**How to apply:** prima di toccare una lista chiediti «questo punto è
chiuso?». Se no, non scrivere. La storia sta solo in Git e nella sezione
"Decisioni" di `estado.md` / `canon/decisiones.md` (con "Scartato" se serve).
