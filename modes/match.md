# Modo: match — ¿Para Qué Becas Califico Mejor?

Cuando el usuario pregunta "¿para qué becas califico?" o "¿cuáles son mis mejores opciones?".

---

## Objetivo

Evaluar el perfil del postulante contra todo el catálogo de becas y devolver un ranking de mejor a peor match, con justificación.

---

## Paso 1 — Leer Perfil

Lee `config/profile.yml` y `cv.md`. Extrae los factores clave de scoring:
- GPA y escala
- Certificaciones de idioma disponibles
- Nivel objetivo (maestría/doctorado)
- Área de estudios
- Experiencia laboral/investigación
- Documentos disponibles
- Restricciones (países excluidos, financiamiento mínimo, etc.)

---

## Paso 2 — Score Rápido para Cada Beca

Lee todos los archivos en `becas/`. Para cada beca, calcula un **score aproximado** (no requiere los 5 bloques completos — solo las dimensiones críticas):

- ¿El nivel objetivo coincide? (maestría/doctorado)
- ¿El idioma está certificado?
- ¿El GPA cumple el mínimo?
- ¿El área de estudios encaja?
- ¿Hay alguna restricción que elimine esta beca?

Asigna un score aproximado de 1-5.

---

## Paso 3 — Ranking

Presenta las becas ordenadas por score descendente:

### 🏆 Tus Mejores Opciones

| # | Beca | País | Score | Financiamiento | Deadline | Por qué eres buen candidato |
|---|------|------|-------|----------------|----------|-----------------------------|
| 1 | Chevening | UK | 4.6/5 | Completo | Ago-Nov | Idioma, área, experiencia encajan |
| 2 | DAAD-EPOS | Alemania | 4.2/5 | Completo | Variable | GPA fuerte, falta alemán |
| ... | | | | | | |

### ⚠️ Opciones Condicionales (necesitas fortalecer algo)

| Beca | Gap Principal | Cómo mitigarlo |
|------|--------------|----------------|
| MEXT (Japón) | Sin certificación de japonés | Cursos de idioma disponibles |

### ❌ No Recomendadas Actualmente

| Beca | Razón | ¿Podría aplicar en el futuro? |
|------|-------|-------------------------------|
| AGCID Chile | Requiere trabajo activo en sector público | Sí, si trabajas en academia |

---

## Paso 4 — Recomendación Final

Señala 2-3 becas priorizadas con razonamiento:

> "Basado en tu perfil, tu mejor apuesta es **[X]** porque [razón]. También considera **[Y]** que tiene menos competencia. Para el próximo ciclo, prepara **[Z]** — solo necesitas [acción específica]."

Pregunta al usuario si quiere evaluación completa de alguna beca del ranking.
