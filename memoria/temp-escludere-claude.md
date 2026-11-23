---
name: temp-escludere-claude
description: pulendo AppData\Local\Temp escludere la cartella `claude`, è dove Lola salva i risultati dei comandi
metadata:
  type: feedback
---

Svuotando `C:\Users\Rachele\AppData\Local\Temp` si cancella anche
`Temp\claude`, dove l'app di Claude tiene i risultati dei comandi e lo
scratchpad: il comando stesso perde l'output.

**Why:** successo il 2026-11-23 (Pulizia pc). Nessun danno ai file di
Rachele, ma il risultato del comando è andato perso.

**How to apply:** nel comando di pulizia aggiungere
`Where-Object Name -ne 'claude'` prima di `Remove-Item`.
