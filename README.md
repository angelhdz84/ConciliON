# ⚖️ Concili_ON

**Motor de validación de ideas en 6 fases con 10 personalidades y score ponderado.**

Concili_ON evalúa cualquier idea de negocio, proyecto o startup usando un sistema multi-personalidad con pesos asimétricos. Cada personalidad representa un ángulo distinto del análisis, desde la visión de mercado hasta la viabilidad financiera, y emite un score ponderado que converge en un **Score Real** con penalizaciones por contradicciones detectadas.

---

## Cómo funciona

```
Idea → FASE 0 (Filtro Hermes) → 7 personalidades → scores → pesos → contradicciones → Score Real + veredicto → (opcional) Ariadna + (opcional) Segunda Opinión
```

### Las 10 personalidades

| Personalidad | Peso | Rol |
|---|---|---|
| **Prometeo** | 7% | Visionario — impacto, escalabilidad |
| **Atenea** | 15% | Risk Manager — riesgos críticos |
| **Hermes** | 7% | El Mensajero — claridad del concepto |
| **Midas** | 25% | El Cliente — disposición a pagar |
| **Eros** | 6% | Niño UX — fricción de uso |
| **Hefesto** | 15% | Ingeniero — viabilidad técnica |
| **Pluto** | 25% | Financiero — costos y ROI |
| **Ariadna** | — | Plan de Rescate (si score < 60%) |

### Las 6 fases

0. **Filtro Hermes** — Claridad mínima (detiene el análisis si es vaga)
1. **Análisis Inicial** — Prometeo, Atenea, Hermes
2. **Validación de Mercado** — Midas, Eros
3. **Evaluación Técnica y Financiera** — Hefesto, Pluto
4. **Decisión y Estrategia** — Zeus (score + polarización + contradicciones) + Odiseo (experimento)
5. 🧶 **Ariadna** — Plan de Rescate (solo si score < 60%)
6. **Consejo de Inversión** — Votación final de las 7 personalidades

---

## Output

Cada análisis genera una carpeta con el slug de la idea:

```
analisis/<slug-idea>/
├── <slug-idea>-concili-on.md     # Informe textual completo
├── <slug-idea>-concili-on.json   # Datos estructurados (scores, polarización, contradicciones)
└── <slug-idea>-concili-on.html   # HTML offline con gráficas (0 CDN, 0 dependencias)
```

### Ejemplo

```
analisis/offline-first-mipymes-latam/
├── offline-first-mipymes-latam-concili-on.md
├── offline-first-mipymes-latam-concili-on.json
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
