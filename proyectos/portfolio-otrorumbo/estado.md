---
titulo: Portfolio Otrorumbo · stato
tipo: estado
creado: 2026-11-17
actualizado: 2026-11-17
estado: ABIERTO
---

# Portfolio Otrorumbo · il portfolio di Rachele, già online

**Per cosa esiste** (2026-11-06): mostrare il lavoro di Rachele (tra gli
altri i prototipi di Glovo e Pillowtalk) in modo da poterlo presentare a chi
vuole. Research e progetto sono fatti e pubblicati; ora si sistema la parte
visiva.

- Online / dove si vede: https://otrorumbo.vercel.app
- Prototipi: https://otrorumbo-pillowtalk.vercel.app ·
  https://otrorumbo-glovoduo.vercel.app
- Codice: `Desktop\Design\Proyectos\Prototipo claude\Portfolio\claude`
  (app Next.js, con PRD e system prompt in `docs/` e `prompt/`). Accanto:
  `glovo/` e `pillowtalk/` con le immagini, `Portfolio assets/`.

## Dove riprendere (2026-11-17)

I passi 1-3 sono fatti. Passo 4 in corso, si parte dal **punto 22
(tipografie)**. Decisioni di Rachele (2026-11-17): il logo lo fa lei e lo
manda da Figma; i testi restano uguali, cambia solo il font in IBM Plex
Sans; prima di toccare il codice si provano un paio di schermate in Figma
per vedere se le misure vanno ritoccate. Fatto il 2026-11-17 in Figma
(file "Otrorumbo — Visual References", frame "Tipografie nuove", via
Desktop Bridge): G-D6 e G-M3 in Plex Sans, stessi corpi e pesi. Risultato:
nessun a capo cambia; Plex è 1-8 px più largo; i testi 10-12 px crescono
di 2 px in altezza; il SemiBold di Plex pesa più di quello di Figtree.
Logo: modello di Rachele nel frame, Redaction 50 Italic, colore accent.
Rachele non era convinta dell'aspetto; su proposta di Lola il frame è ora
in Plex Medium al posto del SemiBold (più vicino al peso di Figtree).
Verdetto di Rachele: Plex non le piace, "troppo serio" (meglio in Medium);
Figtree "troppo rotondo". Serve una via di mezzo. Rachele ha scelto di
provare **Funnel Sans** (Google Fonts): copie "· Funnel Sans" sotto le due
schermate Plex, nel frame "Tipografie nuove", pesi originali (Regular e
SemiBold). Misure quasi identiche a Figtree: niente da ritoccare.
Non provati (proposta di Lola, in riserva): Instrument Sans, Hanken
Grotesk, Onest.
Verdetto: Funnel Sans "molto meglio", pesi da rivedere. Terza fila
"· Funnel Sans · Light": testi Light, titoli progetti SemiBold, titoli di
sezione (Proyectos, Contactos) Medium. Poi (Rachele): chips dei progetti,
"Abrir prototipo", "Reservar una llamada", sottotitolo dell'articolo e
pills di navigazione mobile in Regular; chips delle domande (tag) in
Medium. Avviso di Lola: il sottotitolo (Regular 18) ora si distingue poco
dal testo (Light 16). Per vederlo: copia "G-D3 · Proyecto abierto ·
Glovo · Funnel Sans" (articolo desktop, a destra nel frame) con tutti i
pesi scelti e il logo Redaction.
Rachele (2026-11-17): il titolo della slide / sottotitolo "per adesso
resta così" in Regular.
**Punto 22 fatto e online (2026-11-17).** Funnel Sans e logo nuovo
pubblicati (commit a1321e2, insieme a Next.js 16.4.6 e alle modifiche di
articoli, PRD e system prompt fatte in un'altra chat). Controllato su
https://otrorumbo.vercel.app: logo Redaction accento, testi Funnel Sans
con i pesi giusti. `app/layout.tsx` carica Funnel Sans 300/400/500/600 e
Redaction 50 Italic (file in `app/fonts/`); `app/globals.css` ha i pesi
decisi. Logo: "otrorumbo" su una riga, Redaction 24 px, colore accento,
anche su 404 e privacy; resta accento dopo l'apertura (prima diventava
bianco). Rachele ha visto il sito con Funnel Sans: "va e mi piace".
Testi fuori dalla prova Figma, scelti da Lola sullo stesso schema:
"Reservar una llamada" del menu Regular (come in Figma), titolo del
dialogo e titoli delle sezioni privacy Regular, titolo privacy SemiBold.
Rachele ha approvato il logo. Next.js 16.4.6: 0 vulnerabilità nelle
parti che vanno online (le 15 restanti sono strumenti di lavoro locali).
**Punti leggeri fatti (2026-11-17, commit b817bce):** link nuovi dei
prototipi (24), chat senza barra di scorrimento (19, 23.1), chips dei
progetti a pill (9), barra di testo senza contorno (15).
**Articolo Glovo (2026-11-17, commit 5b35db6 e 00f3902):** testo
allineato al system prompt corretto da Rachele (più 3 correzioni di
spagnolo approvate: "Partimos de", "el brief ha ido cambiando de forma",
"dos riders"); 6 video e la foto finale al loro posto (originali in
`Portfolio\glovo`, nel sito versioni web 720p senza audio né GPS in
`public/glovo/`). Prima l'articolo non mostrava nessun media: ora il
codice mostra video (muti, in loop) e foto. La foto 07 (4:3) viene
tagliata un po' nel riquadro 16:9: Rachele la guarda online.
Pillowtalk: testo uguale al prompt; i contenuti li manda Rachele quando
li ha. Push fatto da Lola il 2026-11-17 (il login a GitHub funziona).
Correzioni di Rachele (commit c57d480): la prima frase ("Feature para la
app Glovo Riders.", per Pillowtalk "Proyecto: …") è una descrizione sotto
il titolo e i chips, Regular 18; il video 01 sta sopra il brief, e il
contatore parte da lì (01/06); la foto finale non ha testo e quindi non ha
numero. Il video 01 in loop "faceva un salto": ora va a metà velocità (approvato
da Rachele); in futuro forse lo cambia con altro. Tutto controllato online.
Prossimo: controllo online; dopo, altri punti
fattibili: 12 (vetro sulle pills), 16 (grassetto), 23.3 (spazio sotto la
barra).
Font: in `Portfolio\tipografie` (copiati da `pillowtalk\`, dove erano).
Per lavorare sul codice serve la cartella Portfolio aperta nella sessione
(la sola `@` nel messaggio non basta).
Lista salvata in `miglioramenti-portfolio.md` (solo i punti aperti).
Proposta di Lola in attesa: gli "imbarazzi" 18, 17, 16.

## Decisioni di questo progetto

- **2026-11-17 · Cosa vuol dire "finito"** · Finito = lo posso presentare.
  Non si chiude mai: resta "a fermentare" finché non arriva il momento di
  riprenderlo, e quel momento può anche non arrivare (come Glovo e
  Pillowtalk). Da quando smetto di modificarlo è finito e lo condivido con
  chi voglio · Perché: un progetto non si può iterare per sempre ·
  Intenzione: poter smettere di lavorarci senza sentirlo incompleto.
  Scartato: "finito = lo mando a qualcuno senza scuse" (proposta di Lola).
- **2026-11-17 · Font dei testi: Funnel Sans** · Pesi: testi Light; titoli
  dei progetti SemiBold; titoli di sezione (Proyectos, Contactos) e tag
  delle domande Medium; chips, pulsanti, pills e sottotitoli Regular ·
  Perché: Figtree troppo rotondo, IBM Plex Sans troppo serio · Intenzione:
  un sito leggero e caldo, con i titoli dei progetti come unico punto
  forte. Scartato: IBM Plex Sans (prevista dalla mail, provata in Figma).

## Coda

1. ~~Finire il prototipo di Glovo~~ (fatto)
2. ~~Sistemare il prototipo di Pillowtalk~~ (fatto)
3. ~~Lista chiusa delle cose visive che non convincono~~ (fatto, Rachele)
4. Sistemare solo le cose della lista e pubblicare (Rachele e Lola). Quello
   che non è nella lista non si tocca in questo giro.
