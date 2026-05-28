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

1. Lee todos los archivos en `becas/` y el archivo `data/becas-espol.csv`.
2. Para cada beca del catálogo markdown y de la base de datos CSV, calcula un **score aproximado** (no requiere los 5 bloques completos — solo las dimensiones críticas):
   - **Nivel objetivo:** ¿El `tipo` (en CSV) o `nivel` (en markdown) coincide con los del perfil? (Maestría, Doctorado, etc.)
   - **Idioma:** ¿Cumple con los idiomas permitidos/requeridos? (Si el programa del CSV indica un país angloparlante o un programa internacional, asume inglés. Si el perfil tiene restricciones como `sin_idiomas` ej. japonés o chino mandarín, penaliza o filtra si el país de destino requiere ese idioma sin alternativas en inglés).
   - **GPA:** ¿Cumple con el GPA mínimo si está especificado?
   - **Área:** ¿El `area` de estudios encaja con las áreas de interés del perfil del estudiante (ej. robótica, computación, ingeniería, STEAM, IA, simulación)?
   - **País:** ¿El país coincide con las preferencias del estudiante?
   - **Restricción:** ¿Hay alguna restricción (como países excluidos o financiamiento mínimo) que elimine esta beca?

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
