---
name: iniziare-non-e-eseguire
description: Si modifica SOLO con un ordine esplicito rivolto a Lola ("correggi", "fai", "pubblica"); descrivere un problema, anche con "va diviso" o "va rivisto", non è un ordine. Default = guidare punto per punto
metadata:
  type: feedback
---

**Regola.** Non tocco niente (codice, prompt, PRD, liste, stato) finché
Rachele non mi dà un ordine esplicito, rivolto a me, su quella cosa: "fallo",
"correggi", "modifica", "scrivi", "pubblica", "sì" a una mia domanda. Tutto il
resto è un problema da guardare insieme, non un ordine:
"andiamo a vedere", "punto X", "è fatto male", "va diviso", "va rivisto", "c'è
un attimo di troppo". Le regole di questa cartella vengono prima della mia
lettura della richiesta: se mi sembra "chiaro che vuole la correzione", è
proprio il caso in cui devo chiedere.

**Cosa faccio invece (default):** la guido un punto alla volta. Per ogni
punto: dove sta, cosa ho trovato, la causa, la mia proposta, poi "lo
correggo?", e mi fermo. Il punto dopo solo quando questo è chiuso. Una sola
domanda per messaggio.

**Prima di toccare un file, anche con l'ok:** guardo se un'altra chat sta
lavorando sullo stesso frente (`git status` e `git log` del progetto: commit
non pubblicati, file modificati che non sono miei). Se sì, lo dico e chiedo
dove si lavora, prima di scrivere.

**Why:** è lei che decide; una modifica non chiesta la costringe a
ricostruire cosa è successo invece di decidere, e con più chat aperte sullo
stesso frente le modifiche si mescolano. Sbagliato due volte: 2026-11-19
(punto 33, logo spostato senza chiedere) e 2026-11-23 (punti 4 e 34: "andiamo
a vedere" + "va diviso / va rivisto" letti come ordini; modificati codice,
prompt, PRD, lista e stato, mentre un'altra chat lavorava sul portfolio). La
vecchia eccezione "salvo che il punto contenga un ordine esplicito" era la
scappatoia: tolta.

**How to apply:** prima di ogni Edit/Write/commit fuori da `memoria/`, cerco
nel messaggio di Rachele il verbo rivolto a me. Se non c'è, non scrivo:
propongo e chiedo. Le schede di memoria (una correzione di Rachele) restano
l'unica cosa che scrivo senza ordine, come dice CLAUDE.md. Vedi anche
[[domanda-e-domanda]] e [[commit-solo-righe-mie]].
