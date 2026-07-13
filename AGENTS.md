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
- Light theme, responsive (desktop + mobile)
- Incluir: gauge SVG del Score Real, barras de scores, waterfall de penalizaciones, tarjetas de contradicciones, índice de incertidumbre, Índice de Polarización, votación del consejo
- Color del gauge según rango: rojo <40%, naranja 40-59%, ámbar 60-79%, verde >=80%

### Carpeta
- `analisis/` en la raíz del proyecto
- Subcarpeta con slug en kebab-case (ej. `offline-first-mipymes-latam`)

## Referencia rápida de personalidades

| Emoji | Personalidad | Peso | Rol | Frase recordatoria |
|---|---|---|---|---|
| 👁️ | **Adán** | 7% | Visionario | *"Va a ganar porque..."* |
| 🛡️ | **Eva** | 15% | Risk Manager | *"Esto puede salir mal si..."* |
| 📢 | **Hermes** | 7% | El Mensajero | *"En cristiano: esto es..."* |
| 💰 | **Midas** | 25% | El Cliente | *"¿Yo pago por esto?"* |
| 🧒 | **Loki** | 6% | Niño UX | *"¿Lo usa un niño de 12?"* |
| 🔧 | **Tesla** | 15% | Ingeniero | *"¿Se puede construir?"* |
| 📊 | **Dédalo** | 25% | Financiero | *"¿Cierra el número?"* |
| ⚡ | **Zeus** | — | El Juez | *"Chocaron, ¿quién gana?"* |
| 🧭 | **Odiseo** | — | El Estratega | *"Probemos algo barato primero"* |
| 🧶 | **Isis** | — | Plan de Rescate | Solo si Score < 60% |

**Reglas de formato en outputs:**
- Toda personalidad debe aparecer como `[emoji] [Nombre] (Rol · Peso%)`
- Ejemplo: `👁️ Adán (Visionario · 7%)`
- Prohibido usar apodos fuera de la tabla canónica
