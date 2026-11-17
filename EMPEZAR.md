# Empezar

Esta carpeta es tu agente: una inteligencia artificial que trabaja en tu
ordenador, dentro de esta carpeta, contigo mirando. Funciona con la **app
de escritorio de Claude**; no hace falta instalar nada más.

## Qué vas a tener

- **Un agente que recuerda.** Lo que decidáis queda escrito en esta
  carpeta y lo lee al empezar la siguiente conversación. No tienes que
  volver a explicarle quién eres ni en qué estás.
- **Un agente que apunta lo que le corriges.** Cada vez que le dices «no,
  así no», lo apunta como regla y la lee la próxima vez. Si repite un
  fallo, díselo: la regla se reescribe más clara.
- **Un tema por conversación.** Cada cosa que llevas (una propuesta, un
  cliente, un proyecto) tiene su página; el agente abre solo la que toca.

## Qué pasa con tus datos

- Lo que escribes y lo que el agente lee viaja a Anthropic (la empresa de
  Claude), como en cualquier chat con una IA.
- En la app, el ajuste de «ayudar a mejorar Claude» debe estar
  **apagado**: así tus conversaciones no se usan para entrenar.

## Antes de empezar: cómo trabajas (5 minutos)

Abre `EXTRACCION.md`, copia el texto de la caja con el botón de copiar y
pégalo en la IA que usas a diario (ChatGPT, Claude, Gemini…). Guarda la
respuesta: la pegarás en la primera sesión.

Si no usas ninguna, contesta tú las seis preguntas en unas líneas.

## Para arrancar

Abre la app de Claude, pestaña **Code**, elige esta carpeta y escribe,
sola, esta frase:

```
Primera sesión. Lee PRIMERA-SESION.md y guíame paso a paso.
```

Dura unos 20 minutos. Si la app te pide permiso para algo dentro de esta
carpeta, «Sí». Si nombra un fichero tuyo de fuera, «No», y pregúntale por
qué.

## Los días

- **Una conversación = un tema.** Empieza diciéndole en qué vas a
  trabajar; él abre su página.
- **Al acabar, «guarda y cerramos»** y luego `/clear` (empieza una
  conversación limpia; lo apuntado sigue en la carpeta). Cada mensaje
  reenvía la conversación entera: las largas gastan tu cuota mucho más
  rápido.
- **Una vez por semana, `/repaso`:** mira los temas parados y las
  correcciones que se repiten.
- **Si algo falla, dilo tal cual** («no ha guardado», «sigue igual»): no
  hace falta saber por qué.

---
Hecho a partir del agente de trabajo de Musho Studio · mushostudio.com. Compártelo con quien le sirva, con esta línea: así saben a quién preguntar.
