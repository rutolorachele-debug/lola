---
titulo: Joyero — estado
tipo: estado
creado: 2026-11-21
actualizado: 2026-11-21
estado: ABIERTO
---

# Joyero · collezione di reference con link, per lavorare con le reference a mano

**Para qué existe** (2026-11-21): tenere in un solo posto le reference
(con il loro link) per lavorarci a mano. Obiettivo: farlo provare anche
ad altre persone, non solo a Rachele.

- En vivo / dónde se ve: https://joyero.vercel.app (ogni push su `main`
  si pubblica da solo)
- Código: https://github.com/rutolorachele-debug/joyero (pubblico).
  Cartella locale sul pc: da chiedere a Rachele
- Prodotto e stato «ufficiali»: documenti del progetto claude.ai «Joyero»
  (joyero-prodotto.md, joyero-stato.md), dice il CLAUDE.md del repo

## Com'è fatto oggi (letto dal repo, 2026-11-21)

- Web: Vite + Preact in `src/`, testi in spagnolo in `src/i18n/es.js`.
- «Database» = un Google Sheet nel Drive di ogni persona, più un Google
  Apps Script attaccato al Sheet (`apps-script/`). La web parla con lo
  script via POST con URL + chiave (il «codice», `src/lib/api.js`).
- Per entrare, ogni persona fa 6 passi a mano (tutorial, 5-10 min):
  copia il Sheet modello, apre Apps Script, fa «Nuova implementazione»,
  autorizza superando l'avviso «app non verificata», copia l'URL, genera
  il codice dal menù del Sheet e lo incolla nella web.
- Ogni modifica allo script va riapplicata a mano: oggi da Rachele, con
  altre persone da OGNUNA di loro (ognuna ha la sua copia dello script).
- Lo script legge anche i metadati delle pagine (titolo, ecc.) dai link:
  questo dal browser da solo non si può fare, serve un pezzo sul server.

## Dónde retomar (2026-11-21)

Letti repo e tutorial: il collo di bottiglia è il punto 3 (database).
Lola ha proposto la strada «accedi con Google» (vedi Cola 3).
Siguiente: Rachele sceglie la strada.

## Decisiones de este frente

- (nessuna ancora)

## Cola

1. ~~Link GitHub e Vercel~~ fatto (letti dal browser dell'app). Manca
   solo la cartella locale del codice, serve quando si lavora sul codice
2. ~~Lola guarda il codice~~ fatto, vedi «Com'è fatto oggi»
3. **Migliorare il collegamento al database** (nota di Rachele,
   2026-11-21): oggi è scomodissimo e non scala, quindi non può farlo
   provare ad altre persone. Intenzione: che altre persone possano usare
   Joyero senza che Rachele faccia passaggi a mano. Lola prima capisce
   com'è fatto oggi (passo 2), poi propone come cambiarlo; Rachele decide.
   Proposta di Lola (criterio suo, da verificare prima di costruire):
   **A · «Accedi con Google»** (consigliata): un bottone, la web crea da
   sola il Sheet nel Drive della persona e ci scrive direttamente.
   Niente script da copiare, niente codice, aggiornamenti per tutti con un
   push. I dati restano nel Drive di ognuno (la promessa del tutorial).
   Costo: un progetto Google Cloud da configurare una volta; i metadati
   dei link passano a una funzione su Vercel.
   **B · database vero** (es. Supabase) con login: scala di più, ma i dati
   non sono più nel Drive della persona, e cambia la promessa del prodotto.
   **C · tenere Apps Script** e ridurre i passi: resta scomodo e gli
   aggiornamenti restano a mano per ognuno. Sconsigliata.
4. Decidere con Rachele il primo lavoro da fare dopo la scelta
