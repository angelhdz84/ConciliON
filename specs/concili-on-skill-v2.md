# Spec: Concili_ON Skill v2

**Versión:** 2.0
**Fecha:** 2026-07-06
**Skill:** `C:\Users\Angel\.agents\skills\concili-on\SKILL.md`

## Cambios respecto a v1

- Nueva **Regla #6**: Generación obligatoria de archivos de salida `.md` + `.html`
- Nueva sección **"Generación de Archivos de Salida"** al final del skill
- Nuevo archivo **`AGENTS.md`** en raíz del proyecto con resumen ejecutivo
- Nueva estructura de carpeta **`analisis/<slug-idea>/`**

## Output esperado

Cada ejecución de Concili_ON debe producir:

```
analisis/<slug-idea>/
├── <slug-idea>-concili-on.md      # Markdown plano, TODO el análisis
└── <slug-idea>-concili-on.html    # HTML offline con gráficas SVG/CSS
```

### HTML: Requisitos técnicos

1. **0 dependencias externas** — Sin CDN, Google Fonts, ni librerías JS
2. **Offline 100%** — Abrible desde filesystem sin servidor
3. **Responsive** — Desktop + mobile (media queries 768px y 480px)
4. **Dark theme** — Fondo #0c0d14, cards #151724, texto claro
5. **Gráficas obligatorias:**
   - Gauge SVG circular del Score Real (color por rango)
   - 7 barras horizontales de personalidades
   - Barras de contribución ponderada
   - Waterfall de penalizaciones
   - Tarjetas de contradicciones (crítica/importante/menor)
   - Índice de incertidumbre
   - Votación del consejo con tally
6. **Color por rango:** rojo <40%, naranja 40-59%, ámbar 60-79%, verde ≥80%
7. **Print-friendly** — `@media print`

## Personalidades y pesos

| Personalidad | Peso | Rol |
|---|---|---|
| Adán | 7% | Visionario |
| Eva | 15% | Risk Manager |
| Bruno | 7% | El Lego (claridad) |
| Midas | 25% | El Cliente |
| Ben | 6% | Niño UX |
| Tesla | 15% | Ingeniero |
| Warren | 25% | Financiero |

## Archivos del proyecto

| Archivo | Propósito |
|---|---|
| `AGENTS.md` | Instrucciones para el agente sobre la skill |
| `specs/concili-on-skill-v2.md` | Esta spec |
| `analisis/<slug>/` | Outputs de análisis |
| `.gitignore` | Exclusiones estándar |
