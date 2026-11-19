---
titulo: Portfolio Otrorumbo · stato
tipo: estado
creado: 2026-11-17
actualizado: 2026-11-18
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
Controllo online di Rachele (2026-11-18): tutto ok.
**Punto 16 fatto (2026-11-18, commit 09b4e86 del Portfolio):** nella
chat niente grassetto. Se la IA scrive `**parola**`, `renderMessage` in
`Chat.tsx` toglie il doppio asterisco e la parola resta normale; le email
restano link. Provato in locale e online con una risposta finta (senza
chiamare la IA).
Per provare la chat nel browser di Lola: l'animazione di apertura lì resta
ferma, e il primo clic o Invio la salta invece di spedire. Non è un bug
del sito.
**Punto 7 fatto (2026-11-18, commit 32ab7e5 del Portfolio):** sfondo
unico e sfocato. Un solo componente `Background.tsx` per home, privacy e
404, con `public/background-blur.mp4`: il video della home già sfocato e
schiarito nel file con ffmpeg (1280×720, sfocatura sigma 10, 74% sul
colore caldo, come la 404 in Figma; 0,3 MB contro 8). Originale nitido:
`background.mp4`, resta nel progetto. L'animazione di apertura è uguale.
Approvato da Rachele ("è perfetto"); online e controllato su home, 404 e
privacy.
Punto 12 (vetro) in pausa: si riscrive dopo lo sfondo, con il riferimento
Figma del vetro e l'elenco dei componenti.
Punto 12 (vetro) rimandato al futuro (Rachele, 2026-11-18): in fondo
alla lista. Punto 23.4 chiuso (fatto da Rachele in un'altra chat).
Prossimo: 23.2 e 23.3, che per Rachele vengono dal design system (spazi e
raggi). Verificato da Lola il 2026-11-18: i token esistono, nella
collezione Figma "Misure" (raggio/xs…pill, spazio/2…32) e nel codice
(`--r-*`, `--s-*`), ma in Figma solo 10 valori su circa 4.000 nelle
schermate finali sono collegati ai token. Valori fuori scala usati: 7, 9,
14, 18, 22, 40, 48, 64 (14 usato 215 volte; nel codice `--s-14` è usato
ma non esiste). Dopo: 23.5.
Elenco delle misure fuori token nel codice scritto (2026-11-18) in
`miglioramenti-portfolio.md`, sotto il punto 23: componente, dove si vede,
riga di `globals.css`, misura e proposta. Prossimo passo: Rachele sceglie i
valori, Lola allinea il codice, lo mostra e pubblica solo con il suo ok.
In pausa (Rachele, 2026-11-18): l'analisi è fatta, la decisione la
prende quando ha tempo di leggere. Intanto si passa al 23.5.
**Punto 23.5 fatto (2026-11-18, commit a6e33d2 del Portfolio):**
sfumatura in alto nella chat desktop, piena a 80 px (sidebar), sparita a
30 px (logo). Maschera su `.chat-area` in `globals.css`. Vista da
Rachele in locale e pubblicata su sua richiesta; controllata online.
23.2 e 23.3: li vede Rachele più avanti (elenco già pronto).
**Punto 10 fatto (2026-11-18, commit 4a859e5 del Portfolio):** cambiando
progetto con le pills si muove solo l'articolo; freccia e pills restano
ferme. L'articolo scorre di lato verso la pill scelta, 32 px con
dissolvenza (0,3 s + 0,45 s, valori in `MOTION.tab`). A 0,2 + 0,3 s
"faceva scatto". Approvato da Rachele; online (nuovi valori verificati nel
codice del sito).
Punti nuovi aggiunti da Rachele (2026-11-19) nella lista: 25 testo dei
messaggi a 14 px, 26 chat più compatta, 27 logo di caricamento più
piccolo, 28 dettagli dell'animazione di entrata, 29 tag delle domande
diversi dalle chips dei progetti.
**Punti 25 + 26 fatti e online (2026-11-19, commit 6bef29c del
Portfolio), controllati su desktop e mobile:**
in `globals.css` i messaggi (IA, utente, "sta scrivendo") passano da 16
a 14 px (interlinea 1,5); padding desktop da 14/20 a 10/16, mobile da
12/16 a 8/12; spazio tra messaggi desktop 10 → 8, mobile 8 → 6. Barra di
testo: desktop 14 px, padding 8/8/8/16 (alta 54 px invece di 58); mobile
padding 6/6/6/12 (era 7, fuori token) e testo a 16 px, perché sotto i 16 px
l'iPhone ingrandisce la pagina. Solo token. Rachele: "molto meglio".
**Punto 27 fatto e online (2026-11-19, commit b477d24 del Portfolio):** logo
di caricamento (video `loader.mp4`, `.loader-logo` in `globals.css`) da
104 a 64 px su desktop, da 88 a 56 px su mobile. Rachele lo vedeva "un
millesimo di secondo" e prima dell'entrata compariva per un attimo il
portfolio aperto. Due difetti in `Loader.tsx`, corretti in locale: (1) il
controllo "almeno un giro" scattava subito (video ancora a 0), ora il logo
esce alla fine del primo giro (1,1 s; sicurezza a 6 s); (2) svaniva tutta
la schermata e sotto si vedeva il sito già aperto, ora svanisce solo il
logo e lo sfondo caldo resta, uguale alla prima schermata dell'entrata.
Codice senza errori; l'effetto l'ha visto Rachele in locale (nel browser
nascosto di Lola le animazioni restano ferme) e ha detto di pubblicare.
Dopo: 28 (dettagli dell'entrata, li dice Rachele); 29 prima in Figma.
Da approfondire più avanti (Rachele): nei prompt dire sempre di usare il
design system alla lettera e solo i token.
Font: in `Portfolio\tipografie` (copiati da `pillowtalk\`, dove erano).
Per lavorare sul codice serve la cartella Portfolio aperta nella sessione
(la sola `@` nel messaggio non basta).
Lista salvata in `miglioramenti-portfolio.md`: punti aperti in alto,
"Punti fatti" in fondo con il come (7, 9, 10, 15, 16, 19, 20, 22, 23.1, 23.4, 23.5, 24, 25, 26, 27).
Proposta di Lola in attesa: gli "imbarazzi" 18 e 17 (prompt, li scrive
Rachele).

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
- **2026-11-18 · Niente grassetto nella chat** · Il codice toglie sempre
  il doppio asterisco; una regola nel prompt è facoltativa e la scrive
  Rachele · Perché: Rachele non vuole che sia la IA a decidere quando
  usarlo · Intenzione: messaggi tutti uguali, controllati da lei.
  Scartato: mostrare il grassetto in SemiBold (pubblicato e tolto lo
  stesso giorno).

## Coda

1. ~~Finire il prototipo di Glovo~~ (fatto)
2. ~~Sistemare il prototipo di Pillowtalk~~ (fatto)
3. ~~Lista chiusa delle cose visive che non convincono~~ (fatto, Rachele)
4. Sistemare solo le cose della lista e pubblicare (Rachele e Lola). Quello
   che non è nella lista non si tocca in questo giro.
