---
name: openclaw-log-setup
description: OpenClaw su Windows — lo stato vero del gateway sta nei log di setup in Roaming, non nel log della tray
metadata:
  type: feedback
---

Lo stato di OpenClaw si legge da `AppData\Roaming\OpenClawTray\Logs` (log di setup, orari in UTC = ora locale −1), non solo da `AppData\Local\OpenClawTray\openclaw-tray.log`.

**Why:** il 2026-11-21 ho detto "nessun gateway collegato" guardando solo il log della tray; in realtà il gateway nativo era già installato (Microsoft Store via WinGet) e si era collegato per 3 minuti. Risposta sbagliata a Rachele.

**How to apply:** prima di dire cosa manca in OpenClaw, cercare nei log di setup ("Native Gateway", "handshake") e controllare la porta 18789 (`netstat -ano -p tcp`, cercare 18789). Vedi anche [[non-supporre-che-non-abbia-visto]].
