# Miglioramenti futuri: Otro Rumbo

Note raccolte durante il testing del portfolio. Non sono da fare adesso: si valutano dopo il test o nella fase giusta della build.

---

## 1. Immagini dei progetti

- Migliorare le immagini dei progetti Glovo Duo e Pillowtalk.
- Da dettagliare: quali immagini non convincono e perché (qualità, peso, ritaglio, formato, resa su mobile).
- Riferimento: fase 7 della build (articoli e immagini), PRD §3.4.

---

## 2. Chat chiusa dopo conversazione ostile: messaggio incoerente

**Cosa succede.** Quando si arriva al gradino 4 della scala ostile (PRD §3.3, system prompt §9), il pulsante di invio si disattiva, come previsto. Però l'ultimo messaggio di Rachele dice "Si tienes una pregunta sobre mi trabajo, aquí estoy", cioè invita a scrivere ancora, mentre il visitatore non può più farlo. L'unica strada è iniziare una nuova conversazione.

**Perché succede.** I due documenti dicono cose diverse:
- Il PRD §3.3 stabilisce che alla chiusura il pulsante si disattiva "with no extra message", cioè senza messaggi aggiuntivi.
- Il system prompt §9 impone il testo del gradino 4 alla lettera.

Il limite delle 30 domande invece ha già un messaggio esplicito nel PRD ("Empieza una nueva conversación o reserva una llamada"). Il caso ostile è l'unico senza una spiegazione chiara.

**Opzioni da decidere (non ancora scelte):**
1. Mostrare un avviso fisso quando l'invio è disattivato per ostilità, per esempio "Esta conversación está cerrada. Puedes empezar una nueva desde el menú." Richiede di modificare la regola "no extra message" del PRD §3.3.
2. Cambiare il testo del gradino 4 nel system prompt, così non invita a scrivere. È una scelta di Rachele, perché il testo è suo.
3. Lasciare tutto com'è, accettando la contraddizione.

**Nota.** Il messaggio del gradino 4 va cambiato solo da Rachele. Prima di toccarlo serve il suo via.

---

## 3. Pulsante "Nueva conversación" sempre attivo

**Cosa succede.** Il pulsante "Nueva conversación" nel menu è sempre attivo, anche prima di aver scritto un messaggio. Non è chiaro se la conversazione si riavvia senza chiedere conferma o se il pulsante non fa nulla. Non si capisce se il comportamento è corretto.

**Cosa dicono i documenti.**
- Il PRD §3.5 dice che, se la conversazione non è ancora iniziata, il riavvio avviene subito, senza dialogo. Altrimenti si apre il dialogo "¿Empezar una nueva conversación?".
- Il PRD §4.1 dice che la conversazione è iniziata quando il visitatore ha scritto un messaggio o usato un tag.
- Il PRD non dice che il pulsante debba essere disattivato quando la conversazione non è iniziata. Rachele lo vuole disattivo: va aggiunto al PRD §3.5.

**Da verificare nel test:**
1. Senza aver scritto né usato un tag, cliccare "Nueva conversación": deve tornare ai quattro messaggi senza dialogo.
2. Dopo un messaggio: deve comparire il dialogo di conferma.
3. Dopo aver usato solo un tag: deve comparire il dialogo, perché il tag avvia la conversazione.

**Da decidere:** disattivare il pulsante finché la conversazione non è iniziata (scelta di Rachele, da riportare nel PRD §3.5). In quel caso il riavvio senza dialogo non servirebbe più.

**Nota.** I messaggi che compaiono senza animazione sono previsti: l'animazione arriva nella fase 5 della build.

---

## 4. Tag: l'offerta dell'argomento già usato

**Cosa succede.** Il visitatore usa prima il tag "¿En qué estás trabajando ahora?", poi il tag "Cuéntame cómo piensas". Dopo la risposta al secondo tag, Rachele propone di nuovo "Si quieres, te cuento en qué estoy trabajando ahora", cioè l'argomento del primo tag, già usato.

**Cosa dicono i documenti.**
- PRD §4.2, scambio 3: se il visitatore sceglie il secondo tag, la risposta è quella preparata e la conversazione prosegue senza aggiungere nulla.
- system prompt §12: dopo il secondo argomento "nothing is added". L'offerta dell'altro argomento va fatta solo dopo il primo tag.

**Perché può succedere.** Il frontend sa quali tag sono stati usati, ma il modello lo deduce solo dal testo della conversazione. Può quindi proporre un argomento già usato. Il comportamento dipende dal modello e può non ripetersi sempre.

**Da verificare nei test:**
1. Tag "¿En qué estás trabajando ahora?", poi "Cuéntame cómo piensas": la risposta al secondo non deve contenere nessuna offerta.
2. Stesso test in ordine inverso: la risposta al secondo tag non deve contenere nessuna offerta.
3. Ripetere più volte ciascun caso, perché l'errore può comparire solo a volte.
4. Verificare che un solo tag usato porti l'offerta dell'altro tag.

**Possibili correzioni (da decidere):**
- Il frontend passa al modello quali tag sono già stati usati, così la risposta non propone l'argomento già usato.
- Chiarire nel system prompt §12 che l'offerta vale solo se l'altro tag è ancora disponibile. Questa modifica è di Rachele.

---

## 5. Pulsante "fammi un riassunto" accanto ai progetti

**Idea.** Un pulsante vicino ai progetti che chiede alla chat un riassunto del progetto ("fammi un riassunto"). Da precisare: dove sta esattamente (sidebar, card o articolo) e se il riassunto parte solo con il progetto aperto.

**Conflitti con i documenti da risolvere prima di costruirlo.**
- system prompt §14: il testo portfolio del progetto non va mai inviato, citato o parafrasato in chat. Un riassunto generato dalla chat, sullo stesso testo, rischia di violare questa regola. Serve chiarire se il riassunto deve venire dal testo descrizione (3-4 righe, già pensato per la chat) e non dal testo portfolio.
- PRD §3.1.1 e brief §4: aprire un progetto non manda nessun messaggio in chat, perché il progetto ha la sua sezione e un messaggio in più sovrastimola. Il pulsante invece invierebbe un messaggio. Va deciso se è accettabile.
- PRD §3.3: ogni messaggio conta per il limite delle 30 domande. Il riassunto conterebbe anche se è un pulsante.
- PRD §4.1: il pulsante farebbe partire la conversazione, quindi andrebbe considerato insieme alla regola dei tag.

**Decisioni prese da Rachele:**
- Il pulsante sta nella card del progetto, accanto a "apri prototipo".
- Il riassunto lo scrive Rachele, quindi non viene generato dalla chat. Il conflitto con il system prompt §14 non si pone più.
- Il pulsante non deve mandare messaggi in chat. La regola del PRD e del brief che lo vieta per l'apertura dei progetti è un residuo, da pulire nei documenti più avanti.

**Da decidere:**
1. Dove appare il riassunto: nella chat, in un overlay o nell'articolo.

---

## 6. Formattazione dei testi degli articoli

**Cosa succede.** Nei testi degli articoli dei progetti manca la formattazione. Esempio segnalato: il primo paragrafo.

**Cosa dicono i documenti.**
- La fase 3 chiede di copiare il "Texto portfolio" alla lettera, con i grassetti dove ci sono (system prompt §14).
- La fase 3 chiede anche di togliere la riga del titolo in grassetto prima di `[01]`, perché in Figma non c'è. Il primo paragrafo, "Proyecto: ...", è rimasto senza formattazione. Va verificato se in Figma quel paragrafo ha uno stile proprio.

**Da verificare:**
1. Quale progetto e quale paragrafo (il primo di Glovo Duo, di Pillowtalk o di entrambi).
2. Confrontare il testo sul sito con Figma, nella pagina "Design System e Schermate finali", per capire lo stile atteso.
3. Controllare che i grassetti e le sezioni del system prompt §14 arrivino nel sito.

---

## 8. Microinterazioni

- Rivedere le microinterazioni.

---

## 11. Spaziature e sfumatura della chat

- La chat non rispetta gli spazi: in basso è molto alta e separata dalla frase sulla privacy. Da rivedere.
- In alto i messaggi devono uscire sfumando. La sfumatura parte dal margine della sidebar al 100% e finisce al margine dell'header al 0%. **Fatto con il 23.5** (vedi Punti fatti). Resta aperta solo la prima riga, che è il 23.3.

---

## 13. La chat apre un progetto su richiesta

- Il visitatore scrive, per esempio, "voglio vedere il progetto di Glovo", e la chat apre il progetto.
- Serve un marcatore nascosto nella risposta, letto dal frontend, come `[[cierre]]`. Serve anche una regola nel system prompt che dica quando usarlo, scritta da Rachele.
- Da decidere: come deve rispondere la chat mentre apre il progetto.

---

## 14. Messaggi lunghi non spezzati

- Nei messaggi lunghi la chat non ha spezzato la risposta in più parti. Da verificare il perché.
- Riferimento: PRD §3.3 e brief §6, risposte spezzate con la riga `---`.

---

## 17. Domande fuori contesto con ricerca sul web (edge case)

- Un amico ha chiesto alla chat che cos'è un "flusso" e che cos'è una "pantaglia". La chat ha risposto cercando su internet.
- Rachele non vuole che la chat cerchi sul web per rispondere al posto suo: è un imbroglio, e se sbaglia sbaglia a suo nome.
- Da gestire come edge case nel system prompt (§9, Edge cases), scritto da Rachele.
- Da testare nei test futuri.

---

## 18. Tono di voce troppo brusco

- Alla domanda su come disegnare un'applicazione in Figma, la chat ha risposto: "io non disegno in Figma per nessuno, calmati". Il tono è stato percepito come aggressivo.
- Il tono deve restare sempre gentile, anche con domande dirette o provocatorie.
- Da rivedere nel system prompt (§6 e §9, scala ostile), perché la scala ostile non deve mai essere usata su domande normali.
- Rachele pensava che fosse già stato sistemato. Da verificare nei test futuri.

---

## 21. Ottimizzare il system prompt (è molto lungo)

- Il system prompt è molto lungo. Da valutare se e come ridurlo, senza perdere le regole che la chat deve rispettare.
- Nei documenti non è scritto un limite di lunghezza. Il brief (§6) dice solo che il costo dipende dalla lunghezza del prompt moltiplicata per i messaggi, e che il prompt caching serve a questo.
- Da rivedere insieme ai punti 17 e 18 (regole da aggiungere o correggere), perché ottimizzare non deve togliere le correzioni.

---

## 23. Correzioni di layout e stato

2. Sidebar: rivedere lo spacing, c'è qualcosa di strano.
3. Chat: rivedere lo spazio tra la barra per scrivere e la caption sotto, che è troppo ampio. Vedi anche punto 11.

### Misure fuori token nel codice (per 23.2 e 23.3)

Controllo di Lola del 2026-11-18, solo sul codice (Rachele: conta il codice, non Figma). File: `Portfolio/claude/app/globals.css`, la riga è dopo i due punti.

- **Scala che esiste:** spazi 2, 4, 6, 8, 10, 12, 16, 20, 24, 28, 32. Raggi 6, 8, 10, 12, 14, 16, 20, pill.
- **Proposta** = il token più vicino (criterio di Lola). Decide Rachele, valore per valore.

**23.2 · Sidebar e logo**

| Componente | Dove si vede | Codice | Ora | Proposta |
|---|---|---|---|---|
| Logo "otrorumbo" | home desktop, in alto a sinistra | :149 | sinistra 28, alto 30 | sinistra 24 (come la sidebar), alto 28 o 32 |
| Sidebar (riquadro progetti) | home desktop, distanza dall'alto | :156 | alto 80 | resta 80, ma con un nome unico ("inizio sotto il logo") |
| Sidebar, altezza massima | home desktop, margine in basso | :158 | schermo − 104 | 80 + 24: si calcola dal valore sopra |
| Logo mobile | home mobile, in alto | :190 | alto 56 | allineato al menu (52) |
| Lista progetti mobile | home mobile, spazio sopra le card | :196 | 108 | calcolato da logo + 24 |
| Lista progetti mobile | home mobile, spazio sotto l'ultima card | :201 | 180 | calcolato da altezza chat (152) + 28 |

- **La cosa strana più probabile:** il logo sta a 28 dal bordo, la sidebar a 24. Non sono allineati per 4 px.
- **Dentro la sidebar** (card, chips, titoli) le misure sono tutte già sui token.

**23.3 · Barra per scrivere e caption sotto**

| Componente | Dove si vede | Codice | Ora | Proposta |
|---|---|---|---|---|
| Gruppo barra + caption | chat, desktop e mobile | :458 | spazio 6 | sul token, ok |
| Caption privacy ("aviso") | chat desktop | :591 | sopra e sotto 8, lati 12 | sopra 0: la distanza dalla barra diventa 6 invece di 14 |
| Caption privacy | chat mobile | :607 | sopra e sotto 7, lati 10 | sopra 0, sotto 8 |
| Barra per scrivere | chat mobile | :606 | interno 7 | 8 |
| Card della chat | chat mobile, margine in basso | :217 | 24 | sul token, ok |

- **Su desktop tutto è già sui token:** lo spazio largo (6 + 8 = 14 px) è una somma di due token, non un errore di token. Va deciso quanto deve essere.

**Altre misure fuori scala (non legate a 23.2 e 23.3)**

| Componente | Dove si vede | Codice | Ora | Proposta |
|---|---|---|---|---|
| Bolle della chat (IA, tua, "sta scrivendo") e bolla della 404 | chat desktop, 404 | :463, :475, :507, :828 | interno 14 (`--s-14` usato ma non esiste) | aggiungere il token 14 (zero cambi visivi) oppure 12 o 16 |
| Chips delle domande | chat mobile | :605 | lati 14 | 16, come su desktop |
| Tab (pills di navigazione) | articolo | :344 | sopra e sotto 9 | 8 o 10 |
| Testo della slide | articolo desktop | :400 | sotto 22 | 24 o 20 |
| Testo della slide | articolo mobile | :414 | lati e sotto 18 | 16 o 20 |
| Logo su 404 e privacy | 404, privacy | :820, :857 | alto 29 | 28 |
| Card della chat, angoli | chat mobile | :214-215 | usa lo *spazio* 24 come raggio | raggio 20 (`--r-3xl`) o nuovo raggio 24 |
| Maniglia della chat, angoli | chat mobile | :242 | raggio 2 | pill |
| Barra di scorrimento, angoli | dove c'è scorrimento | :785 | raggio 2 | pill |
| Menu a tendina | home | :635 | alto 48 | 40 (pulsante) + 8 |

**Misure di layout, non da token (restano):** larghezza e posizione della chat (540, 450), pulsanti 40, pulsante invio 38 (unico diverso dagli altri 40), puntini 6, maniglia 120×24 e 36×4, larghezze massime (302, 540, 720), dialogo 355, menu 232, logo di caricamento 88 e 104, altezza card chat 152, sfumatura 80, margini grandi di 404 e privacy (80, 40).

---

## 27. Logo troppo grande durante il caricamento (2026-11-19)

- Il logo che si vede mentre la pagina carica è troppo grande: va rimpicciolito.

---

## 28. Dettagli dell'animazione di entrata (2026-11-19)

- L'animazione di entrata va bene, ma ci sono piccoli dettagli da rivedere. Quali, li dice Rachele.

---

## 29. Tag delle domande e chips dei progetti troppo uguali (2026-11-19)

- Le pills delle domande (tag in chat) e le etichette dei progetti sembrano lo stesso componente. Non va bene: devono essere diversi.
- Modifica grossa: da progettare in Figma prima del codice (criterio di Lola).

---

## 12. Effetto glass sulle pills della chat (per il futuro)

- Le pills della chat non hanno l'effetto glass. Da correggere.
- Non urgente (Rachele, 2026-11-18). Quando si riprende: con lo sfondo ora sfocato, la sfocatura dei componenti quasi non si vede. Il punto va riscritto con il riferimento Figma del vetro e l'elenco dei componenti a cui applicarlo.

---

## Da decidere

- [ ] Immagini dei progetti: raccogliere i dettagli e scegliere le versioni da sostituire.
- [ ] Chat chiusa: scegliere tra le opzioni 1, 2 o 3 del punto 2.
- [ ] "Nueva conversación": confermare se disattivare il pulsante finché la conversazione non inizia, e verificare i tre casi del punto 3.
- [ ] Tag: verificare più volte l'offerta dell'argomento già usato, nei due ordini, e scegliere la correzione del punto 4.
- [ ] Pulsante "fammi un riassunto": decidere dove appare il riassunto, secondo il punto 5.
- [ ] Microinterazioni: rivedere, secondo il punto 8.
- [ ] Spaziature e sfumatura della chat: rivedere, secondo il punto 11.
- [ ] La chat apre un progetto su richiesta: marcatore nascosto, regola nel system prompt e risposta mentre apre, secondo il punto 13.
- [ ] Messaggi lunghi: verificare perché non vengono spezzati, secondo il punto 14.
- [ ] Domande fuori contesto con ricerca sul web: gestire nel system prompt §9 e testare, secondo il punto 17.
- [ ] Tono di voce troppo brusco: rivedere il system prompt e testare, secondo il punto 18.
- [ ] Ottimizzare il system prompt, che è molto lungo: valutare la riduzione, secondo il punto 21.
- [ ] Correzioni di layout e stato: spacing sidebar, spazio sotto la barra, sfumatura sotto il logo, secondo il punto 23.
- [ ] Formattazione degli articoli: dire quale progetto e quale paragrafo, poi confrontare con Figma, secondo il punto 6.
- [ ] Testo dei messaggi: provare 14 px, secondo il punto 25.
- [ ] Chat più compatta: meno padding nei messaggi, secondo il punto 26.
- [ ] Logo di caricamento più piccolo, secondo il punto 27.
- [ ] Animazione di entrata: Rachele elenca i dettagli, secondo il punto 28.
- [ ] Tag delle domande diversi dalle chips dei progetti, secondo il punto 29.
- [ ] Per il futuro: effetto glass, da riscrivere con il riferimento Figma, secondo il punto 12.

---

## Punti fatti

Testo originale del punto, poi **Fatto:** come si è risolto.

---

### 7. Sfondo troppo pesante

- Lo sfondo della spiaggia è troppo pesante. Va applicata la sfocatura, come da richiesta di Rachele.
- Con lo sfondo generale completamente sfocato, la sfocatura va uniformata su tutti gli elementi che ne hanno una personalizzata, come la pagina 404.
- Lo sfondo della chat va reso totalmente sfocato. Ora ha troppo peso visivo, e Rachele non lo vuole.

**Fatto (2026-11-18):** home, privacy e 404 hanno lo stesso sfondo: il video della spiaggia già sfocato e schiarito nel file (`background-blur.mp4`), come la 404 in Figma (sfocatura 22, opacità 74%). La sfocatura è nel file e non nel browser, quindi non pesa; il video passa da 8 MB a 0,3 MB. L'animazione di apertura è uguale. La foto a parte della 404 è stata tolta. Approvato da Rachele, online e controllato.

---

### 9. Chips dei progetti a forma di pill

- Le chips che descrivono i progetti devono avere la forma di pill.

**Fatto (2026-11-17):** le chips dei progetti hanno gli angoli completamente arrotondati, a pill. Online e controllato.

---

### 10. Cambio di progetto nella sidebar

- Quando si cambia progetto con le pills nella sidebar, devono sparire solo la copertina e l'articolo.
- La freccia di ritorno e le pills restano visibili.

**Fatto (2026-11-18, commit 4a859e5 del Portfolio):** al cambio con le pills si muove solo l'articolo (copertina compresa); freccia, pills e "Abrir prototipo" restano ferme. L'articolo scorre di lato nella direzione della pill scelta (pill a destra: esce a sinistra ed entra da destra; e viceversa), di 32 px, con dissolvenza: esce in 0,3 s (accelera piano) ed entra in 0,45 s (frena morbida). Richiesta di Rachele: verticale e lento (0,6 + 0,6) non aveva senso per le tab; la prova a 0,2 + 0,3 s "faceva scatto". Alla prima apertura entra tutto il pannello, come prima. Codice: `handleChipSwitch` in `page.tsx`, l'entrata in `Projects.tsx`, i valori in `lib/motion.ts` (`MOTION.tab`). Provato su desktop e mobile; approvato da Rachele, online.

---

### 15. Contorno rosa sulla barra di testo

- Quando si seleziona la barra di testo per scrivere, compare un contorno rosa.
- Rachele non lo ha deciso e non lo vuole. Va rimosso o rivisto, da allineare alle indicazioni di Figma.

**Fatto (2026-11-17):** la barra di testo non ha più nessun contorno quando si clicca per scrivere. Il contorno resta solo sugli elementi raggiunti con la tastiera, per l'accessibilità (vedi punto 23.4, ancora aperto). Online e controllato.

---

### 16. Grassetto non renderizzato

- A volte il grassetto non viene letto e compare il doppio asterisco, per esempio `**parola**`, invece della parola in grassetto. Da verificare il perché.

**Fatto (2026-11-18):** la causa era che la chat mostrava il testo della IA così com'era. Decisione di Rachele: nella chat niente grassetto. Ora la chat toglie sempre il doppio asterisco e la parola resta normale; le email restano link. Una regola nel prompt per non usarlo è facoltativa e la scrive Rachele. Provato in locale e online con una risposta finta.

---

### 19. Barra di scorrimento visibile nella chat

- Nella chat si vede la barra per scorrere. Rachele non vuole che si veda.
- Lo scorrimento deve restare possibile, ma la barra deve essere nascosta.

**Fatto (2026-11-17):** la barra di scorrimento della chat è nascosta; si scorre come prima. Online e controllato. Insieme al punto 23.1.

---

### 20. Prototipi e storytelling dei progetti

1. Glovo Duo e Pillowtalk: pulire i prototipi e decidere lo storytelling, cioè cosa raccontare e cosa lasciare fuori. Prima Glovo Duo, che ne ha più bisogno.
2. Video: girarli solo quando i prototipi sono definitivi.

**Fatto (2026-11-17):** prototipi di Glovo Duo e Pillowtalk sistemati (lo ha confermato Rachele). L'articolo di Glovo è online con il testo del system prompt, 6 video e la foto finale. Pillowtalk: il testo è online; video e immagini arrivano quando Rachele manda i contenuti.

---

### 22. Cambio di logo e font

- Cambiare il logo con "Redaction".
- Cambiare il font dei testi con IBM Plex Sans.
- Dettagli nella mail di Rachele, da riportare qui quando serve. Da questa chat non posso leggere la mail.
- Sostituisce quanto scritto nel brief §5: Figtree per i testi e Funnel Display per il logo.

**Fatto (2026-11-17):** logo "otrorumbo" in Redaction 50 Italic, 24 px, colore accento, anche su 404 e privacy. Per i testi IBM Plex Sans è stato provato in Figma e scartato ("troppo serio"): al suo posto Funnel Sans, con testi Light, titoli dei progetti SemiBold, titoli di sezione e tag Medium, chips, pulsanti e sottotitoli Regular. Online e controllato.

---

### 23.1. Scrollbar della chat

1. Chat: togliere la scrollbar visibile. Lo scroll resta, ma non si deve vedere nessuna scrollbar. Vedi anche punto 19.

**Fatto (2026-11-17):** risolto insieme al punto 19.

---

### 23.4. Contorno viola cliccando con il mouse

4. Contorno viola: sulla barra di testo è tolto. Resta, voluto, sugli elementi raggiunti con la tastiera. Da verificare se compare ancora cliccando con il mouse su altri elementi.

**Fatto (2026-11-18):** sistemato da Rachele in un'altra chat. Nel codice il contorno viola compare solo quando si arriva a un elemento con la tastiera (`:focus-visible`), non con il clic del mouse; sulla barra di testo non compare mai. Verificato nel codice, non provato a mano.

---

### 23.5. Sfumatura in alto nella chat

5. Chat: aggiungere nella parte alta una sfumatura che fa sparire la chat all'altezza del logo. Vedi anche punto 11, dove la sfumatura parte dal margine della sidebar.

**Fatto (2026-11-18):** solo desktop, su mobile c'era già (`.chat-fade`). I messaggi sono pieni fino a 80 px dall'alto (inizio della sidebar) e spariscono a 30 px (inizio del logo): una maschera sulla chat in `globals.css` (`.chat-area`, blocco desktop), che vale qualunque sia l'altezza della chat. Copre anche la seconda riga del punto 11. Commit a6e33d2 del Portfolio; online e controllato con messaggi finti.

---

### 24. Link aggiornati dei prototipi

- Pillow Talk: https://otrorumbo-pillowtalk.vercel.app
- Glovo Duo: https://otrorumbo-glovoduo.vercel.app
- Da fare, nella sessione di build o nel PRD: sostituire i vecchi URL con questi due nuovi nel PRD §3.4, dove sono elencati i prototipi, e in ogni altro punto che li cita.
- I vecchi URL sono: https://glovo-duo.vercel.app/ e https://astounding-cajeta-04da12.netlify.app/#springboard.

**Fatto (2026-11-17):** i pulsanti "Abrir prototipo" del sito aprono i due link nuovi. Nel codice, nel PRD e negli altri documenti non resta nessun link vecchio. Online e controllato.

---

### 25. Testo dei messaggi troppo grande (2026-11-19)

- Il testo dei messaggi a 16 px sembra grande, sproporzionato rispetto ai testi dei progetti: gli stili di testo non sono in equilibrio tra loro.
- Ipotesi di Rachele: portare i messaggi a 14 px dovrebbe bastare. Da provare prima di decidere.

**Fatto (2026-11-19, commit 6bef29c del Portfolio):** messaggi della IA, dell'utente e "sta scrivendo" a 14 px con interlinea 1,5 (prima 16 px e 1,6), su desktop e mobile. Testo della barra a 14 px su desktop; su mobile resta a 16 px, perché sotto i 16 px l'iPhone ingrandisce la pagina quando si tocca il campo. In `globals.css`. Approvato da Rachele ("molto meglio"), online e controllato.

---

### 26. La chat occupa troppo spazio (2026-11-19)

- I riquadri che contengono i messaggi hanno un padding troppo grande.
- Nell'insieme la chat pesa troppo a livello visivo: deve occupare meno spazio. Va insieme al punto 25 (testo più piccolo, componenti più piccoli).

**Fatto (2026-11-19, commit 6bef29c del Portfolio):** padding dei messaggi: desktop 10/16 px (prima 14/20), mobile 8/12 (prima 12/16). Spazio tra i messaggi: desktop 8 px (prima 10), mobile 6 (prima 8). Barra di testo: desktop 8/8/8/16 px (prima 10/10/10/20, alta 54 px invece di 58), mobile 6/6/6/12 (prima 7, fuori token). Solo token. Online e controllato su desktop e mobile.
