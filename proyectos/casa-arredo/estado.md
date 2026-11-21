---
titulo: Arredo casa · estado
tipo: estado
creado: 2026-11-21
actualizado: 2026-11-21
estado: ABIERTO
---

# Arredo casa · provare dove stanno i mobili nella casa nuova

**Para qué existe** (2026-11-21): la casa nuova arriva quasi vuota; serve
capire come incastrare i mobili di salone, camera e studio prima di
comprarli o portarli. Una pagina web con la pianta in scala dove si
trascinano rettangoli con misure modificabili.

- En vivo: https://claude.ai/artifact/UQScJccNoSTYKuhMWRAFPN (privata, la condivide Rachele)
- Código: `proyectos/casa-arredo/index.html` (un solo file, senza librerie)

## Dónde retomar (2026-11-21)

Pagina fatta e provata (aggiungere, trascinare, ridimensionare, ruotare,
sovrapposizioni in rosso, salvataggio nel browser). Mancano le misure di
cucina, bagno e corridoio e quale stanza è salone/camera/studio.
Siguiente: Rachele la prova e porta le misure mancanti.

## Decisiones de este frente

- **2026-11-21 · misure dalla planimetria a mano** · stanza 1 = 4,30 × 2,90;
  stanza 2 = 4,43 × 3,70; stanza 3 = 3,20 × 3,05 (misure grandi del foglio).
  Porte: 80 cm (stanza 1, posizione stimata), 100 cm (stanza 2), 80 cm
  (stanza 3). Pilastri, finestre, cucina, bagno, corridoio: stimati dallo
  schizzo, segnati «da confermare». I pilastri sono spostabili.
- **2026-11-21 · condividere = copia/incolla del testo** · nella pagina
  pubblicata download e finestre di conferma sono bloccati.

- **2026-11-21 · mobile first** · sul telefono: pianta a tutta altezza,
  barra in basso per il mobile scelto, catalogo che sale dal basso. Da
  980 px in su: tre colonne (catalogo, pianta, misure).
- **2026-11-21 · GitHub e Vercel in un repo a parte** · la pagina non si
  pubblica dal repo `lola`, perché esporrebbe la memoria di Lola. Serve un
  repo vuoto solo per la pagina (es. `arredo-casa`).

## Cola

0. Rachele crea su GitHub il repo vuoto `arredo-casa`; Lola ci mette la
   pagina; Rachele la importa su Vercel (Rachele, poi Lola)
1. Rachele prova la pagina e dice cosa non torna (Rachele)
2. Misure di cucina, bagno, corridoio e posizione reale dei pilastri (Rachele)
3. Nomi delle stanze: quale è salone, camera, studio (Rachele, si scrive nella pagina)
4. Aggiornare la pianta con le misure vere e ripubblicare (Lola)
