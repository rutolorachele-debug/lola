---
titulo: <Nombre del frente> — estado
tipo: estado
creado: AAAA-MM-DD
actualizado: AAAA-MM-DD
estado: ABIERTO | CERRADO (fecha y por qué)
---

# <Nombre del frente> · qué es en una frase

<!--
  Este fichero es la ÚNICA cola de este frente. Un frente = un estado.md = una
  cola. Cuando nace un plan nuevo del mismo frente, lo pendiente del anterior
  se muda aquí (o se cierra con decisión escrita) en el mismo commit. PORQUE
  con dos listas para el mismo frente, la petición que está en la lista que
  nadie mira se pierde, y se descubre tres días tarde.

  Tope: 10 KB. Se carga en cada sesión de este frente; lo que deja de ser lo
  último va a `historial/` (esta misma carpeta) y aquí queda una línea.

  Sin fechas propias: la cola va por dependencia (el paso 2 necesita el 1).
  Solo se citan las fechas que traen los stakes (un cliente que espera, un
  evento, un aviso de un tercero). Una fecha inventada por el agente no es un
  stake: se incumple sin consecuencia y solo mete ruido.
-->

**Para qué existe** (fecha): qué debe conseguir este frente, en dos frases.
Es lo que permite juzgar cada petición futura sin volver a preguntar.

- En vivo / dónde se ve: <dirección o «aún nada»>
- Código: <ruta dentro de este repo, o el repo aparte donde vive>

## Dónde retomar (fecha)

Tres líneas máximo: dónde estamos, qué queda, siguiente paso y con quién.
La misma línea, resumida, vive en `_INDEX.md` § «Dónde retomar».

## Decisiones de este frente

- **fecha · qué** — porqué · intención (qué debe conseguir). Las de empresa
  van además a `canon/decisiones.md`; aquí solo las que solo afectan a esto.

## Cola

1. <Paso, con su entregable y quién lo abre («decidir X» si lo abre el humano)>
2. <Paso que depende del 1>
3. …

<!-- Cerrado = «CERRADO (fecha): por qué» en el frontmatter y la cola vacía. -->
