---
name: push-github-senza-gh
description: Login di Git a GitHub sul PC di Rachele: gestore di Git, niente GitHub CLI
metadata:
  type: reference
---

Sul computer di Rachele GitHub CLI non c'è più. Il 2026-11-17, con l'ok
di Rachele, ho tolto da `C:\Users\Rachele\.gitconfig` le righe che
facevano fare il login a GitHub con GitHub CLI. Adesso Git usa il suo
gestore di login (`manager`, installato con Git), quindi basta il normale
`git push`.

Il login è salvato: il 2026-11-17 Lola ha fatto `git push` da sola, senza
finestre. Quindi il push lo fa Lola (Rachele ha già dato l'ok a pubblicare
il portfolio).

Solo se il login va rifatto (errore di accesso), Rachele lancia `git push` dal suo terminale: si
apre il browser e accede lei. Se lo lancia Lola (Bash), la finestra di
login si chiude da sola.

Il Terminale di Windows c'è (lo ha detto Rachele): non dedurre che manca
solo perché `wt.exe` non si trova.
