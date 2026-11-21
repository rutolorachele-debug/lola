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

Diagnosi fatta (solo lettura, niente toccato). Due cause: RAM poca (8 GB,
quasi sempre piena) e disco pieno al 90%. Siguiente: Rachele decide se
togliere Windows.old (passo 1).

## Diagnosi (2026-11-21, misurata sul PC)

- **RAM 8 GB, un solo banco su 2 slot** (max 32 GB). Libera 2,3 GB; Windows
  già comprime la memoria (800 MB): segno che non basta. L'app Claude da
  sola usa ~2 GB. **È la causa principale della lentezza.**
- **Disco C: 51 GB liberi su 503** (90% pieno). Sotto il 10-15% libero
  Windows rallenta (criterio mio, regola diffusa).
- **Windows.old = 81 GB**: copia del vecchio Windows lasciata dal ripristino
  del 12/11. Si toglie con lo strumento di Windows «Pulizia disco».
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

1. **Decidere Windows.old** (Rachele): c'è qualcosa del vecchio PC che ti
   manca? Se no → si toglie con «Pulizia disco» (+81 GB). Lola guida passo
   passo.
2. **Comprare un banco RAM** (Rachele): DDR4 SO-DIMM 8 GB 2666 MHz, uguale a
   quello montato → 16 GB. Il miglioramento più grande per pochi euro. Si
   monta in 10 minuti (o in negozio).
3. **Resti vecchi** (Lola propone, Rachele approva): `$AV_ASW`,
   `MobiSaverCache`, backup Dr.Fone, archivi iCloud doppi.
4. **Foto**: impostare iCloud Photos su «ottimizza spazio» e spostare le
   cartelle grandi (PORTO, Fez, CAMERA) su disco esterno o cloud.
5. **Abitudini**: riavviare almeno una volta a settimana; togliere Edge
   dall'avvio automatico.
6. **Capire il disco D** (7,7 GB quasi pieno).
