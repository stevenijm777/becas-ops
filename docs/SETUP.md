# becas-ops — Guía de Configuración

## Prerequisitos

Solo necesitas:
- Un AI coding CLI: [Claude Code](https://claude.ai/code), [Gemini CLI](https://github.com/google-gemini/gemini-cli), u OpenCode
- Git para clonar el repositorio

No se requiere Node.js, Python ni ninguna otra dependencia.

## Instalación

```bash
# 1. Clonar el repositorio
git clone https://github.com/stevenijm777/becas-ops.git
cd becas-ops

# 2. Crear tu perfil de postulante
cp config/profile.example.yml config/profile.yml
# Edita config/profile.yml con tus datos académicos

# 3. Crear tu CV en markdown
# Crea el archivo cv.md en el directorio raíz con tu CV completo
# Secciones recomendadas: Resumen, Educación, Experiencia, Proyectos, Habilidades, Certificaciones

# 4. Abrir con tu AI CLI
claude    # Claude Code
# o
gemini    # Gemini CLI
```

## Configurar tu Perfil (config/profile.yml)

Los campos más importantes:

```yaml
universidad:
  gpa: "8.9/10"  # Tu promedio real — incluye la escala

idiomas:
  - idioma: "Inglés"
    nivel: "B2"
    certificacion: "IELTS 7.0"  # La certificación exacta que tienes

documentos_disponibles:
  titulo_profesional: true/false
  certificacion_idioma: true/false
```

## Comandos Disponibles

Una vez que estés en tu AI CLI dentro del directorio becas-ops:

| Comando | Descripción |
|---------|-------------|
| `/becas-ops` | Muestra todos los comandos disponibles |
| `/becas-ops {nombre o URL}` | Evalúa una beca completa |
| `/becas-ops scan` | Escanea plazos abiertos en el catálogo |
| `/becas-ops match` | Ranking de becas por compatibilidad con tu perfil |
| `/becas-ops carta` | Genera carta de motivación |
| `/becas-ops checklist` | Checklist de documentos |
| `/becas-ops tracker` | Estado de tus aplicaciones |

## Agregar una Nueva Beca al Catálogo

```bash
# 1. Copia la plantilla
cp templates/beca-template.md becas/nombre-de-la-beca.md

# 2. Completa todos los campos del template

# 3. Abre un Pull Request en GitHub
```

## Estructura de Archivos Personales (Gitignoreados)

Estos archivos son tuyos y nunca se suben al repositorio:

| Archivo | Descripción |
|---------|-------------|
| `cv.md` | Tu CV en markdown |
| `config/profile.yml` | Tu perfil académico y preferencias |
| `modes/_profile.md` | Tu personalización del sistema |
| `data/applications.md` | Tu tracker de aplicaciones |
| `data/pipeline.md` | Tu inbox de becas pendientes |
| `reports/` | Tus reportes de evaluación |
| `output/` | Tus cartas y checklists generados |

## Preguntas Frecuentes

**¿Puedo usar este sistema si no soy de ESPOL?**
Sí. El catálogo de becas es universal. Algunos documentos en `modes/checklist.md` mencionan trámites de ESPOL — el agente los adaptará a tu universidad si le dices dónde estudias.

**¿El sistema envía mis aplicaciones automáticamente?**
No. El sistema genera documentos y recomienda acciones, pero **nunca envía nada sin tu revisión y aprobación**. Tú siempre tienes la última palabra.

**¿Cómo mantengo el catálogo actualizado?**
Los plazos cambian cada año. El comando `scan` verifica las fechas actuales usando WebSearch. También puedes actualizar los campos `deadline_next` en los archivos de `becas/` cuando confirmes un plazo.

**¿Puedo contribuir nuevas becas?**
¡Sí! Usa `templates/beca-template.md` como guía y abre un Pull Request.
