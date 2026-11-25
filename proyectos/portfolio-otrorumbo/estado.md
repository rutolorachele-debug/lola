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

**Mobile, decisioni da eseguire col codice (2026-11-23, chat senza
codice):** questa chat raccoglie le modifiche; la sessione col codice le
esegue e Rachele le prova in localhost. Audit mobile per parti.
1. **Apertura uguale al desktop (deciso, Rachele, 2026-11-24):** niente
   card dietro durante i primi messaggi. Messaggi 1-3 solo sullo sfondo,
   centrati (bolle allineate a sinistra), all'altezza dove stanno a fine
   animazione con la card aperta. Al messaggio 4 (progetti) la card entra
   dal basso tutta in una volta (slide-in, non cresce a poco a poco),
   insieme a progetti e header, come sul desktop. Ordine dei messaggi
   invariato. Perché: stessa esperienza su desktop e mobile; probabilmente
   toglie anche gli scatti (la card che cambia altezza).
2. **Header: resta com'è (Rachele, 2026-11-24)**, logo al messaggio 4 e
   menu al 5, come sul desktop. L'idea sotto è scartata.
   ~~Header (logo e menu) per ultimo (da provare, Rachele):~~ i progetti
   compaiono più in alto, nello spazio dell'header; finiti i messaggi,
   mentre escono i tag, scende l'header (e i progetti scendono al loro
   posto). Spazio NON riservato: era la proposta di Lola, scartata perché
   toglierebbe il senso (recuperare spazio). Va visto se vale la pena.
   Oggi i tempi sono strani: il logo entra con i progetti, il menu dopo.
3. **Tag delle domande in fill:** sono allungati a tutta larghezza. Devono
   avere misure e padding del chip del design system e stare uno accanto
   all'altro. Misurati da Lola (2026-11-24, Funnel Sans Medium 14, gap 8,
   spazio utile 358 su iPhone 390): con lati 16 servono 388 px, con 12
   372, con 10 364, con 8 356 (ci stanno per 2 px, e su iPhone da 375 no).
   Ridurre il padding non basta. **Deciso (Rachele, 2026-11-24):** padding
   del design system (8/16), uno per riga, ognuno largo quanto il suo
   testo. Correzione: togliere le righe 667-668 di `globals.css`.
4. **Card chiusa:** deve restare solo la barra con il drag handle; oggi si
   vede anche un pezzo degli ultimi messaggi. Oggi, chiusa, non si riesce
   a riaprire.
5. **Card all'invio:** quando si manda un messaggio la card si apre fino
   all'altezza massima decisa (Rachele ricorda circa 3/4: verificare il
   valore nel codice o nei documenti).
6. **Sfondo:** quasi non si vede, sembra molto ingrandito. Da riguardare
   dopo il punto 1 (con l'apertura nuova il tramonto si vedrà di più).
7. **Progetto aperto:** l'header (logo e menu) si accavalla alla barra
   del progetto (freccia indietro e pills), che deve stare sotto l'header.
   L'articolo esce dallo schermo a destra, non adattato al mobile (forse
   stessa causa del difetto desktop sotto ~1300 px, punto 31).

**Verificato nel codice (2026-11-24, repo `otro-rumbo` su GitHub, ultimo
commit f1541a2, letto da Lola in sola lettura):**
- Apertura (`page.tsx`): messaggi 1 saluto, 2 respiro, 3 refugio, 4
  proyectos (entrano sidebar e logo), 5 invito (entrano barra, tag e menu).
  Stessi tempi su desktop e mobile: il logo coi progetti e il menu dopo
  non è un errore del mobile, è la sequenza di entrambi.
- Tag: su mobile `.chips` è in colonna (`flex-direction: column`, riga
  667) e i chip si allungano; lati 14 (riga 668). Togliere le due righe.
- Card chiusa: i messaggi non vengono nascosti, la card si accorcia e basta
  (152 su 844, minimo 140, `MOTION.mobile`). Si riapre già toccando il
  campo di testo e inviando; la maniglia solo chiude, trascinare in su non
  c'è. Ma Rachele (2026-11-24): sul telefono non si apre mai, né col campo
  né con la maniglia. Provato da Lola (2026-11-24, sito in locale, Chrome
  a misura iPhone 13, chiusa sia col tocco sulla maniglia sia trascinando):
  il tocco sul campo la riapre (83%), il tocco sulla maniglia mai. Su
  iPhone vero il campo non la apre: causa propria di Safari iOS, non
  riproducibile qui. Ipotesi non verificata: la tastiera che si apre
  sposta la pagina. **Deciso (Rachele, 2026-11-24, proposta di Lola):**
  card chiusa, tocco o trascinamento in su sulla maniglia la apre; card
  aperta, tocco o trascinamento in giù la chiude (come ora). Il campo
  su iPhone si riprova sul telefono dopo la correzione.
- Card aperta: **570 su 844 (circa 2/3), sempre** (apertura, maniglia,
  invio). Deciso da Rachele 2026-11-25: sostituisce i 698 di Figma (brief
  §5), perché lascia vedere l'inizio del primo progetto.
- Sfondo: video orizzontale 16:9 con `object-fit: cover` su schermo
  verticale: se ne vede circa un quarto della larghezza, ecco l'effetto
  ingrandito. Rachele (2026-11-24): resta così, punto 6 chiuso.
- Progetto aperto: barra (freccia + pills) a top 52 left 16, logo a top 56
  left 16 sopra di lei (z 20): il logo non si nasconde. Articolo:
  `width: 100%` più `left: 16` → esce di 16 px a destra (con width
  impostata, `right` viene ignorato). Causa diversa dal punto 31, ma
  stessa famiglia (misure responsive): Rachele li tiene insieme.

**Audit mobile eseguito (2026-11-25, commit 7a9bffc del Portfolio, in
locale, NON pubblicato):** punti 1, 3 e 4 fatti; il campo apre la card
anche al focus (per iPhone). Provato da Lola in Chrome a misura 390×844:
messaggi 1-3 fermi alla loro altezza finale, senza card dietro; card
entra al 4 (698 px); tag uno per riga, larghi quanto il testo; card
chiusa = solo barra e maniglia (152 px); tocco sulla maniglia apre e
chiude; trascinare in su apre, in giù chiude; focus sul campo apre.
Scatti: la card ora anima solo la sua altezza (prima riscriveva una
variabile a ogni frame, sospetto degli scatti).
**Non verificato:** l'animazione vera (il pannello browser di Lola è
nascosto e GSAP resta fermo), scatti su iPhone, campo su iPhone, tocco
su un tag a card aperta, conversazione lunga. Punto 7 resta col 31.
Aperto e non deciso: il tocco che salta l'apertura.
**Siguiente:** Rachele prova su iPhone (stessa wifi,
http://192.168.1.193:3000 col server acceso) e dà l'ok al push.

**Fatto (2026-11-23, sidebar):** ritocchi in commit 1344469 del Portfolio,
pubblicati (push 9d21e72..1344469, online verificato): "Proyectos" fisso (scorre solo la
lista, `.sidebar-list`), 12 tra le card, chip a 4, card `--vetro-campo`
come i messaggi, hover bianco pieno. Padding card 8/8/12 lasciato apposta
(Rachele ok). Limite noto: in pressed la card resta come in hover.

**Prompt diviso (2026-11-23, commit f1541a2 del Portfolio, in locale):**
`prompt/system_prompt.md` (84 KB) ora è 10 file numerati in `prompt/`
(01-chi-sei … 10-prenotazione-e-risposte-lunghe), stesse sezioni §1-18.
Il server (`readSystemPrompt`, `route.ts`) li cuce nell'ordine del numero:
testo identico byte per byte (verificato), build ok, tutti i file nel
pacchetto Vercel. Perché (Rachele): col file unico gli assistenti non
riuscivano a leggerlo tutto. Per la chat non cambia niente. Aggiornati
CLAUDE.md, brief e PRD del Portfolio. Prossimo sul prompt: punto 14
(risposte lunghe, §18), poi 21 (accorciare; candidato di Lola: texto
portfolio, ~10 KB). Push fatto con l'ok di Rachele (2026-11-23).
Provato online da Rachele con un messaggio vero: la chat risponde. Chiuso.

**Aperto (2026-11-23):** punti 4 (tag) e 34 (entrata a 5 messaggi) fatti
(commit 826d923 del Portfolio), pubblicati il 2026-11-23 insieme ad a415ccd
e 9d21e72 (ok di Rachele). Dettagli nella lista. Prossimo: Rachele guarda
online il ritmo dell'entrata e i due tag nei due ordini. Nuovo punto 35: comando vocale, da valutare.

**Aperto (2026-11-20):** punto 32 fatto e chiuso da Rachele (1,5 / 3,5 /
3,5 s, online in f1fa4df; se vorrà, lo ritocca più avanti). Punti 2 e 3
fatti in locale (a415ccd), più barra chiusa al 50% con "Ya no puedes
enviar mensajes" (9d21e72, sopra 826d923): Rachele li ha provati in locale
il 2026-11-23 e le vanno bene. Pubblicati tutti e tre (push c01c5e1..9d21e72,
2026-11-23, ok di Rachele anche per 826d923 dell'altra chat). Da provare
online: il solo tag attiva "Nueva conversación". Vercel ha saltato il push di 266a7bc (causa non vista:
serve il login di Rachele al pannello); il push dopo (6bbb870) è andato
online in 43 s. Se un push non arriva, prima cosa: pannello Deployments.

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
tagliata un po' nel riquadro 16:9: Rachele la guarda online. Push fatto
da Lola il 2026-11-17 (il login a GitHub funziona).
**Articolo Pillowtalk (2026-11-20, commit 37c32b3 del Portfolio,
online):** testo uguale al prompt; 5 video al loro posto, niente
foto finale. Originali da Drive in `Portfolio\pillowtalk` (01-05.mov),
nel sito versioni web 1280×720 senza audio né GPS in `public/pillowtalk/`
(0,3-1,4 MB). Il video 02 mostra varie sezioni di contenuto: descrizione
aggiornata nel prompt e in `articles.ts`. Provato online: 5 video
caricati, muti, in loop. Video dal telefono: Rachele li carica in
una cartella Drive condivisa col link, Lola li scarica.
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
**Punto 28 (2026-11-19), analisi fatta, codice non toccato:** il difetto
che resta (Rachele) è al messaggio 4: messaggi, tag e barra si scontrano
mentre compaiono. Causa (`page.tsx`, sequenza di apertura, solo desktop):
le posizioni dei messaggi sono fisse dal brief (y 460 durante 1-3, y 419
al 4), non calcolate sulle misure vere, e i messaggi si muovono due volte
(al 4 e poi di nuovo verso la posizione finale). Con le misure di prima
del 25-26 (posizione finale y 392) stavano 68 px più in basso, sopra lo
spazio di tag e barra: al 4 ci restavano sopra mentre comparivano. Con le
misure nuove (finale y 463) salgono di 41 px e poi riscendono di 44.
Decisione di Rachele: «Sì, correggi». Corretto in locale (page.tsx):
all'inizio i messaggi stanno più in basso di quanto misurano i tag
(fondo tag − fondo messaggi, oggi 46 px a 1440×900), al 4 salgono una
volta sola (1 s) e i tag compaiono dopo, a spazio libero. Tolte le
posizioni fisse 460/419. TypeScript ok; stato finale misurato ok.
L'animazione la guarda Rachele (il pannello di Lola non la fa girare).
Approvato da Rachele, online (commit b55c839), spostato in Punti fatti.
Prossimo: 29 prima in Figma.
**Punto 30 (2026-11-19):** le bolle della IA su desktop occupavano tutta
la colonna (nessuna larghezza massima; su mobile c'era già, 302 px).
Corretto in locale: `max-width: 80%` su `.bubble-ai` in `globals.css`,
come le bolle dell'utente (criterio di Lola). Misurato: 432 px su 540.
Approvato da Rachele, online (commit e6e6d31), spostato in Punti fatti.
**Nuovi punti (2026-11-19), scritti nella lista, non ancora guardati:**
31 applicazione non centrata (un po' a sinistra), 32 tempi delle
animazioni irregolari, 33 spazi strani intorno alla sidebar (con il 23.2).
Ordine proposto da Lola: 33 con 23.2, poi 31 (stesse misure di layout),
poi 32 (tempi, a parte). Ognuno in una sessione nuova.
**Punti 33 e 23.3 fatti (2026-11-19, commit 266a7bc del Portfolio):**
logo a 24; tolto il margine automatico sopra la caption (barra più in
basso, caption ferma); fondo della sidebar sempre allineato alla caption
(decisione di Rachele), con scorrimento interno. Approvati da Rachele
dallo screenshot. Vercel non ha pubblicato questo push; sono andati online
con il commit dopo (6bbb870), misurati online.
**Punti 29 e 31 fatti (2026-11-19, commit 6bbb870 del Portfolio), online
e misurati:** 29 etichette dei progetti neutre (#efe9eb / #6b5e64). 31 la
colonna chat si sposta tutta a destra perché i messaggi (432 su 540)
stiano al centro: a 1440 colonna a 504, messaggi 504 | 504; animazione
apri/chiudi progetto provata. Resta per gli schermi stretti (decisione di
Rachele: più avanti, con tablet e mobile): sotto ~1300 px, a progetto
aperto, la chat esce a destra (c'era già).
Prossimo nell'ordine proposto: punto 32.
Da approfondire più avanti (Rachele): nei prompt dire sempre di usare il
design system alla lettera e solo i token.
Font: in `Portfolio\tipografie` (copiati da `pillowtalk\`, dove erano).
Per lavorare sul codice serve la cartella Portfolio aperta nella sessione
(la sola `@` nel messaggio non basta).
Lista salvata in `miglioramenti-portfolio.md`: punti aperti in alto,
"Punti fatti" in fondo con il come (7, 9, 10, 15, 16, 19, 20, 22, 23.1, 23.3, 23.4, 23.5, 24, 25, 26, 27, 28, 29, 30, 31, 33).
Punto 17 fatto in un'altra chat (2026-11-20, commit 1ec5f62). Punto 18
(tono brusco) scartato da Rachele (2026-11-20): non si vede, tolto dalla
lista. Punto 21 (prompt più corto) necessario, ma più avanti.
Tolti anche 1 e 6 (articoli già con struttura e contenuti nuovi) e 11
(era il 23.3, fatto). Punto 3 deciso (2026-11-20): "Nueva conversación"
disattivato finché non c'è un messaggio o un tag; codice dopo il 32.
Punti 4 e 13: Rachele li guarda a casa, con calma.
Punto 2 deciso (2026-11-20): si toglie il gradino 4, la chat si chiude al
3 con `[[cierre]]`; prompt §9 e PRD §3.3 dopo il 32. Punto 5 in pausa.
**Mobile rotto (2026-11-20, aperto):** su iPhone di Rachele l'apertura non
si vede. Escluse: "Riduci movimento" (spento), risparmio energetico (succede
anche senza). Logo: rifatto 256×192, 39 kB (e784651, online) e ora gira da
solo. Resta: dopo il logo la card è a metà altezza (46%), vuota, sfondo
chiaro, e non si muove; un tocco fa apparire tutto. Quindi la sequenza
GSAP parte (la card prende il 46%) ma resta ferma all'inizio; il tocco la
porta alla fine (`skipOpening`, `page.tsx`:64). Succede anche in Safari.
**Causa trovata (misurata in Chrome a 390×664):** la sequenza non è ferma.
Con la card bassa (46%, poi 55%), tag e barra, ancora invisibili, occupano
già il loro spazio; ai messaggi restano 45 px, coperti tutti dalla
sfumatura in alto (`.chat-fade`). Il messaggio 1 sta sopra, fuori dalla
card. Tutto si vede solo quando la card sale piena (t4, ~10 s). Corretto
(39e4bf4 + c01c5e1, online, provato in locale a 390×664): messaggi 2-4, tag
e barra `display: none` finché non compaiono; durante l'apertura la card
abbraccia i messaggi (hug) e cresce con ognuno, a t4 altezza piena.
Intenzione (Rachele): far capire che la card si muove e che dietro c'è
qualcosa. Sfumatura in alto solo se c'è testo nascosto sopra (vale sempre,
non solo in apertura; non provata con una conversazione lunga). Da provare
su iPhone. Ancora da fare: tocco che non salta l'apertura su mobile.
**Prova su iPhone dopo c01c5e1: va tutto a scatti.** Rachele: ogni
correzione ne fa uscire altre 4, quindi il mobile si rifà in una
conversazione nuova, come **audit completo** (tutti gli errori prima,
poi le correzioni). Da portare all'audit: (1) a scatti, ipotesi di Lola non
verificata: la card cambia `--chat-card-height` a ogni fotogramma e tutta la
pagina si ricalcola (anche in `openChatCard`/`closeChatCard`); (2) un tocco
salta l'apertura; (3) sfumatura non provata in conversazione lunga; (4) i
video dei progetti chiedono play. Le prove in locale a misura iPhone (Chrome
headless) non vedono gli scatti: serve il telefono vero. Script di prova:
Chrome headless + CDP (`shot.mjs` nella scratchpad, non conservato).

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
- **2026-11-19 · Accento solo su ciò che si clicca** · Tag delle domande
  restano come sono (accento); etichette dei progetti neutre (#efe9eb,
  testo #6b5e64), stessa forma · Perché: le etichette sono informative, e
  l'accento dice "qui puoi fare qualcosa" · Intenzione: distinguere a
  colpo d'occhio cosa si clicca. Scartato: tag in primario (il primario è
  inviare), tag grigi come il secondario o il menu (non staccano).
- **2026-11-20 · La chat non risponde col sapere generale a nome di
  Rachele** (punto 17) · Tre casi: parole base del mestiere (frame,
  flujo…) si spiegano in una frase; tutto ciò che non è nel prompt
  (metodi, strumenti, cifre, leggi, opinioni) riceve una frase del §10
  ("Eso no te lo sé decir por aquí" o la CTA), mai "non l'ho fatto/non lo
  so"; curiosità fuori tema come ora · Perché: ogni risposta si legge come
  di Rachele, e il sapere del modello non è il suo · Intenzione: che chi
  scrive non legga mai qualcosa che Rachele non direbbe in un colloquio.
  Accettato: qualche caso limite (es. SAP) resta senza risposta. Nel §9
  del prompt, commit 1ec5f62 del Portfolio.
- **2026-11-20 · Apertura: primo messaggio corto e tempi per messaggio**
  (punto 32, solo la sequenza di apertura) · Il messaggio 1 diventa "Hola,
  soy Rachele." (via "Bueno, mi versión digital"). Pause dopo i messaggi:
  1 → 1,5 s (corto, attesa breve), 2 → 3,5 s (uguale), 3 → 3,5 s (era 3,
  fa comparire sidebar e titolo), 4 e tag non si toccano. Prima prova
  online con 0,5 e 4,5: per Rachele 1→2 troppo corto, 3→4 troppo lungo · Perché: il
  tempo va dove c'è da guardare, non dove il testo è lungo · Intenzione:
  ritmo dell'apertura che segue l'attenzione. Che è un'IA lo dice la
  caption sotto la barra. Commit 777018b e f1fa4df del Portfolio, online
  (controllati testo e pause nel codice pubblicato).

## Coda

1. ~~Finire il prototipo di Glovo~~ (fatto)
2. ~~Sistemare il prototipo di Pillowtalk~~ (fatto)
3. ~~Lista chiusa delle cose visive che non convincono~~ (fatto, Rachele)
4. Sistemare solo le cose della lista e pubblicare (Rachele e Lola). Quello
   che non è nella lista non si tocca in questo giro.
