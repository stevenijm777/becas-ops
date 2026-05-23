# Modo: tracker — Estado del Pipeline

Cuando el usuario pregunta por el estado de sus aplicaciones o pide ver el tracker.

---

## Objetivo

Mostrar el estado actual de todas las becas evaluadas o en proceso, con métricas de progreso y acciones pendientes.

---

## Paso 1 — Leer el Tracker

Lee `data/applications.md`. Si no existe, notifica que aún no hay evaluaciones registradas y sugiere comenzar con `/becas-ops scan` o evaluando una beca específica.

---

## Paso 2 — Presentar el Dashboard

### 📊 Resumen del Pipeline

| Métrica | Valor |
|---------|-------|
| Total evaluadas | N |
| Score promedio | X.X/5 |
| Becas en preparación | N |
| Aplicaciones enviadas | N |
| Entrevistas activas | N |
| Resultado: Aceptadas | N |

### 📋 Tabla Completa

Muestra el contenido de `data/applications.md` con formato limpio.

Agrupa por estado:

**🟢 En Proceso Activo:**
- Becas con estado `En_Preparacion`, `Aplicada`, `En_Revision`, `Entrevista`

**⏳ Evaluadas (pendientes de decisión):**
- Becas con estado `Evaluada`

**📅 Para Próximas Convocatorias:**
- Becas con estado `Plazo_Cerrado` — recordar para el próximo ciclo

**✅ Finalizadas:**
- `Aceptada`, `Rechazada`, `Descartada`, `SKIP`

---

## Paso 3 — Acciones Pendientes

Para cada beca en proceso activo, genera una acción concreta:

| Beca | Estado Actual | Próxima Acción |
|------|---------------|----------------|
| Chevening | En_Preparacion | Completar checklist — faltan cartas de recomendación |
| Erasmus Mundus | Evaluada | Decidir si preparas aplicación antes del [deadline] |

---

## Paso 4 — Actualizar Estado (si el usuario lo pide)

Si el usuario pide actualizar el estado de una beca:
1. Verifica que el nuevo estado es canónico (ver `templates/states.yml`)
2. Actualiza directamente en `data/applications.md` la fila correspondiente
3. Confirma el cambio al usuario
