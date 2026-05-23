# Modo: beca — Evaluación Completa A-E

Cuando el usuario pega el nombre, URL o texto de una beca, ejecutar SIEMPRE los 5 bloques completos (A-E).

---

## Paso 0 — Detección de Arquetipo y Recolección de Datos

Antes de los bloques:

1. **Identificar la beca:** Si es un nombre conocido, buscarla en `becas/`.  
   Si no está en el catálogo, usar WebSearch para obtener la convocatoria oficial.

2. **Clasificar el arquetipo** (ver `_shared.md`): Completa / Parcial / Gobierno Bilateral / ONG / Universidad / Joint-Erasmus.

3. **Verificar plazo:** Usa WebSearch con "[nombre de beca] [año actual] convocatoria plazo" para confirmar fechas.

4. **Leer perfil del postulante:** `cv.md` + `config/profile.yml` + `modes/_profile.md`.

---

## Bloque A — Resumen de la Beca

Tabla resumen con:

| Campo | Valor |
|-------|-------|
| **Arquetipo** | (detectado) |
| **Oferente** | Institución/gobierno que financia |
| **Programa objetivo** | Maestría / Doctorado / Ambos |
| **Área de estudios** | (específica o "todas las áreas") |
| **País de estudio** | |
| **Idioma del programa** | |
| **Financiamiento** | Completo / Parcial — rubros que cubre |
| **Deadline (este ciclo)** | fecha o `⚠️ estimado: [mes típico]` |
| **Deadline status** | open / closed / estimated / unknown |
| **URL oficial** | enlace directo |
| **TL;DR** | Una frase que resume la oportunidad |

Si el plazo no es `open`, agrega el disclaimer de incertidumbre (ver `_shared.md`).

---

## Bloque B — Match con Perfil

Lee `cv.md` y `config/profile.yml`. Crea tabla con cada requisito de la beca mapeado a evidencia concreta del perfil del postulante.

**Formato:**

| Requisito de la Beca | Nivel Requerido | Perfil del Postulante | ¿Cumple? |
|---------------------|----------------|----------------------|----------|
| Título profesional | Pregrado completo | BS Mecatrónica ESPOL 2025 | ✅ |
| GPA mínimo | ... | ... | ✅/⚠️/❌ |
| Certificación de idioma | ... | ... | ✅/⚠️/❌ |
| Experiencia laboral/investigación | ... | ... | ✅/⚠️/❌ |

**Leyenda:**
- ✅ Cumple claramente
- ⚠️ Cumple parcialmente / con observaciones
- ❌ No cumple (gap crítico)

**Sección de Gaps:** Para cada ❌ o ⚠️:
1. ¿Es un bloqueador eliminatorio o un deseable?
2. ¿Puede el postulante demostrar experiencia adyacente?
3. Plan de mitigación concreto (certif. en preparación, proyecto equivalente, etc.)

---

## Bloque C — Score de Probabilidad de Aceptación

Calcula el score siguiendo la fórmula de `_shared.md`. Para cada dimensión:

| Dimensión | Peso | Puntuación (1-5) | Justificación |
|-----------|------|-----------------|---------------|
| GPA / Calificaciones | 20% | ... | "GPA 8.9/10 vs. requisito ≥ 80%" |
| Idioma | 20% | ... | "Pearson B2 vs. IELTS/TOEFL requerido" |
| Área de estudios | 15% | ... | |
| Experiencia | 15% | ... | |
| Documentos disponibles | 10% | ... | |
| Competitividad histórica | 10% | ... | |
| Urgencia del plazo | 10% | ... | |
| **SCORE TOTAL** | **100%** | **X.X/5** | |

**Veredicto:**
- Score + interpretación (ver tabla en `_shared.md`)
- Recomendación explícita: **Aplicar / Aplicar si es prioridad / Evaluar / No recomendado**
- 1-2 factores que más impactan el score (positivos y negativos)

---

## Bloque D — Plan de Aplicación

### Timeline Recomendado

Basado en el deadline detectado, genera un cronograma inverso:

| Semana | Acción | Descripción |
|--------|--------|-------------|
| Ahora | Confirmar plazo | Verificar en URL oficial que el plazo está vigente |
| -8 sem | Documentos académicos | Solicitar certificado de calificaciones, copia de título |
| -6 sem | Certificación de idioma | Agendar examen si no tiene certificación |
| -4 sem | Cartas de recomendación | Contactar profesores/supervisores |
| -3 sem | Carta de motivación | Redactar y revisar (usar /becas-ops carta) |
| -2 sem | Revisión completa | Verificar todos los documentos del checklist |
| -1 sem | Envío anticipado | No dejar para el último día |

### Documentos Requeridos

Lista completa de documentos de la convocatoria, con indicador de disponibilidad del postulante (de `config/profile.yml`) y dónde obtenerlos si no los tiene.

---

## Bloque E — Borrador de Carta de Motivación

Genera un borrador completo de carta de motivación adaptado a:
- El idioma del programa (ver convocatoria)
- El arquetipo y foco de la beca (ONG → énfasis en impacto social; Completa → énfasis en excelencia académica)
- El perfil, CV y narrativa del postulante

**Estructura (ver reglas completas en `_shared.md`):**
1. Apertura — por qué esta beca/programa
2. Perfil académico — logros vinculados al foco
3. Motivación de investigación — qué y por qué
4. Impacto — contribución a comunidad/país
5. Cierre

Máximo 1 página (400-500 palabras). Voz activa. Sin frases vacías.

**Nota al usuario:** "Este es un borrador base. Revísalo y ajusta con tu voz antes de enviar."

---

## Post-Evaluación

**SIEMPRE** después de los bloques A-E:

### 1. Guardar reporte .md

Guardar en `reports/{###}-{beca-slug}-{YYYY-MM-DD}.md`.

- `{###}` = siguiente número secuencial (3 dígitos, zero-padded)
- `{beca-slug}` = nombre de la beca en lowercase con guiones
- `{YYYY-MM-DD}` = fecha actual

**Formato del reporte:**

```markdown
# Evaluación: {Nombre de la Beca}

**Fecha:** {YYYY-MM-DD}
**Arquetipo:** {detectado}
**Score:** {X.X/5}
**Deadline Status:** {open | closed | estimated | unknown}
**URL:** {URL oficial}

---

## A) Resumen de la Beca
(contenido completo del bloque A)

## B) Match con Perfil
(contenido completo del bloque B)

## C) Score de Probabilidad
(contenido completo del bloque C)

## D) Plan de Aplicación
(contenido completo del bloque D)

## E) Carta de Motivación (Borrador)
(contenido completo del bloque E)
```

### 2. Registrar en tracker

**SIEMPRE** registrar en `data/applications.md`:

```markdown
| {#} | {Fecha} | {Beca} | {Programa} | {Score}/5 | Evaluada | ❌ | [{###}](reports/{###}-{slug}-{fecha}.md) | {nota 1 línea} |
```

- Si la beca ya existe en el tracker, **actualiza** la entrada existente — no crees un duplicado
- La carta (columna 7) empieza en ❌ y cambia a ✅ cuando se genera la versión final
