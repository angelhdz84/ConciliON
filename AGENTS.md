# Concili_ON — Reglas para el Agente

## Skill principal

La skill `concili-on` está en `C:\Users\Angel\.agents\skills\concili-on\SKILL.md`.
Debe activarse automáticamente cuando el usuario pida evaluar, validar o analizar una idea de negocio.

## Output obligatorio

Al finalizar cada análisis Concili_ON, el agente DEBE generar estos archivos:

```
analisis/<slug-idea>/
├── <slug-idea>-concili-on.md     # volcado textual completo del análisis
├── <slug-idea>-concili-on.json   # datos estructurados del análisis (scores, contradicciones, polarización)
└── <slug-idea>-concili-on.html   # HTML monolitico con gráficas (0 CDN, offline-ready)
```

### Reglas del HTML
- 0 dependencias externas (sin CDN, Google Fonts, ni librerías JS)
- Debe abrirse directamente desde el sistema de archivos sin servidor
- Dark theme, responsive (desktop + mobile)
- Incluir: gauge SVG del Score Real, barras de scores, waterfall de penalizaciones, tarjetas de contradicciones, índice de incertidumbre, Índice de Polarización, votación del consejo
- Color del gauge según rango: rojo <40%, naranja 40-59%, ámbar 60-79%, verde >=80%

### Carpeta
- `analisis/` en la raíz del proyecto
- Subcarpeta con slug en kebab-case (ej. `offline-first-mipymes-latam`)

## Referencia rápida de personalidades

| Personalidad | Peso | Rol |
|---|---|---|---|
| Prometeo | 7% | Visionario |
| Atenea | 15% | Risk Manager |
| Hermes | 7% | El Mensajero (claridad) |
| Midas | 25% | El Cliente |
| Eros | 6% | Niño UX |
| Hefesto | 15% | Ingeniero |
| Pluto | 25% | Financiero |
| Ariadna | — | Plan de Rescate (solo si score < 60%) |
