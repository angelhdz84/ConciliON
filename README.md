# ⚖️ Concili_ON

**Motor de validación de ideas en 5 fases con 7 personalidades y score ponderado.**

Concili_ON evalúa cualquier idea de negocio, proyecto o startup usando un sistema multi-personalidad con pesos asimétricos. Cada personalidad representa un ángulo distinto del análisis, desde la visión de mercado hasta la viabilidad financiera, y emite un score ponderado que converge en un **Score Real** con penalizaciones por contradicciones detectadas.

---

## Cómo funciona

```
Idea → 7 personalidades → scores → pesos → contradicciones → Score Real + veredicto
```

### Las 7 personalidades

| Personalidad | Peso | Rol |
|---|---|---|
| **Adán** | 7% | Visionario — impacto, escalabilidad |
| **Eva** | 15% | Risk Manager — riesgos críticos |
| **Bruno** | 7% | El Lego — claridad del concepto |
| **Midas** | 25% | El Cliente — disposición a pagar |
| **Ben** | 6% | Niño UX — fricción de uso |
| **Tesla** | 15% | Ingeniero — viabilidad técnica |
| **Warren** | 25% | Financiero — costos y ROI |

### Las 5 fases

1. **Análisis Inicial** — Adán, Eva, Bruno
2. **Validación de Mercado** — Midas, Ben
3. **Evaluación Técnica y Financiera** — Tesla, Warren
4. **Decisión y Estrategia** — Zeus (contradicciones) + Salomón (experimento)
5. **Consejo de Inversión** — Votación final de las 7 personalidades

---

## Output

Cada análisis genera una carpeta con el slug de la idea:

```
analisis/<slug-idea>/
├── <slug-idea>-concili-on.md     # Informe textual completo
└── <slug-idea>-concili-on.html   # HTML offline con gráficas (0 CDN, 0 dependencias)
```

### Ejemplo

```
analisis/offline-first-mipymes-latam/
├── offline-first-mipymes-latam-concili-on.md
└── offline-first-mipymes-latam-concili-on.html
```

---

## Requisitos

- [OpenCode](https://opencode.ai) o Claude Code
- Skill `concili-on` instalada en `~/.agents/skills/concili-on/`

## Uso

Describe tu idea al agente. Si el agente detecta que necesitas una validación de negocio, activará Concili_ON automáticamente. Solo necesitas proporcionar:

1. **Problema** — ¿Qué problema real resuelve?
2. **Solución** — ¿Cuál es la solución concreta?
3. **Cliente objetivo** — ¿Quién paga por esto?
4. **Modelo de negocio** — ¿Cómo genera ingresos?

---

## Score Real

| Rango | Decisión |
|---|---|
| ≥ 80% | 🟢 APROBAR |
| 60–79% | 🟡 Aprobar con modificaciones |
| 40–59% | 🟠 Requiere pivote significativo |
| < 40% | 🔴 RECHAZAR |

---

## Stack

- Markdown + HTML monolitico (sin frameworks)
- CSS puro + SVG inline para gráficas
- 0 dependencias externas, 0 CDN, 100% offline

---

## Licencia

Uso interno — Ángel Hernández
