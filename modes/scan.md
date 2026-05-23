# Modo: scan — Escaneo de Plazos Abiertos

Cuando el usuario pide buscar becas abiertas o escanear convocatorias activas.

---

## Objetivo

Identificar qué becas del catálogo tienen plazos abiertos o próximos en el ciclo actual, y hacer match con el perfil del postulante.

---

## Paso 1 — Leer el Catálogo

Lee todos los archivos en `becas/`. Para cada beca, extrae:
- `deadline_typical` (mes típico de cierre)
- `deadline_status` (open / closed / estimated / unknown)
- `deadline_next` (si existe)

---

## Paso 2 — Verificar Plazos con WebSearch

Para cada beca con `deadline_status: estimated` o `unknown`:

Busca: `"[nombre beca] [año actual] convocatoria plazo postulación"`

Actualiza el estado basado en los resultados. Si encuentras plazo confirmado, anótalo como `open`. Si no hay resultados del ciclo actual, mantén `estimated` con el mes típico.

**Límite:** Verifica máximo 5-6 becas con WebSearch por sesión para no exceder el tiempo de respuesta.

---

## Paso 3 — Match Rápido con Perfil

Para las becas abiertas/próximas, haz un match rápido (sin evaluación completa):

Lee `config/profile.yml`. Para cada beca abierta, calcula si el postulante cumple los **requisitos mínimos obligatorios**:
- ¿Tiene título o está en vías de obtenerlo?
- ¿Tiene certificación de idioma requerida (o puede obtenerla)?
- ¿Su área de estudios califica?

Clasifica como: ✅ Apto / ⚠️ Apto con condiciones / ❌ No apto (bloqueador)

---

## Paso 4 — Presentar Resultados

### Becas con Plazo Abierto o Próximo

| Beca | Deadline | Estado | Financiamiento | Match Rápido |
|------|----------|--------|----------------|--------------|
| Chevening | Agosto-Nov 2026 | ⚠️ estimado | Completo | ✅ |
| DAAD-EPOS | [verificado] | ✅ abierto | Completo | ⚠️ |
| ... | ... | ... | ... | ... |

### Recomendación de Prioridad

Ordena las becas aptas por:
1. Score de match (mayor primero)
2. Urgencia del deadline (más próxima primero)
3. Calidad del financiamiento (completo > parcial)

---

## Paso 5 — Acciones Sugeridas

Para cada beca en la lista:
> "¿Quieres que evalúe [Chevening] en detalle? Te daré el score completo, la carta de motivación y el checklist de documentos."

Si el usuario dice que sí para alguna, activa el modo `beca`.
