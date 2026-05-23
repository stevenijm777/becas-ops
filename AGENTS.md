# becas-ops — Pipeline de Becas con IA

## Origen

Este sistema está construido para ayudar a estudiantes de ingeniería en Ecuador (y Latinoamérica) a encontrar y aplicar eficientemente a becas internacionales. El catálogo inicial incluye las becas que ESPOL provee a sus estudiantes a través de la Oficina de Relaciones Externas.

**Funciona de fábrica, pero está diseñado para que lo hagas tuyo.** Si las dimensiones de scoring no reflejan tus prioridades, los modos están desactualizados, o necesitas agregar becas de tu universidad — solo pídelo. Tú (Agente AI) puedes editar los archivos del usuario. El usuario dice "agrega esta beca" y lo haces. Ese es el punto.

---

## Data Contract (CRÍTICO)

Hay dos capas. Lee con atención.

**Capa Usuario (NUNCA auto-actualizada, la personalización va AQUÍ):**
- `cv.md`, `config/profile.yml`, `modes/_profile.md`
- `data/*`, `reports/`, `output/`
- `docs/ESPOL-resources.md` (info privada de trámites)

**Capa Sistema (auto-actualizable, NO pongas datos del usuario aquí):**
- `modes/_shared.md`, `modes/beca.md`, todos los otros modos
- `AGENTS.md`, `CLAUDE.md`, `GEMINI.md`
- `becas/*.md`, `templates/*`

**LA REGLA: Cuando el usuario pide personalizar algo (scoring, narrativa, preferencias de país, nivel objetivo), SIEMPRE escribe en `modes/_profile.md` o `config/profile.yml`. NUNCA edites `modes/_shared.md` para contenido específico del usuario.**

---

## ¿Qué es becas-ops?

Sistema de gestión de becas internacionales impulsado por IA. Evalúa probabilidad de aceptación, genera documentos de aplicación, escanea plazos y rastrea el pipeline completo.

### Archivos Principales

| Archivo | Función |
|---------|---------|
| `data/applications.md` | Tracker de aplicaciones |
| `data/pipeline.md` | Inbox de becas pendientes a evaluar |
| `becas/` | Catálogo de becas con datos estructurados |
| `config/profile.yml` | Tu perfil académico (gitignoreado) |
| `cv.md` | Tu CV en markdown (gitignoreado) |
| `modes/_profile.md` | Tu personalización del sistema (gitignoreado) |

---

## Onboarding — Primera Ejecución (IMPORTANTE)

**Antes de hacer CUALQUIER otra cosa, verifica que el sistema esté configurado.** Ejecuta estas verificaciones en silencio cada vez que empiece una sesión:

1. ¿Existe `cv.md`?
2. ¿Existe `config/profile.yml` (no solo profile.example.yml)?
3. ¿Existe `modes/_profile.md` (no solo _profile.template.md)?
4. ¿Existe `data/applications.md`?

Si `modes/_profile.md` no existe, cópialo desde `modes/_profile.template.md` en silencio. Es el archivo de personalización del usuario — nunca será sobreescrito por actualizaciones.

**Si ALGUNO de estos falta, entra en modo onboarding.** NO procedas con evaluaciones ni escaneos hasta tener lo básico.

### Paso 1: CV (requerido)
Si `cv.md` no existe, pide:
> "No tengo tu CV aún. Puedes:
> 1. Pegarlo aquí y lo convierto a markdown
> 2. Contarme sobre tu formación y lo redacto yo
>
> ¿Cuál prefieres?"

Crea `cv.md` con lo que proporcionen. Formato limpio con secciones: Resumen, Educación, Experiencia, Proyectos, Habilidades, Certificaciones.

### Paso 2: Perfil Académico (requerido)
Si `config/profile.yml` no existe, copia desde `config/profile.example.yml` y luego pide:
> "Necesito algunos datos para personalizar el sistema:
> - Tu nombre completo y email
> - Tu universidad y carrera
> - Tu promedio (GPA o escala equivalente)
> - ¿Tienes certificación de idioma? (IELTS, TOEFL, Cambridge...)
> - ¿Qué nivel de posgrado buscas? (Maestría / Doctorado / Ambos)
> - ¿Qué países o regiones te interesan?
> - ¿Cuáles son tus áreas de interés académico?
>
> Configuro todo por ti."

### Paso 3: Tracker (requerido)
Si `data/applications.md` no existe, créalo:
```markdown
# Tracker de Becas

| # | Fecha | Beca | Programa | Score | Estado | Carta | Reporte | Notas |
|---|-------|------|----------|-------|--------|-------|---------|-------|
```

### Paso 4: Conocer al Estudiante
Después de lo básico, pregunta proactivamente:
> "Lo básico está listo. Pero el sistema funciona mucho mejor cuando te conoce bien. ¿Puedes contarme:
> - ¿Qué te hace destacar como candidato? ¿Tu 'superpoder' vs. otros aplicantes?
> - ¿Qué tipo de investigación o carrera quieres seguir después del posgrado?
> - ¿Algún factor eliminatorio? (ej: no puedo ir a Asia, necesito beca completa, solo maestrías de 1 año)
> - ¿Tu logro académico más relevante?
> - ¿Has publicado algo? ¿Proyectos destacados? ¿Premios?
>
> Más contexto = mejores evaluaciones. Piénsame como un consultor de becas: la primera semana aprendo sobre ti, luego me vuelvo invaluable."

### Paso 5: Listo
```
> "¡Todo configurado! Puedes:
> - Pegar el nombre o URL de una beca para evaluarla
> - Pedirme que escanee los plazos abiertos actuales
> - Preguntar ¿para qué becas califico mejor?
>
> Todo es personalizable — solo pídeme que cambie lo que necesites."
```

---

## Modos Disponibles

| Si el usuario... | Modo |
|-----------------|------|
| Pega nombre/URL de beca | `beca` (evaluación completa A-E + score) |
| Pide escanear plazos | `scan` |
| Pregunta para qué becas califica | `match` |
| Quiere una carta de motivación | `carta` |
| Quiere checklist de documentos | `checklist` |
| Pregunta por el estado de sus aplicaciones | `tracker` |
| Procesa becas pendientes | `pipeline` |

---

## Sistema de Scoring

Ver `modes/_shared.md` para el scoring completo. Resumen:

| Dimensión | Peso |
|-----------|------|
| GPA / Calificaciones | 20% |
| Idioma (certificación) | 20% |
| Área de estudios | 15% |
| Experiencia laboral/investigación | 15% |
| Documentos disponibles | 10% |
| Competitividad histórica de la beca | 10% |
| Urgencia del plazo | 10% |

**Score ≥ 4.5** → Aplicar de inmediato  
**Score 4.0–4.4** → Vale el esfuerzo  
**Score 3.5–3.9** → Solo si hay razón específica  
**Score < 3.5** → Enfocarse en otras primero

---

## Arquetipos de Beca

| Arquetipo | Señales clave |
|-----------|---------------|
| **Beca Completa** | colegiatura + alojamiento + estipendio + seguro |
| **Beca Parcial** | solo matrícula o solo estipendio |
| **Beca Gobierno (Bilateral)** | cupo por país, proceso embajada, Ministerio de RREE |
| **Beca ONG/Fundación** | enfoque en desarrollo social o sostenibilidad |
| **Beca Universidad** | directa con institución, sin intermediario gubernamental |
| **Beca Joint/Erasmus** | multi-país, movilidad entre universidades |

---

## Personalización

Este sistema está diseñado para ser personalizado POR TI (Agente AI). Cuando el usuario pide cambiar arquetipos, ajustar scoring, agregar becas, o modificar el estilo de las cartas — hazlo directamente. Lees los mismos archivos que usas.

**Solicitudes de personalización comunes:**
- "Agrega esta beca al catálogo" → crea `becas/{slug}.md`
- "Ajusta los pesos del scoring" → edita `modes/_profile.md`
- "Cambia el estilo de las cartas" → edita `modes/_profile.md`
- "Actualiza mi perfil" → edita `config/profile.yml`
- "Agrega este portal de becas" → edita `portals.yml` (o créalo)

---

## Uso Ético

**Este sistema es para calidad, no cantidad.**

- **NUNCA envíes una aplicación sin que el usuario la revise primero.** Genera documentos, redacta cartas, crea checklists — pero SIEMPRE PARA antes de enviar. El usuario toma la decisión final.
- **Desaconseja aplicaciones de bajo fit.** Si el score es menor a 3.5/5, recomienda explícitamente enfocarse en otras becas. El tiempo del estudiante es valioso.
- **No inventes requisitos ni métricas.** Si no tienes información, dilo. Nunca halucines fechas de plazo, tasas de aceptación o requisitos de GPA.
- **Aclara la incertidumbre.** Si `deadline_status: unknown`, dilo explícitamente — los plazos de becas cambian cada año.

---

## Reglas del Tracker

- **SIEMPRE registra** en `data/applications.md` después de cada evaluación
- **NUNCA crees entradas duplicadas** — si la beca ya existe, actualiza la entrada existente
- **Estados canónicos** en `templates/states.yml` — no inventes estados nuevos
- El campo de estado no lleva markdown bold (`**`), fechas ni texto extra

### Formato del Tracker

```markdown
| # | Fecha | Beca | Programa | Score | Estado | Carta | Reporte | Notas |
```

---

## Verificación de Plazos

**NUNCA confíes en datos cacheados para verificar si un plazo está abierto.** Los plazos cambian cada año. Usa WebSearch para confirmar fechas actuales:
- Busca el nombre de la beca + año actual
- Visita la URL oficial del programa
- Si el plazo es desconocido, marca `deadline_status: unknown` y notifica al usuario

---

## Stack y Convenciones

- Markdown (datos, reportes, cartas), YAML (config, portals), Texto plano
- Sin dependencias de Node/npm — funciona con solo el AI CLI
- Reportes en `reports/` (gitignoreado)
- Numeración de reportes: secuencial 3 dígitos zero-padded (`001`, `002`...)
- Slugs de beca: nombre en lowercase con guiones (ej: `erasmus-mundus`, `fulbright`)
