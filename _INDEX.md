# Índice de Lola

Punto de entrada. Se lee al empezar CADA sesión, antes de buscar nada.

**≤ 10 KB.** Este fichero se lee en cada sesión: lo que deja de ser lo
último de su tema se mueve a su carpeta, y aquí queda una línea.

## Dónde retomar

UNA línea por tema (≤ 3 si hace falta), con enlace a su `estado.md`: dónde
estamos y el siguiente paso con quién. Lo demás vive en ese `estado.md`, no
aquí. Cada `estado.md` tiene su línea aquí, y cada línea apunta a un
`estado.md` que existe.

- **Portfolio Otrorumbo** — online; passi 1-3 fatti, ora le migliorie
  della lista (24 punti); prossimo: Rachele sceglie da dove partire
  (proposta: 18, 17, 16, 24) →
  [stato](proyectos/portfolio-otrorumbo/estado.md)
- **Propuesta de ejemplo** (ejemplo: bórralo cuando tengas el tuyo) — una
  propuesta para un cliente inventado; el resumen del encargo está hecho,
  falta el enfoque; siguiente: el enfoque (agente) →
  [estado](proyectos/ejemplo-propuesta/estado.md) ·
  [brief](proyectos/ejemplo-propuesta/brief.md)

## Mapa de la carpeta

| Área | Qué hay | Estado |
|---|---|---|
| `CLAUDE.md` | Quién es el agente, cómo trabaja y sus reglas | completo |
| `EMPEZAR.md` · `PRIMERA-SESION.md` · `EXTRACCION.md` | Cómo empezar, el guion de la primera sesión y las seis preguntas | listo |
| `canon/` | Decisiones tuyas: `decisiones.md` y `personas.md`. **Manda sobre todo** | ficha de Rachele + 2 decisiones |
| `proyectos/` | Una carpeta por tema con su `estado.md` (un tema = un `estado.md` = una cola); `ejemplo-propuesta/` es el de práctica | portfolio-otrorumbo + el ejemplo |
| `plantillas/` | El molde del `estado.md` de cada tema | listo |
| `GLOSARIO.md` | Palabras de la casa, en llano | 2 ejemplos |
| `memoria/` | La memoria del agente (`MEMORY.md` + una ficha por hecho) | 1 ficha |
| `.claude/` | Ajustes y `/repaso` (el agente no puede editarlo) | listo |
