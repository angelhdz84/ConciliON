# Spec: Concili_ON Skill v2.2

**Versión:** 2.2
**Fecha:** 2026-07-07
**Skill:** `C:\Users\Angel\.agents\skills\concili-on\SKILL.md`

## Cambios respecto a v1

- **v2.3** — Emojis identificadores: cada personalidad tiene emoji único + rol + peso visible en outputs (.md/.html/.json). Tabla de identificación rápida en SKILL.md, AGENTS.md y toda salida. Prohibidos apodos no canónicos.
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

## Sistema de Identificadores Visuales (v2.3)

Cada personalidad tiene un identificador visual único (emoji) que debe aparecer en TODOS los outputs:

- **En .md**: `### 🔥 Prometeo (Visionario · 7%)` como header, y `🔥 Prometeo` en tablas y menciones.
- **En .html**: Mismo formato en barras, tarjetas y votación. Tooltip con `title="Nombre (Rol · Peso%) — frase clave"`.
- **En .json**: Los keys del objeto `consejo.detalle` incluyen emoji: `"🔥prometeo": "condicional"`.

### Reglas de uso

1. **Obligatorio:** Toda mención a una personalidad en outputs debe incluir su emoji.
2. **Obligatorio:** Toda mención debe incluir rol y peso: `🔥 Prometeo (Visionario · 7%)`.
3. **Prohibido:** Usar apodos fuera de la tabla canónica (Adán, Eva, Bruno, Ben, Tesla, Warren, Salomón).
4. **Consistencia:** Los identificadores deben ser idénticos en .md, .html y .json.
5. **Tooltips en HTML:** Cada personalidad en barras, council-vote y contradicciones debe tener title descriptivo.

### Mapa completo

| Emoji | Canonical | Rol | Peso | Antiguo (prohibido) | Frase recordatoria |
|---|---|---|---|---|---|
| 🔥 | Prometeo | Visionario | 7% | Adán | "Va a ganar porque..." |
| 🛡️ | Atenea | Risk Manager | 15% | Eva | "Esto puede salir mal si..." |
| 📢 | Hermes | El Mensajero | 7% | Bruno | "En cristiano: esto es..." |
| 💰 | Midas | El Cliente | 25% | — | "¿Yo pago por esto?" |
| 🧒 | Eros | Niño UX | 6% | Ben | "¿Lo usa un niño de 12?" |
| 🔧 | Hefesto | Ingeniero | 15% | Tesla | "¿Se puede construir?" |
| 📊 | Pluto | Financiero | 25% | Warren | "¿Cierra el número?" |
| ⚡ | Zeus | El Juez | — | — | "Chocaron, ¿quién gana?" |
| 🧭 | Odiseo | El Estratega | — | Salomón | "Probemos algo barato primero" |
| 🧶 | Ariadna | Plan de Rescate | — | — | Solo si score < 60% |

## Archivos del proyecto

| Archivo | Propósito |
|---|---|
| `AGENTS.md` | Instrucciones para el agente sobre la skill |
| `specs/concili-on-skill-v2.md` | Esta spec |
| `docs/manual_ConciliON.md` | Manual de usuario completo |
| `analisis/<slug>/` | Outputs de análisis |
| `.gitignore` | Exclusiones estándar |
