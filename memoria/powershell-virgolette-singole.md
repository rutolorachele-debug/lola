---
name: powershell-virgolette-singole
description: comandi PowerShell lanciati da Bash vanno tra virgolette singole, altrimenti Bash mangia i $
metadata:
  type: feedback
---

Lanciando `powershell -Command "..."` da Bash, i `$_` e `$os` vengono
sostituiti da Bash prima di arrivare a PowerShell: il comando si rompe.

**Why:** successo il 2026-11-21 (Pulizia pc): tre comandi di diagnosi falliti.

**How to apply:** sempre `powershell -NoProfile -Command '...'` con virgolette
singole fuori.
