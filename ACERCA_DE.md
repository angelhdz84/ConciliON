# Acerca de Concili_ON

**Versión:** 2.0
**Fecha:** 2026-07-06
**Autor:** Ángel Hernández

## ¿Qué es?

Concili_ON es un motor de validación de ideas de negocio que simula un consejo de 7 personalidades, cada una con un peso específico en la decisión final. No es una IA generativa opinando — es un sistema estructurado de puntuación con detección de contradicciones diseñado para separar la ilusión de la realidad.

## ¿Por qué existe?

Porque la mayoría de las validaciones de ideas son conversaciones sesgadas: el fundador solo escucha lo que quiere oír, el amigo dice "está genial", y el inversor dice "no" sin explicación. Concili_ON fuerza 7 ángulos distintos, pesos asimétricos (un financiero pesa 4× más que un visionario), y penaliza contradicciones internas del análisis.

## Filosofía

- **La realidad dura pesa más.** Warren (25%), Midas (25%), Eva (15%) y Tesla (15%) suman el 80% del score. Adán (7%) puede soñar, pero no decide.
- **Sin datos no hay análisis.** La skill exige 4 campos antes de empezar. No evalúa sobre vacío.
- **Las contradicciones cuestan.** Si dos personalidades chocan severamente, la penalización puede llegar al -20% del score matemático.
- **Un veredicto no es el final.** Todo análisis incluye un experimento barato (Salomón) para validar fuera del papel antes de construir.

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
└── <slug>-concili-on.html    # HTML con gráficas offline
```

El HTML es autónomo: 0 CDN, 0 frameworks, 0 dependencias. Se abre directo desde el explorador de archivos. Incluye gauge SVG, barras de scores, waterfall de penalizaciones, tarjetas de contradicciones y tally de votación.

## Personalidades

| Quién | Peso | Dice |
|---|---|---|
| **Adán** | 7% | "Esto va a ganar" |
| **Eva** | 15% | "Esto va a fracasar porque..." |
| **Bruno** | 7% | "No entendí nada, explícalo simple" |
| **Midas** | 25% | "¿Yo pagaría por esto?" |
| **Ben** | 6% | "Muy complicado, no lo uso" |
| **Tesla** | 15% | "Técnicamente imposible en 3 meses" |
| **Warren** | 25% | "La cuenta no da" |

## Changelog

### v2.0 (2026-07-06)
- Nueva regla #6: generación automática de archivos `.md` + `.html`
- Nueva sección "Generación de Archivos de Salida" en la skill
- AGENTS.md con instrucciones rápidas
- Spec document en `specs/concili-on-skill-v2.md`
- HTML con 8 elementos visuales (gauge, barras, waterfall, etc.)
