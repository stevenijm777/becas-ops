# Modo: pipeline — Procesar Becas Pendientes

Cuando el usuario tiene becas pendientes de evaluar en `data/pipeline.md`.

---

## Objetivo

Procesar el inbox de becas pendientes, evaluando cada una en orden de prioridad.

---

## Paso 1 — Leer el Pipeline

Lee `data/pipeline.md`. Si no existe o está vacío, notifica al usuario:
> "No hay becas pendientes en el pipeline. Puedes agregar becas con:
> - `/becas-ops {nombre o URL de beca}`
> - O agrégarlas manualmente a `data/pipeline.md`"

---

## Paso 2 — Mostrar el Inbox

Lista las becas pendientes con su prioridad sugerida:

| # | Beca/URL | Agregada | Prioridad Sugerida |
|---|----------|----------|--------------------|
| 1 | Chevening UK | 2026-05-20 | Alta (plazo próximo) |
| 2 | Erasmus Mundus Robotics | 2026-05-18 | Alta (beca completa) |
| 3 | OEA Fellowship | 2026-05-15 | Media |

Pregunta al usuario: "¿Quieres que evalúe todas en orden, o prefieres empezar con una específica?"

---

## Paso 3 — Evaluar en Orden

Para cada beca en el pipeline (en orden de prioridad):
1. Activa el modo `beca` con la información de esa entrada
2. Genera la evaluación completa (bloques A-E)
3. Registra en el tracker
4. Elimina la entrada del pipeline

Después de cada evaluación, pregunta: "¿Continúo con la siguiente o prefieres revisar esta primero?"

---

## Formato de `data/pipeline.md`

```markdown
# Pipeline de Becas — Pendientes de Evaluar

| # | Beca / URL | Fecha de Agregado | Notas |
|---|-----------|-------------------|-------|
| 1 | https://www.chevening.org/scholarships/ | 2026-05-20 | Beca completa UK |
| 2 | Erasmus Mundus Joint Master in Robotics | 2026-05-18 | |
```
