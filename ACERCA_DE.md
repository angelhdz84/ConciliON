# Acerca de Concili_ON

**Versión:** 2.2
**Fecha:** 2026-07-07
**Autor:** Ángel Hernández

## ¿Qué es?

Concili_ON es un motor de validación de ideas de negocio que simula un consejo de 7 personalidades con score (más 3 roles analíticos: Zeus, Odiseo, Ariadna), cada una con un peso específico en la decisión final. No es una IA generativa opinando — es un sistema estructurado de puntuación con detección de contradicciones diseñado para separar la ilusión de la realidad.

## ¿Por qué existe?

Porque la mayoría de las validaciones de ideas son conversaciones sesgadas: el fundador solo escucha lo que quiere oír, el amigo dice "está genial", y el inversor dice "no" sin explicación. Concili_ON fuerza 7 ángulos distintos, pesos asimétricos (un financiero pesa 4× más que un visionario), y penaliza contradicciones internas del análisis.

## Filosofía

- **La realidad dura pesa más.** Pluto (25%), Midas (25%), Atenea (15%) y Hefesto (15%) suman el 80% del score. Prometeo (7%) puede soñar, pero no decide.
- **Sin datos no hay análisis.** La skill exige 4 campos antes de empezar. No evalúa sobre vacío.
- **Las contradicciones cuestan.** Si dos personalidades chocan severamente, la penalización puede llegar al -20% del score matemático.
- **Un veredicto no es el final.** Todo análisis incluye un experimento barato (Odiseo) para validar fuera del papel antes de construir.

## Skill

La skill principal está en:
```
C:\Users\Angel\.agents\skills\concili-on\SKILL.md
```

Se activa automáticamente cuando detects que necesitas evaluar una idea.

## Output

```
analisis/<slug>/
├── <slug>-concili-on.md      # Informe textual
├── <slug>-concili-on.json    # Datos estructurados
└── <slug>-concili-on.html    # HTML con gráficas offline
```

El HTML es autónomo: 0 CDN, 0 frameworks, 0 dependencias. Se abre directo desde el explorador de archivos. Incluye gauge SVG, barras de scores, waterfall de penalizaciones, tarjetas de contradicciones, índice de polarización y tally de votación.

## Personalidades

| Quién | Peso | Dice |
|---|---|---|---|
| **Prometeo** | 7% | "Esto va a ganar" |
| **Atenea** | 15% | "Esto va a fracasar porque..." |
| **Hermes** | 7% | "No entendí nada, explícalo simple" |
| **Midas** | 25% | "¿Yo pagaría por esto?" |
| **Eros** | 6% | "Muy complicado, no lo uso" |
| **Hefesto** | 15% | "Técnicamente imposible en 3 meses" |
| **Pluto** | 25% | "La cuenta no da" |
| **Ariadna** | — | "No está muerta, aquí está cómo mejorarla" |

## Changelog

### v2.2 (2026-07-07)
- **Panteón griego completo:** Adán→Prometeo, Eva→Atenea, Bruno→Hermes, Ben→Eros, Tesla→Hefesto, Warren→Pluto, Salomón→Odiseo
- **Nueva FASE 0:** Filtro Hermes — claridad mínima antes del análisis
- **Índice de Polarización:** Desviación estándar de scores
- **Ariadna progresiva:** Completa si < 40%, ligera si 40–59%
- **Loop Atenea→Ariadna:** Mitigaciones vinculadas a riesgos críticos
- **Export JSON:** Tercer archivo de salida
- **Modo Segunda Opinión:** Re-evaluación si polarización alta

### v2.1 (2026-07-07)
- Nueva personalidad: **Ariadna** 🧶 — Plan de Rescate (se activa si score < 60%)
- Bruno → **Hermes**, Ben → **Eros** (consistencia del panteón)
- Ariadna no vota, no tiene peso; solo diagnostica y prescribe mejoras

### v2.0 (2026-07-06)
- Nueva regla #6: generación automática de archivos `.md` + `.html`
- Nueva sección "Generación de Archivos de Salida" en la skill
- AGENTS.md con instrucciones rápidas
- Spec document en `specs/concili-on-skill-v2.md`
- HTML con 8 elementos visuales (gauge, barras, waterfall, etc.)
