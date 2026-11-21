---
titulo: Pulizia pc — estado
tipo: estado
creado: 2026-11-21
actualizado: 2026-11-21
estado: ABIERTO
---

# Pulizia pc · far tornare veloce il portatile di Rachele

**Para qué existe** (2026-11-21): il PC è lento anche dopo il ripristino
della settimana scorsa (non si accendeva, tolti tutti i programmi). Obiettivo:
che torni fluido per lavorare (Figma, Chrome, Claude) senza perdere file.

- PC: Acer Nitro AN515-54 (2019), Intel i5-9300H 4 core, Windows 11 Home
- Disco: SSD NVMe 512 GB, salute «Healthy»

## Dónde retomar (2026-11-21)

Windows.old tolto: disco C da 51 a 125 GB liberi. Rachele compra la RAM
(passo 1). Siguiente: resti vecchi (passo 2), Lola propone e Rachele approva.

## Diagnosi (2026-11-21, misurata sul PC)

- **RAM 8 GB, un solo banco su 2 slot** (max 32 GB). Libera 2,3 GB; Windows
  già comprime la memoria (800 MB): segno che non basta. L'app Claude da
  sola usa ~2 GB. **È la causa principale della lentezza.**
- **Disco C: 125 GB liberi su 503** (75% pieno). Sotto il 10-15% libero
  Windows rallenta (criterio mio, regola diffusa).
- Avvio automatico: solo 6 programmi (OneDrive, Figma Agent, Edge, audio,
  antivirus). Va bene, poco da guadagnare.
- Foto: Immagini ~92 GB locali + «iCloud Photos» (580 GB in totale, in gran
  parte solo in cloud). Documenti 54 GB, Desktop 48 GB.
- Resti vecchi: cartella `$AV_ASW` (Avast 2020), `MobiSaverCache`,
  `Wondershare_DrFone_WhatsApp_Backup`, due archivi «Foto di iCloud» (13 GB).
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
2. **Resti vecchi** (Lola propone, Rachele approva): `$AV_ASW`,
   `MobiSaverCache`, backup Dr.Fone, archivi iCloud doppi.
3. **Foto**: impostare iCloud Photos su «ottimizza spazio» e spostare le
   cartelle grandi (PORTO, Fez, CAMERA) su disco esterno o cloud.
4. **Abitudini**: riavviare almeno una volta a settimana; togliere Edge
   dall'avvio automatico.
5. **Capire il disco D** (7,7 GB quasi pieno).

## Punti fatti

- **Decidere Windows.old** (Rachele). Conteneva SOLO i dati dei programmi di
  prima (`Users\Rachele\AppData`, 80,6 GB: Chrome 26,6, CapCut 19,6 con 2,7
  di progetti), non foto né documenti. Fatto (2026-11-21): Rachele ha detto
  che non serve niente; Lola l'ha cancellato da terminale. Disco C da 51 a
  125 GB liberi. Restano 10 MB di file protetti, ininfluenti.
