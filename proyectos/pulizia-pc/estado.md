---
titulo: Pulizia pc — estado
tipo: estado
creado: 2026-11-21
actualizado: 2026-11-23
estado: ABIERTO
---

# Pulizia pc · far tornare veloce il portatile di Rachele

**Para qué existe** (2026-11-21): il PC è lento anche dopo il ripristino
della settimana scorsa (non si accendeva, tolti tutti i programmi). Obiettivo:
che torni fluido per lavorare (Figma, Chrome, Claude) senza perdere file.

- PC: Acer Nitro AN515-54 (2019), Intel i5-9300H 4 core, Windows 11 Home
- Disco: SSD NVMe 512 GB, salute «Healthy»

## Dónde retomar (2026-11-23)

Disco C da 51 a 179 GB liberi (Windows.old, Cestino, Temp). RAM: Rachele la
compra più avanti. Siguiente: Rachele lancia «Pulizia disco» (passo 2), poi
app in sottofondo (passo 3).

## Diagnosi (2026-11-21, misurata sul PC; disco aggiornato 2026-11-23)

- **RAM 8 GB, un solo banco su 2 slot** (max 32 GB). Libera 2,3 GB; Windows
  già comprime la memoria (800 MB): segno che non basta. L'app Claude da
  sola usa ~2 GB. **È la causa principale della lentezza.**
- **Disco C: 179 GB liberi su 503** (64% pieno). Sotto il 10-15% libero
  Windows rallenta (criterio mio, regola diffusa): ora non è più un problema.
- Avvio automatico: solo 6 programmi (OneDrive, Figma Agent, Edge, audio,
  antivirus). Va bene, poco da guadagnare.
- Foto: Immagini ~92 GB locali + «iCloud Photos» (580 GB in totale, in gran
  parte solo in cloud). Documenti 54 GB, Desktop 48 GB.
- Disco D: 7,7 GB quasi pieno (da capire cos'è: chiavetta o partizione).
- Acceso da 5 giorni senza riavvio.

## Decisiones de este frente

- **2026-11-21 · Lola non cancella niente da sola** — ogni eliminazione la
  approva Rachele, file per file o cartella per cartella · intención: zero
  rischio di perdere foto o lavori.

## Cola

1. **Comprare un banco RAM** (Rachele, deciso 2026-11-21): DDR4 SO-DIMM 8 GB
   2666 MHz, uguale a quello montato → 16 GB. Il miglioramento più grande
   per pochi euro. Si monta in 10 minuti (o in negozio).
2. **Aggiornamenti Windows già installati, 1,3 GB** (Rachele, con Lola che
   guida): servono i permessi di amministratore, da terminale Lola non può.
   Start → «Pulizia disco» → «Pulisci file di sistema» → spuntare «Pulizia
   di Windows Update» → OK.
3. **App che girano in sottofondo** (Lola propone, Rachele approva): pesano
   sulla RAM più che sul disco. Programmi installati: pochi (il ripristino
   li ha tolti). Candidate: Teams (2 versioni), Collegamento al telefono
   (YourPhone, 130 MB di RAM), Copilot, giochi/Xbox, Notizie, Meteo,
   Clipchamp, Mixed Reality. Da chiedere: OpenClaw Companion (installato
   21/11), la riconosce?
4. **Resti vecchi** (piccoli, misurati 2026-11-23): `$AV_ASW` e
   `MobiSaverCache` vuoti, Dr.Fone 0,1 GB, FluidRay 1,7 GB, iTubeGo 0,8 GB,
   archivi «Foto di iCloud» 13 GB (da capire se doppi).
5. **Foto**: impostare iCloud Photos su «ottimizza spazio» e spostare le
   cartelle grandi (PORTO, Fez, CAMERA) su disco esterno o cloud.
6. **Abitudini**: riavviare almeno una volta a settimana; togliere Edge
   dall'avvio automatico.
7. **Capire il disco D** (7,7 GB quasi pieno).

## Punti fatti

- **Decidere Windows.old** (Rachele). Conteneva SOLO i dati dei programmi di
  prima (`Users\Rachele\AppData`, 80,6 GB: Chrome 26,6, CapCut 19,6 con 2,7
  di progetti), non foto né documenti. Fatto (2026-11-21): Rachele ha detto
  che non serve niente; Lola l'ha cancellato da terminale. Disco C da 51 a
  125 GB liberi. Restano 10 MB di file protetti, ininfluenti.
- **Cestino: 65 GB** (Rachele lo guarda e lo svuota lei). Buttato il 17/11;
  dentro anche video di clienti (Kevin y Lucia, entrevistas 9-10, 8 GB) e la
  cartella `Desktop\Design\Material` (10 GB). Fatto (2026-11-23): svuotato da
  Rachele, misurato 0,1 GB.
- **Temporanei** (Lola, sicuro): Temp 0,9 GB + aggiornamenti Windows già
  installati 1,3 GB. Fatto (2026-11-23): Temp svuotato da Lola (restano 0,08
  GB di file in uso); gli aggiornamenti chiedono l'amministratore → passo 2.
