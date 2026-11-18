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

## 10. Cambio di progetto nella sidebar

- Quando si cambia progetto con le pills nella sidebar, devono sparire solo la copertina e l'articolo.
- La freccia di ritorno e le pills restano visibili.

---

## 11. Spaziature e sfumatura della chat

- La chat non rispetta gli spazi: in basso è molto alta e separata dalla frase sulla privacy. Da rivedere.
- In alto i messaggi devono uscire sfumando. La sfumatura parte dal margine della sidebar al 100% e finisce al margine dell'header al 0%.

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
4. Contorno viola: sulla barra di testo è tolto. Resta, voluto, sugli elementi raggiunti con la tastiera. Da verificare se compare ancora cliccando con il mouse su altri elementi.
5. Chat: aggiungere nella parte alta una sfumatura che fa sparire la chat all'altezza del logo. Vedi anche punto 11, dove la sfumatura parte dal margine della sidebar.

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
- [ ] Cambio di progetto nella sidebar: far sparire solo copertina e articolo, secondo il punto 10.
- [ ] Spaziature e sfumatura della chat: rivedere, secondo il punto 11.
- [ ] La chat apre un progetto su richiesta: marcatore nascosto, regola nel system prompt e risposta mentre apre, secondo il punto 13.
- [ ] Messaggi lunghi: verificare perché non vengono spezzati, secondo il punto 14.
- [ ] Domande fuori contesto con ricerca sul web: gestire nel system prompt §9 e testare, secondo il punto 17.
- [ ] Tono di voce troppo brusco: rivedere il system prompt e testare, secondo il punto 18.
- [ ] Ottimizzare il system prompt, che è molto lungo: valutare la riduzione, secondo il punto 21.
- [ ] Correzioni di layout e stato: spacing sidebar, spazio sotto la barra, contorno viola col mouse, sfumatura sotto il logo, secondo il punto 23.
- [ ] Formattazione degli articoli: dire quale progetto e quale paragrafo, poi confrontare con Figma, secondo il punto 6.
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

### 24. Link aggiornati dei prototipi

- Pillow Talk: https://otrorumbo-pillowtalk.vercel.app
- Glovo Duo: https://otrorumbo-glovoduo.vercel.app
- Da fare, nella sessione di build o nel PRD: sostituire i vecchi URL con questi due nuovi nel PRD §3.4, dove sono elencati i prototipi, e in ogni altro punto che li cita.
- I vecchi URL sono: https://glovo-duo.vercel.app/ e https://astounding-cajeta-04da12.netlify.app/#springboard.

**Fatto (2026-11-17):** i pulsanti "Abrir prototipo" del sito aprono i due link nuovi. Nel codice, nel PRD e negli altri documenti non resta nessun link vecchio. Online e controllato.
