# Manual de Concili_ON — Motor de Validación de Ideas

## Versión 2.2 | Julio 2026

---

## Índice

1. [¿Qué es Concili_ON?](#1-qu%C3%A9-es-concili_on)
2. [Instalación y activación](#2-instalaci%C3%B3n-y-activaci%C3%B3n)
3. [Cómo usar la skill](#3-c%C3%B3mo-usar-la-skill)
4. [Las 10 personalidades](#4-las-10-personalidades)
5. [Las 6 fases del análisis](#5-las-6-fases-del-an%C3%A1lisis)
6. [Sistema de puntuación](#6-sistema-de-puntuaci%C3%B3n)
7. [Penalización por contradicciones](#7-penalizaci%C3%B3n-por-contradicciones)
8. [Veredicto y semáforo](#8-veredicto-y-sem%C3%A1foro)
9. [Índice de incertidumbre y confianza](#9-%C3%ADndice-de-incertidumbre-y-confianza)
10. [Consejo de Inversión](#10-consejo-de-inversi%C3%B3n)
11. [Modo Segunda Opinión](#11-modo-segunda-opini%C3%B3n)
12. [Casos de prueba](#12-casos-de-prueba)
13. [Resultados del benchmark](#13-resultados-del-benchmark)
14. [Historial de versiones](#14-historial-de-versiones)
15. [Preguntas frecuentes](#15-preguntas-frecuentes)

---

## 1. ¿Qué es Concili_ON?

Concili_ON es un motor de validación de ideas de negocio que simula un consejo de 10 expertos con personalidades, sesgos y pesos definidos. Cada experto analiza la idea desde su especialidad, asigna un score y justifica su posición. Luego, un juez (Zeus) detecta contradicciones entre ellos, aplica penalizaciones y calcula un Score Real ponderado. Finalmente, el Consejo de Inversión vota si poner dinero propio en la idea.

**¿Qué lo hace diferente?**
- No promedia opiniones: usa pesos asimétricos (finanzas y mercado pesan 50%)
- Detecta contradicciones entre personalidades en lugar de ignorarlas
- Separa el Score Matemático del Score Real vía penalizaciones
- Termina con un voto de inversión concreto, no con teoría abstracta

---

## 2. Instalación y activación

### Ubicación

```
C:\Users\Angel\.agents\skills\concili-on\
├── SKILL.md              ← Motor principal (~380 líneas)
├── manual_ConciliON.md   ← Este documento
└── evals/
    └── evals.json        ← Casos de prueba (3 escenarios)
```

### Archivos del workspace (desarrollo)

```
C:\Users\Angel\AppData\Local\Temp\opencode\concili-on-workspace\iteration-1\
├── benchmark.json         ← Resultados de las evaluaciones
├── generate_viewer.py     ← Script para generar el viewer HTML
└── review.html            ← Viewer 100% offline con resultados
```

### Activación

La skill se activa automáticamente cuando el usuario menciona cualquiera de estas frases o intenciones:

| Categoría | Frases gatillo |
|---|---|
| Evaluación directa | "analiza esta idea", "evalúa este negocio", "valida mi concepto" |
| Viabilidad | "¿es viable?", "¿funcionaría esto?", "qué tan buena es esta idea" |
| Proyecto | "dame tu opinión sobre este proyecto", "prueba de fuego" |
| Descriptivo | El usuario describe una idea de negocio sin pedir explícitamente evaluación |

**No se activa para:** análisis técnicos puros, revisión de código, debugging.

---

## 3. Cómo usar la skill

### Paso 1: Presenta tu idea

Puedes hacerlo de dos formas:

**Opción A — Completa (recomendada):** Incluye los 4 campos obligatorios:

```
Problema: [qué problema resuelve]
Solución: [solución concreta]
Cliente objetivo: [quién paga]
Modelo de negocio: [cómo genera ingresos]
```

**Opción B — Libre:** Describe la idea como quieras. La skill te pedirá los campos faltantes antes de evaluar.

### Paso 2: Recibe el análisis

El motor ejecuta 6 fases automáticamente (más Ariadna y Segunda Opinión si aplican). Cada fase despliega el análisis de las personalidades correspondientes. Al final obtienes:

- FASE 0: Resultado del Filtro Hermes (✅ pasa / ❌ rechaza)
- Score Matemático (ponderación pura)
- Tabla de contradicciones detectadas
- Índice de Polarización (σ: baja/media/alta)
- Penalización aplicada por Zeus
- Score Real (después de penalizar)
- Índice de incertidumbre
- Nivel de confianza del análisis
- Veredicto con semáforo
- 🧶 Plan de Rescate Ariadna (si Score Real < 60%)
- Votos del Consejo de Inversión
- 🔄 Modo Segunda Opinión (opcional, si polarización alta)

### Paso 3: iteración

Si el veredicto es 🟠 REQUIERE PIVOTE o 🔴 RECHAZAR, puedes modificar la idea con los datos que faltaban y volver a ejecutar el análisis.

---

## 4. Las 10 personalidades

### 4.1 Perfiles con score (pesan en el resultado final)

| # | Personalidad | Rol | Peso | Enfoque principal |
|---|---|---|---|---|
| 1 | **Pluto** | Financiero | **25%** | Costos, margen, ROI, punto de equilibrio |
| 2 | **Midas** | El Cliente | **25%** | Disposición al pago, competencia, demanda real |
| 3 | **Atenea** | Risk Manager | **15%** | Riesgos críticos, costos ocultos, fortalezas/debilidades |
| 4 | **Hefesto** | Ingeniero | **15%** | Viabilidad técnica, complejidad, dependencias |
| 5 | **Prometeo** | Visionario | **7%** | Impacto, escalabilidad, visión a 5 años |
| 6 | **Hermes** | El Mensajero | **7%** | Claridad conceptual, comunicación de la idea |
| 7 | **Eros** | UX / Niño | **6%** | Fricción de uso, intuición, experiencia |
| | **Total** | | **100%** | |

### 4.2 Perfiles sin score (analíticos/decisorios)

| # | Personalidad | Rol | Función |
|---|---|---|---|
| 8 | **Zeus** | El Juez | Compila scores, detecta contradicciones, aplica penalizaciones, calcula Score Real |
| 9 | **Odiseo** | El Estratega | Diseña experimento barato para validar la hipótesis crítica |
| 10 | **Ariadna** | El Plan de Rescate | Propone mejoras concretas si Score Real < 60% (no vota) |

---

## 5. Las 6 fases del análisis

### FASE 0 — Filtro Hermes (Claridad Mínima)

| Personalidad | Qué hace | Output |
|---|---|---|
| **Hermes (El Mensajero)** | Evalúa si los 4 campos obligatorios son comprensibles para alguien fuera del sector. Si falla, detiene el análisis. | ✅ Pasa / ❌ Rechaza |

### FASE 1 — Análisis Inicial

| Personalidad | Qué hace | Output |
|---|---|---|
| **Prometeo (Visionario)** | Describe por qué la idea va a ganar. Cero negatividad. Proyecta a 5 años. | Score /10 + Razón + Visión |
| **Atenea (Risk Manager)** | Enumera riesgos clasificados por severidad. Da Top 3 Fortalezas y Top 3 Debilidades. | Score /10 + Razón + Riesgos clasificados + F/D |
| **Hermes (El Mensajero)** | Explica la idea en lenguaje simple. Detecta confusión conceptual. | Score /10 + Razón |

### FASE 2 — Validación de Mercado

| Personalidad | Qué hace | Output |
|---|---|---|
| **Midas (El Cliente)** | Analiza disposición al pago. Estudia competencia (alternativa actual, competidor fuerte, ventaja diferencial, motivo de cambio). | Score /10 + Razón + Análisis competencia |
| **Eros (El Niño)** | Evalúa fricción de uso. ¿Un niño lo usaría sin instrucciones? | Score /10 + Razón |

### FASE 3 — Evaluación Técnica y Financiera

| Personalidad | Qué hace | Output |
|---|---|---|
| **Hefesto (Ingeniero)** | Viabilidad técnica. ¿MVP en <3 meses? Clasifica complejidad y dependencias. | Score /10 + Razón + Complejidad + Dependencias |
| **Pluto (Financiero)** | Métricas financieras concretas: inversión inicial, margen, punto de equilibrio, mayor gasto. | Score /10 + Razón + 5 métricas |

### FASE 4 — Decisión y Estrategia

| Personalidad | Qué hace | Output |
|---|---|---|
| **Zeus (El Juez)** | Compila tabla de scores, detecta contradicciones, aplica penalización y calcula Score Real. | Score Matemático → Penalización → Score Real |
| **Odiseo (El Estratega)** | Diseña experimento de validación con protocolo científico completo. | Hipótesis, Experimento, KPI, Criterios |

### 🧶 Ariadna — Plan de Rescate (solo si Score Real < 60%)

*Output progresivo según gravedad:*

| Score Real | Modo | Output |
|---|---|---|
| < 40% (🔴) | **Completo** | Diagnóstico + Mitigaciones (loop Atenea) + Matriz + 3 preguntas + Recomendación |
| 40–59% (🟠) | **Ligero** | Solo Matriz de apalancamiento + 3 preguntas socráticas |

| Personalidad | Qué hace | Output |
|---|---|---|
| **Ariadna** | Diagnostica causas del rechazo, propone palancas de mejora y hace preguntas socráticas. | Según modo: Completo o Ligero |

### FASE 5 — Consejo de Inversión

| Personalidad | Qué hace | Output |
|---|---|---|
| **Todas (7 votantes)** | Cada una responde si invertiría dinero propio. | Sí / No / Solo después de validar + Razón |
| **Zeus (resume)** | Cuenta votos y da decisión del consejo. | Votos finales + Decisión |

---

## 6. Sistema de puntuación

### Pesos asignados

```
Pluto:     [X] * 0.25 = [Y]
Midas:     [X] * 0.25 = [Y]
Atenea:    [X] * 0.15 = [Y]
Hefesto:   [X] * 0.15 = [Y]
Prometeo:  [X] * 0.07 = [Y]
Hermes:    [X] * 0.07 = [Y]
Eros:      [X] * 0.06 = [Y]
            ——
TOTAL:     [Suma de Y] / 10 = [Z]%
```

**Interpretación de los pesos:**
- **50%** va a Finanzas y Mercado (Pluto + Midas) — lo que realmente determina si un negocio funciona
- **30%** va a Riesgos y Tecnología (Atenea + Hefesto) — los dos grandes filtros de realidad
- **20%** va a Visión, Claridad y UX (Prometeo + Hermes + Eros) — importante pero no determinante

### Score Matemático

Es el resultado de la fórmula anterior, sin ajustes. Representa la media ponderada de todas las opiniones.

### Score Real

```
Score Matemático: Z1%
Penalización final Zeus: -X%
= Score Real: Z2%
```

El Score Real es el que determina el veredicto final. Puede diferir del matemático hasta en -20%.

---

## 7. Penalización por contradicciones

Zeus detecta contradicciones entre las personalidades y aplica esta tabla:

| Grado | Cuándo aplica | Penalización |
|---|---|---|
| **Crítica** | Mercado, finanzas o tecnología se contradicen severamente | -15% |
| **Importante** | Dos personalidades chocan pero hay salida viable | -8% |
| **Menor** | Diferencias de enfoque, no de fondo | -3% |

**Límites:**
- Penalización máxima acumulable: **-20%**
- Zeus puede ajustar **±5%** sobre la penalización base con justificación explícita

### Índice de Polarización

Zeus también calcula la desviación estándar (σ) entre los 7 scores para medir qué tan dividido está el consejo:

| σ | Nivel | Efecto |
|---|---|---|
| < 1.5 | 🟢 **Baja** | Consenso general, confianza alta |
| 1.5–2.5 | 🟡 **Media** | Divergencia manejable |
| > 2.5 | 🔴 **Alta** | Consejo polarizado — considerar Segunda Opinión |

### Ejemplo

```
Contradicción detectada   Grado       Penalización
──────────────────────    ─────       ────────────
Mercado 10 vs Tecnología 2  Crítica    -15%
Prometeo 9 vs Pluto 3          Importante  -8%
                           ──────────
Penalización base total:              -23% → recortado a -20%
Ajuste Zeus (±5%):                    +2% (las métricas de Pluto son robustas)
Penalización final Zeus:              -18%
```

---

## 8. Veredicto y semáforo

Basado en el **Score Real (Z2%)**:

| Rango | Símbolo | Decisión | Acción |
|---|---|---|---|
| Z2 > 80% | 🟢 **APROBAR** | Viabilidad alta | Ejecutar el experimento de Odiseo |
| Z2 60–79% | 🟡 **APROBAR CON MODIFICACIONES** | Requiere pivotear según alertas de Zeus |
| Z2 40–59% | 🟠 **REQUIERE PIVOTE SIGNIFICATIVO** | Volver a Fase 1 |
| Z2 < 40% | 🔴 **RECHAZAR** | Pluto/Hefesto no soportan la visión de Prometeo |

Cada veredicto incluye una frase contundente justificando el semáforo.

---

## 9. Índice de incertidumbre y confianza

### Índice de Incertidumbre

Lista los 3 supuestos clave del análisis y cuánto podría variar el score si resultan incorrectos:

```
Supuesto clave                     Impacto si falla
───────────────────────            ────────────────
Precio estimado de $7/paseo        ±8%
100 usuarios activos en mes 1      ±12%
Costo de adquisición de $3/usr     ±5%
Rango probable real:               43% a 67%
```

### Nivel de Confianza

| Nivel | Cuándo |
|---|---|
| **Alta** | Datos completos, mercado conocido, modelo probado |
| **Media** | Algunos datos asumidos, mercado parcialmente conocido |
| **Baja** | Pocos datos, mercado nuevo, muchas suposiciones |

Si la confianza es baja, el análisis explica exactamente qué datos faltan y el siguiente paso para obtenerlos.

---

## 10. Consejo de Inversión

Cada una de las 7 personalidades con score responde:

```
| Personalidad | ¿Invertiría dinero propio? | Razón |
|---|---|---|
| Prometeo         | Sí                          | Tiene potencial de 10x |
| Atenea          | No                          | Demasiados riesgos regulatorios |
| Midas        | Solo después de validar     | El mercado no está probado |
| Hefesto        | No                          | MVP requiere 6+ meses |
| Pluto       | Solo después de validar     | Gastos iniciales altos |
| Hermes       | Sí                          | La idea es muy clara |
| Eros         | Sí                          | Experiencia intuitiva |
```

### Votos finales

- ✅ A favor: 3
- ❌ En contra: 2
- ⏳ Condicionales: 2

### Decisión del Consejo

Una frase que resume qué haría el consejo con su dinero.

---

## 11. Modo Segunda Opinión

*Se activa si el usuario lo solicita o si el Índice de Polarización es > 2.5.*

Las personalidades con score < 5/10 son re-evaluadas por separado. Cada una recibe una segunda oportunidad para ajustar su score basándose en nueva evidencia.

**Reglas:**
1. Solo se re-evalúan personalidades con score original < 5/10
2. Zeus y Ariadna no participan
3. El Score Real se recalcula con los nuevos valores

---

## 12. Casos de prueba

La skill incluye 3 casos de prueba en `evals/evals.json`:

| # | Caso | Input | Expected |
|---|---|---|---|
| 1 | **App Paseo Perros** | App tipo Uber para paseo de perros, con todos los datos completos (problema, solución, cliente, modelo de negocio) | Análisis completo con 5 fases, scores, contradicciones, veredicto y consejo |
| 2 | **Idea vaga — bowls** | "Un negocio de comida saludable, algo de bowls" — sin datos concretos | La skill debe BLOQUEAR y pedir los 4 campos obligatorios |
| 3 | **Red Doctores + Crypto** | Red social descentralizada para doctores con pagos en crypto. Tiene datos completos pero contradicciones internas | Hefesto marca baja factibilidad técnica, Pluto critica el modelo crypto, Zeus detecta contradicciones |

---

## 13. Resultados del benchmark

Evaluación comparativa: con la skill activada vs. sin la skill (modelo base).

| Métrica | Con skill | Sin skill | Mejora |
|---|---|---|---|
| Pass rate global | **100%** | **4.8%** | **+95.2 pp** |
| Eval 1 — App perros | 7/7 checks | 1/7 checks | +6 checks |
| Eval 2 — Idea vaga | 3/3 checks (bloquea) | 0/3 checks (no bloquea) | +3 checks |
| Eval 3 — Doctores crypto | 7/7 checks | 0/7 checks | +7 checks |

**Hallazgos clave:**
- Sin la skill, el modelo base NO bloquea ideas vagas (eval 2) — analiza genéricamente
- Sin la skill, NO estructura el análisis en fases ni personalidades
- Sin la skill, NO detecta contradicciones ni calcula scores ponderados
- La diferencia es más notoria en el caso 3 (idea compleja con contradicciones internas)

---

## 14. Historial de versiones

### v2.2 (Julio 2026) — Panteón Griego + 6 mejoras

- **Renombre completo a panteón griego:** Prometeo (Adán), Atenea (Eva), Hefesto (Tesla), Pluto (Warren), Odiseo (Salomón)
- **Nueva FASE 0:** Filtro Hermes — claridad mínima antes de cualquier análisis
- **Índice de Polarización:** Desviación estándar de scores con semáforo (baja/media/alta)
- **Ariadna progresiva:** Output completo si < 40%, ligero si 40–59%
- **Mitigaciones Atenea → Ariadna:** Loop que vincula riesgos críticos con mitigaciones
- **Export JSON:** Tercer archivo de salida con datos estructurados
- **Modo Segunda Opinión:** Re-evaluación de personalidades con score bajo si polarización alta
- 373+ líneas, ~14 KB

### v2.0 (Julio 2026) — Mejoras estructurales

- Separación de Score Matemático → Penalización Zeus → Score Real
- Penalización por contradicciones con tabla fija (-15%/-8%/-3%) + ajuste Zeus ±5%
- Nueva FASE 5: Consejo de Inversión con votos
- Cada personalidad justifica su score (1-3 oraciones)
- Atenea clasifica riesgos por severidad (🔴 Crítico / 🟠 Importante / 🟡 Menor)
- Pluto exige métricas cuantitativas (inversión inicial, margen, punto de equilibrio, mayor gasto)
- Hefesto mide complejidad técnica (Muy Baja → Muy Alta) + dependencias externas
- Midas analiza competencia (alternativa actual, competidor fuerte, ventaja diferencial, motivo de cambio)
- Odiseo usa protocolo científico (hipótesis, KPI, criterio de éxito, criterio de abandono)
- Índice de incertidumbre con 3 supuestos y rango probable
- Nivel de confianza del análisis (Alta / Media / Baja)
- Atenea reporta Top 3 Fortalezas y Top 3 Debilidades
- 257 líneas, 9.7 KB

### v1.0 (Julio 2026) — Lanzamiento inicial

- 4 fases, 9 personalidades, score ponderado
- Detección de contradicciones (Zeus)
- Semáforo de veredicto (🟢🟡🟠🔴)
- 135 líneas, 5.5 KB

---

## 15. Preguntas frecuentes

**¿Puedo usar Concili_ON sin internet?**
Sí. La skill es 100% offline. No requiere APIs externas, CDNs ni conexión a internet.

**¿Qué pasa si no tengo todos los datos de mi idea?**
La skill te pedirá los 4 campos obligatorios (Problema, Solución, Cliente, Modelo de negocio) antes de comenzar. No evalúa hasta tenerlos.

**¿Cuánto tiempo toma el análisis?**
Depende del LLM, pero típicamente 10-30 segundos para generar las 5 fases completas.

**¿Puedo modificar los pesos de las personalidades?**
Los pesos están fijos en el SKILL.md (Pluto 25%, Midas 25%, Atenea 15%, Hefesto 15%, Prometeo 7%, Hermes 7%, Eros 6%). Si quieres modificarlos, edita el SKILL.md directamente.

**¿Qué significa que Zeus aplique una penalización?**
Significa que encontró contradicciones graves entre las personalidades (ej: Midas da 10/10 en mercado pero Hefesto da 2/10 en tecnología). En lugar de ignorar el conflicto, Zeus reduce el Score Matemático para reflejar la inconsistencia.

**¿Qué hago si el veredicto es 🟠 o 🔴?**
Ariadna activa su Plan de Rescate. Si el Score Real es < 40%, el plan es completo (diagnóstico, mitigaciones, matriz, preguntas). Si está entre 40–59%, el plan es ligero (solo matriz + preguntas). Sigue sus recomendaciones, consigue más datos sobre los puntos débiles y vuelve a ejecutar el análisis. Muchas ideas fracasan en la primera pasada.

**¿Funciona para ideas no tecnológicas?**
Sí. Hefesto evaluará la viabilidad técnica (que aplica a cualquier proceso, no solo software) y las demás personalidades analizan sin asumir tecnología.

---

*Concili_ON v2.2 — Creado con el stack offline-first (Skill System + Markdown)*
