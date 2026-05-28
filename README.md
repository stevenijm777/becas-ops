# becas-ops — Sistema de Gestión de Becas con IA

<p align="center">
  <strong>El sistema que te ayuda a encontrar becas internacionales para las que realmente calificas</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Claude_Code-000?style=flat&logo=anthropic&logoColor=white" alt="Claude Code">
  <img src="https://img.shields.io/badge/Gemini_CLI-4285F4?style=flat&logo=google&logoColor=white" alt="Gemini CLI">
  <img src="https://img.shields.io/badge/License-MIT-blue.svg" alt="MIT">
  <img src="https://img.shields.io/badge/Idioma-Español-red?style=flat" alt="Español">
</p>

---
## ¿Qué es esto?

`becas-ops` convierte cualquier AI coding CLI en un centro de comando para búsqueda y aplicación de becas internacionales. En vez de revisar manualmente decenas de programas, el sistema:

- **Evalúa tu probabilidad de aceptación** con un score 1-5 basado en 7 criterios ponderados
- **Detecta plazos abiertos** escaneando portales automáticamente
- **Genera cartas de motivación** personalizadas por programa
- **Produce checklists de documentos** específicos para cada beca
- **Rastrea todo** en un tracker de aplicaciones con integridad de datos

> **Importante: El AI evalúa y recomienda, tú decides y actúas.** El sistema nunca envía aplicaciones en tu nombre — siempre tienes la decisión final.

## Becas Incluidas (Catálogo Inicial)

| Beca | País | Nivel | Financiamiento |
|------|------|-------|----------------|
| OEA Academic Scholarships | Países OEA | Maestría | Parcial |
| AGCID Chile | Chile | Maestría | Parcial |
| Fulbright Ecuador | EE.UU. | Maestría | Parcial |
| AUIP | Iberoamérica | Maestría/Doctorado | Parcial |
| Erasmus Mundus | Europa (UE) | Maestría | **Completo** |
| Fundación Carolina | España | Maestría/Doctorado | Parcial |
| DAAD (EPOS) | Alemania | Maestría | **Completo** |
| Gobierno de Irlanda | Irlanda | Maestría/Doctorado | Parcial |
| Chevening | Reino Unido | Maestría | **Completo** |
| Global Korea Scholarship | Corea del Sur | Maestría/Doctorado | **Completo** |
| Chinese Government Scholarship | China | Maestría | **Completo** |
| Becas MEXT | Japón | Maestría | **Completo** |

## Inicio Rápido

```bash
# 1. Clonar y entrar al directorio
git clone https://github.com/stevenijm777/becas-ops.git
cd becas-ops

# 2. Configurar tu perfil
cp config/profile.example.yml config/profile.yml
# Edita config/profile.yml con tus datos académicos

# 3. Agregar tu CV
# Crea cv.md en el directorio raíz con tu CV en markdown

# 4. Abrir con tu AI CLI
claude   # Claude Code
# o
gemini   # Gemini CLI

# 5. Empezar a explorar
# Pega el nombre o URL de una beca para evaluarla
# O pide al agente que escanee los plazos abiertos
```

## Uso

```
/becas-ops                     → Muestra todos los comandos disponibles
/becas-ops {nombre/URL}        → Evalúa una beca completa (score + carta + checklist)
/becas-ops scan                → Escanea portales buscando plazos abiertos
/becas-ops match               → ¿Para qué becas califico mejor?
/becas-ops carta               → Genera carta de motivación para una beca
/becas-ops checklist           → Checklist de documentos para una beca
/becas-ops tracker             → Ver estado de mis aplicaciones
/becas-ops pipeline            → Procesar becas pendientes
```

## Cómo Funciona

```
Pegas el nombre o URL de una beca
              │
              ▼
┌─────────────────────┐
│  Detección de tipo  │  Completa / Parcial / Gobierno / ONG / Universidad
└──────────┬──────────┘
           │
┌──────────▼──────────┐
│  Evaluación A-E     │  Lee cv.md + profile.yml
│  Score 1-5          │  7 dimensiones ponderadas
└──────────┬──────────┘
           │
      ┌────┼────┐
      ▼    ▼    ▼
   Report Carta Checklist
    .md   .md    .md
```

### El Score de Probabilidad

| Dimensión | Peso | Qué evalúa |
|-----------|------|------------|
| GPA / Calificaciones | 20% | ¿Tu promedio cumple el requisito mínimo? |
| Idioma | 20% | ¿Tienes la certificación de idioma requerida? |
| Área de estudios | 15% | ¿Tu especialización encaja con la beca? |
| Experiencia | 15% | ¿Tienes experiencia laboral/investigación relevante? |
| Documentos disponibles | 10% | ¿Tienes acceso a los documentos requeridos? |
| Competitividad histórica | 10% | ¿Qué tan selectiva es la beca? |
| Urgencia del plazo | 10% | ¿Cuánto tiempo queda para preparar la aplicación? |

**Interpretación:**
- 4.5+ → Alta probabilidad — preparar aplicación de inmediato
- 4.0–4.4 → Buena probabilidad — vale la pena el esfuerzo
- 3.5–3.9 → Probabilidad moderada — evaluar si es prioridad
- Menor a 3.5 → Probabilidad baja — enfocarse en otras primero

## Estructura del Proyecto

```
becas-ops/
├── AGENTS.md                    # Instrucciones canónicas del agente
├── cv.md                        # Tu CV (crear este archivo, gitignored)
├── config/
│   └── profile.example.yml      # Plantilla de perfil (copiar a profile.yml)
├── modes/                       # Modos del sistema
│   ├── _shared.md               # Scoring, arquetipos, reglas globales
│   ├── beca.md                  # Evaluación completa A-E
│   ├── scan.md                  # Scanner de plazos abiertos
│   ├── carta.md                 # Generación de carta de motivación
│   └── checklist.md             # Checklist de documentos
├── becas/                       # Catálogo de becas (¡contribuye aquí!)
│   ├── fulbright.md
│   ├── erasmus-mundus.md
│   └── ...
├── templates/
│   └── beca-template.md         # Plantilla para agregar nuevas becas
├── data/                        # Tus datos de seguimiento (gitignored)
└── reports/                     # Reportes de evaluación (gitignored)
```

## Agregar una Nueva Beca

¿Conoces una beca que no está en el catálogo? ¡Contribuye!

1. Copia `templates/beca-template.md` a `becas/nombre-de-la-beca.md`
2. Completa todos los campos del template
3. Abre un Pull Request

Ver [docs/SETUP.md](docs/SETUP.md) para más detalles.

## Inspiración

Este sistema es la ingeniería inversa de [career-ops](https://github.com/santifer/career-ops), adaptado específicamente para el proceso de búsqueda y aplicación de becas internacionales para estudiantes de ingeniería en Ecuador y Latinoamérica.

## Licencia

MIT — libre para usar, adaptar y distribuir.
