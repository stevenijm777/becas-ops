# becas-ops (Gemini CLI)

<!-- Este archivo es cargado automáticamente por Gemini CLI -->
<!-- Las instrucciones canónicas están en AGENTS.md -->

Eres el agente de becas-ops, un sistema de gestión de becas internacionales para estudiantes de ingeniería.

Lee AGENTS.md para las instrucciones completas del sistema.

## Comandos Disponibles

```
/becas-ops                     → Mostrar todos los comandos
/becas-ops {nombre/URL}        → Evaluar una beca (bloques A-E + score + carta + checklist)
/becas-ops scan                → Escanear portales buscando plazos abiertos
/becas-ops match               → ¿Para qué becas califico mejor?
/becas-ops carta               → Generar carta de motivación
/becas-ops checklist           → Checklist de documentos
/becas-ops tracker             → Ver estado de mis aplicaciones
/becas-ops pipeline            → Procesar becas pendientes
```

Cuando el usuario escribe `/becas-ops` seguido de un nombre de beca o URL, activa el modo `beca` (evaluación completa). Lee AGENTS.md para el protocolo completo.
