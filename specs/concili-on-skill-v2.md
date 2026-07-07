# Spec: Concili_ON Skill v2.2

**Versión:** 2.2
**Fecha:** 2026-07-07
**Skill:** `C:\Users\Angel\.agents\skills\concili-on\SKILL.md`

## Cambios respecto a v1

- **Pantheon griego completo:** Adán→Prometeo, Eva→Atenea, Tesla→Hefesto, Warren→Pluto, Salomón→Odiseo
- Nueva **Regla #6**: Generación obligatoria de archivos de salida `.md` + `.json` + `.html`
- Nueva **FASE 0**: Filtro Hermes — claridad mínima
- **Índice de Polarización:** Desviación estándar entre los 7 scores
- **Ariadna progresiva:** Output completo (< 40%) o ligero (40–59%)
- **Mitigaciones Atenea→Ariadna:** Loop riesgos críticos
- **Modo Segunda Opinión:** Re-evaluación si polarización alta
- Nueva sección **"Generación de Archivos de Salida"** al final del skill
- **`AGENTS.md`** actualizado con tabla de personalidades y especificación de 3 outputs
- Nueva estructura de carpeta **`analisis/<slug-idea>/`**

## Output esperado

Cada ejecución de Concili_ON debe producir:

```
analisis/<slug-idea>/
├── <slug-idea>-concili-on.md      # Markdown plano, TODO el análisis
├── <slug-idea>-concili-on.json    # Datos estructurados (scores, polarización, contradicciones)
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
|---|---|---|---|
| Prometeo | 7% | Visionario |
| Atenea | 15% | Risk Manager |
| Hermes | 7% | El Mensajero (claridad) |
| Midas | 25% | El Cliente |
| Eros | 6% | Niño UX |
| Hefesto | 15% | Ingeniero |
| Pluto | 25% | Financiero |
| Ariadna | — | Plan de Rescate (si score < 60%) |

## Archivos del proyecto

| Archivo | Propósito |
|---|---|
| `AGENTS.md` | Instrucciones para el agente sobre la skill |
| `specs/concili-on-skill-v2.md` | Esta spec |
| `docs/manual_ConciliON.md` | Manual de usuario completo |
| `analisis/<slug>/` | Outputs de análisis |
| `.gitignore` | Exclusiones estándar |
