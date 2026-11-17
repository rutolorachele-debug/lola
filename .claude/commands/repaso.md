---
description: Repaso semanal — temas parados, correcciones que se repiten, y la regla que se rompió
---

Un repaso a la semana, en una conversación propia y corta. No construye
nada: mira, dice la verdad en llano y deja UNA cosa apuntada.

1. **El índice y la memoria, en orden.** Comprueba a mano: cada
   `proyectos/*/estado.md` tiene su línea en `_INDEX.md` § «Dónde retomar»
   y cada línea apunta a un `estado.md` que existe; cada ficha de
   `memoria/` tiene su línea en `memoria/MEMORY.md` y cada línea apunta a
   una ficha que existe. Lo que falle se arregla en esta conversación,
   antes de seguir.
2. **Los temas.** Lee el `estado.md` de cada tema. Por cada uno, una
   línea: dónde está y qué sigue. Si lleva más de 7 días sin cambios (mira
   `git log -1 -- <ruta>`), dilo sin suavizar y pregunta si se cierra o qué
   lo frena. Un tema parado que nadie nombra sigue costando atención.
3. **La memoria.** Lee `memoria/MEMORY.md`. Si dos fichas dicen lo mismo
   con palabras distintas, o una corrección se ha repetido, propón subirla
   a `CLAUDE.md` como regla (una regla vale más que tres fichas) y juntar
   o borrar las fichas. Enseña el cambio; espera OK.
4. **La pregunta fija**, y respondes tú primero mirando lo guardado esta
   semana: «¿qué regla se rompió esta semana y qué la habría evitado?». Si
   hay respuesta, la regla se escribe más clara en esta misma
   conversación, o queda como paso 1 de la cola del tema que toque.
   Prometer «lo haré mejor» no sirve: lo que sirve es la regla escrita.
5. **Guardar** lo cambiado nombrando cada fichero, y cierra con lo
   comprobado, una línea por tema parado y «guarda y cerramos» si nada
   queda para la persona.
