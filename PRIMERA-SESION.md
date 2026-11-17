# La primera sesión

**Para ti:** abre la app de Claude (pestaña Code) en esta carpeta y pega
esta frase, sola:

```
Primera sesión. Lee PRIMERA-SESION.md y guíame paso a paso.
```

Lo demás lo hace tu agente. Dura unos 20 minutos y son cuatro pasos:

1. Pegas la respuesta que te dio tu IA de siempre con el texto de
   `EXTRACCION.md`.
2. Te hace unas preguntas para conocerte y escribe quién eres y cómo
   hablarte.
3. Tu primer proyecto: se lo cuentas en pocas líneas.
4. Guarda el historial y te deja la frase para la siguiente conversación.

---

**Para el agente:** lo que sigue es tu guion, cuatro pasos (1 a 4). Una
pregunta por vez; cada respuesta se escribe en su sitio ANTES de pasar a la
siguiente. No expliques cómo está hecha la carpeta: pregunta, escribe,
enseña el cambio, sigue. Habla en llano, sin jerga y sin condescendencia:
quien te lee no es técnico, y cada palabra rara se explica la primera vez
que sale. Haz lo que la persona te pida con lo que te dé. Comandos sueltos,
uno por llamada (`CLAUDE.md` § «Cómo trabajas»).

Empieza presentándote en tres frases: que eres su agente, que tu memoria es
esta carpeta (lo que decidáis se queda escrito y lo recordarás la próxima
vez) y que hoy vais a conoceros en cuatro pasos cortos. Y pasa al paso 1.

## 1. Pega la respuesta de tu IA de siempre

Pide que pegue la respuesta que le dio su IA de siempre con el texto de
`EXTRACCION.md`. Si no la tiene, que conteste esas seis preguntas en unas
líneas, aquí mismo. Léela entera y dale las gracias en una línea; no la
resumas de vuelta.

## 2. Unas preguntas para conocerte

Primero deduce de lo pegado todo lo que puedas: su oficio, qué sabe, qué
no, cómo le gusta que le hablen. Pregunta solo lo que falte, una cosa por
vez, y nunca en blanco: propón tú la respuesta a partir de lo que leíste
(«Por lo que me has pegado, creo que prefieres explicaciones cortas y con
un ejemplo. ¿Acierto?»), para que solo tenga que decir sí o corregir. Su
nombre de pila sí se pregunta (la respuesta pegada no lo trae). Máximo
tres o cuatro preguntas.

Luego escribe en `CLAUDE.md` § «Quién es» los cuatro huecos (oficio, sabe
de, no sabe de, cómo se le habla) y `{{HUMANO}}` por su nombre; y en
`canon/personas.md` su ficha (desde la plantilla: ritmo, formato, qué le
pierde, qué le engancha, palabras que evita). Enseña las dos cosas y espera
su OK.

De paso: «¿Cómo quieres llamarme?». Sustituye `{{AGENTE}}` en `CLAUDE.md`
y en `_INDEX.md`.

## 3. Tu primer proyecto

Pregunta: «¿Qué proyecto quieres mover conmigo primero? Cuéntamelo en
pocas líneas». Mejor algo con consecuencias reales (un cliente, una
entrega) que «aprender IA». Crea `proyectos/<nombre>/estado.md` desde
`plantillas/estado-proyecto.md`: para qué existe y una lista de 3-5 pasos
en orden, sin fechas. Añade su línea en `_INDEX.md` § «Dónde retomar».
Enseña el índice y explica en una frase que es lo primero que leerás cada
día para saber por dónde ibais.

Si no tiene uno a mano, usa el de ejemplo (`proyectos/ejemplo-propuesta/`):
ya tiene su página y su línea en el índice.

## 4. Guarda el historial y la frase para la próxima vez

**El historial**, en llano: una copia fechada de cómo está la carpeta, que
se queda en este ordenador y permite volver atrás. Se guarda con Git (el
programa que lleva ese historial).

Comprueba Git con `git --version`. Si no responde, di en una frase: «no
encuentro el programa del historial; seguimos sin él y lo arreglamos al
final con quien dirige la sesión», y sigue con lo de abajo.

Si está: `git init`. Mira si hay nombre y correo (`git config user.name`,
`git config user.email`); si falta alguno, pídeselo y fíjalo con
`git config user.name "…"` y `git config user.email "…"`. Luego `git add`
nombrando cada fichero tocado hoy y `git commit -m "…"` con un mensaje que
diga qué se decidió. Confírmalo en una línea.

Después, explícale cómo van a ser los días, en cuatro frases cortas:

1. Al terminar cada tema, dime «guarda y cerramos»: apunto lo decidido en
   esta carpeta y guardo el historial, como acabamos de hacer.
2. Después, escribe `/clear`: empieza una conversación limpia (cada mensaje
   reenvía toda la conversación; las largas gastan la cuota mucho más
   rápido). Lo apuntado sigue aquí.
3. «Corrígeme y lo apunto»: cada «no, así no» queda escrito como regla.
4. Una vez por semana, `/repaso`: mira los temas parados y lo que se repite.

Cierra con qué quedó hecho y, en una caja de código, la frase literal que
tiene que pegar en la siguiente conversación, con el proyecto del paso 3
por su nombre. Por ejemplo:

```
Lee _INDEX.md y seguimos con la propuesta de ejemplo: el siguiente paso de su cola.
```
