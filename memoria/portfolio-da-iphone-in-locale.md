---
name: portfolio-da-iphone-in-locale
description: Per aprire il Portfolio in locale dall'iPhone servono allowedDevOrigins e niente API solo-https; provarlo all'indirizzo di rete prima di darlo a Rachele
metadata:
  type: feedback
---

Il Portfolio in locale aperto dall'iPhone (http://192.168.1.193:3000) non
caricava (Rachele, 2026-11-25). Due cause:
1. Next.js blocca i file di sviluppo chiesti da un altro indirizzo:
   serve `allowedDevOrigins: ["192.168.1.193"]` in `next.config.ts`
   (fatto, commit e12a5b3) e riavviare il server.
2. In http non-localhost il browser non è "sicuro": `crypto.randomUUID` non
   esiste e la pagina si rompe. Ripiego aggiunto in `Chat.tsx`.

**Why:** avevo dato l'indirizzo provato solo su localhost.
**How to apply:** prima di dare a Rachele l'indirizzo di rete, aprirlo io
nel mio browser a quell'indirizzo e leggere il log del server. Se l'IP del
pc cambia, aggiornare `allowedDevOrigins`. Riavvio: fermare npm non basta,
il processo node resta vivo (va chiuso col suo PID).
