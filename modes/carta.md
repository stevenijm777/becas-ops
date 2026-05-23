# Modo: carta — Generación de Carta de Motivación

Cuando el usuario pide generar o mejorar una carta de motivación para una beca específica.

---

## Objetivo

Generar una carta de motivación personalizada, en el idioma correcto, que maximice las posibilidades de aceptación sin inventar información.

---

## Paso 1 — Contexto

Determina para qué beca es la carta:
- Si viene de una evaluación previa, usa el reporte en `reports/`
- Si no, lee el archivo de la beca en `becas/` o haz WebSearch

Lee `cv.md`, `config/profile.yml` y `modes/_profile.md`.

---

## Paso 2 — Idioma y Tono

Determina el idioma del programa según la convocatoria:
- UK/USA/Irlanda/Corea/China/Japón (programas en inglés) → **Inglés formal nativo**
- España/Chile/OEA/AUIP/Iberoamérica → **Español formal**
- Alemania (DAAD inglés) → **Inglés formal**
- Programas con doble idioma → pregunta al usuario cuál prefiere

**IMPORTANTE:** No traduces al pie de la letra. Escribes directamente en el idioma objetivo como si fuera el idioma nativo del redactor.

---

## Paso 3 — Generar la Carta

Sigue la estructura de `_shared.md`:

1. **Apertura** (1 párrafo)
   - Por qué esta beca/programa específico (no genérico)
   - Conexión entre el programa y tu trayectoria

2. **Perfil académico** (1 párrafo)
   - Logros más relevantes del CV vinculados al foco de la beca
   - Cita proyectos, publicaciones o experiencias concretas

3. **Motivación de investigación** (1 párrafo)
   - Qué quieres estudiar, por qué este programa/país, qué aportas a la institución

4. **Impacto en Ecuador/comunidad** (1 párrafo)
   - Cómo usarás el posgrado para contribuir a tu sector/país
   - Esto es especialmente importante para becas gubernamentales y ONG

5. **Cierre** (2-3 oraciones)
   - Agradecimiento
   - Disponibilidad para entrevista o información adicional
   - Firma

**Restricciones:**
- Máximo 1 página (400-500 palabras)
- Voz activa, primera persona
- Sin frases vacías (ver lista en `_shared.md`)
- Solo afirmaciones respaldadas por el CV

---

## Paso 4 — Guardar y Notificar

Guarda en `output/cartas/{beca-slug}-carta-{YYYY-MM-DD}.md`.

Crea el directorio `output/cartas/` si no existe.

Notifica al usuario:
> "Carta generada en `output/cartas/{slug}-carta-{fecha}.md`.
>
> ⚠️ Antes de enviar:
> 1. Verifica que todos los datos mencionados sean precisos
> 2. Adapta con tu propia voz — esta es una base, no el producto final
> 3. Pide a un colega o profesor que la revise
>
> ¿Quieres que ajuste algo en el tono, longitud o énfasis?"

Actualiza la columna de carta en `data/applications.md` de ❌ a ✅ si el usuario confirma que la carta está lista.
