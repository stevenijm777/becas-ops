# Modo: checklist — Checklist de Documentos

Cuando el usuario pide el checklist de documentos para una beca específica.

---

## Objetivo

Generar un checklist personalizado de documentos requeridos, indicando cuáles el postulante ya tiene disponibles y cómo obtener los que faltan (con énfasis en trámites de ESPOL cuando aplique).

---

## Paso 1 — Identificar la Beca

Determina para qué beca es el checklist:
- Busca en `becas/{slug}.md` o en `data/becas-espol.csv` (emparejando por nombre o del oferente)
- Si no está en el catálogo ni en el CSV, usa WebSearch para obtener los requisitos oficiales

Lee `config/profile.yml` para conocer qué documentos ya tiene disponibles.

---

## Paso 2 — Generar el Checklist

Crea una tabla con cada documento requerido:

| # | Documento | ¿Lo tienes? | Cómo obtenerlo | Tiempo estimado |
|---|-----------|-------------|----------------|-----------------|
| 1 | Pasaporte vigente | ✅ | — | — |
| 2 | Copia certificada del título | ❌ | Secretaría Técnica Académica ESPOL ($10) | 3-5 días hábiles |
| 3 | Certificado de calificaciones | ⚠️ | www.certificados.espol.edu.ec ($2) — pedir en inglés si el programa es en inglés | 2-3 días hábiles |
| 4 | Certificación de idioma (IELTS/TOEFL) | ❌ | CELEX ESPOL o centro certificado | 4-6 semanas (preparación + examen) |
| 5 | Cartas de recomendación (2-3) | ❌ | Solicitar a profesores del área relevante — dar 4-6 semanas de anticipación | 4-6 semanas |
| 6 | Carta de motivación | ❌ | Generar con `/becas-ops carta [nombre beca]` | 1-3 días (revisión propia) |
| 7 | CV actualizado | ✅ | `cv.md` — exportar a PDF si se requiere | 1 día |

**Leyenda:**
- ✅ Disponible
- ⚠️ Disponible pero necesita actualización/traducción
- ❌ No disponible — requiere acción

---

## Paso 3 — Resumen Crítico

### Documentos Críticos Faltantes (bloqueadores)

Lista solo los documentos sin los cuales NO puedes aplicar:

> "⚡ Acción inmediata requerida:
> 1. **Certificación de idioma** — Si no la tienes, este es el cuello de botella más largo (6+ semanas con preparación). Agenda el examen primero.
> 2. **[Otro crítico]** — ..."

### Documentos Logísticos (ESPOL)

Si el postulante es de ESPOL, incluir info específica:

| Trámite | Plataforma | Costo | Contacto |
|---------|-----------|-------|---------|
| Copia certificada del título | www.certificados.espol.edu.ec | USD 10 | — |
| Certificado de calificaciones | www.certificados.espol.edu.ec | USD 2 | — |
| Traducciones certificadas al inglés | CELEX ESPOL | Consultar | celex@espol.edu.ec |
| Apostilla | Coordinaciones Zonales Ecuador | Variable | — |

### Apostilla y Legalizaciones

Si la beca requiere documentos apostillados:
> "Los documentos apostillados se tramitan en las Coordinaciones Zonales del Ministerio de Relaciones Exteriores de Ecuador. La validación de títulos por Senescyt se realiza en su web. Si el programa es europeo, puede requerirse apostilla de La Haya."

---

## Paso 4 — Timeline de Preparación

Basado en el deadline de la beca y los tiempos de obtención de cada documento, sugiere un orden de acciones:

**[Semana X antes del deadline] → Iniciar certificación de idioma**  
**[Semana X-4] → Solicitar documentos académicos a ESPOL**  
**[Semana X-4] → Contactar profesores para cartas de recomendación**  
**[Semana X-2] → Redactar y revisar carta de motivación**  
**[Semana X-1] → Completar formulario de aplicación y subir documentos**

---

## Paso 5 — Guardar Checklist

Guarda en `output/checklists/{beca-slug}-checklist-{YYYY-MM-DD}.md`.
