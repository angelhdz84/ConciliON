# Manual de Concili_ON — Motor de Validación de Ideas

## Versión 2.0 | Julio 2026

---

## Índice

1. [¿Qué es Concili_ON?](#1-qu%C3%A9-es-concili_on)
2. [Instalación y activación](#2-instalaci%C3%B3n-y-activaci%C3%B3n)
3. [Cómo usar la skill](#3-c%C3%B3mo-usar-la-skill)
4. [Las 9 personalidades](#4-las-9-personalidades)
5. [Las 5 fases del análisis](#5-las-5-fases-del-an%C3%A1lisis)
6. [Sistema de puntuación](#6-sistema-de-puntuaci%C3%B3n)
7. [Penalización por contradicciones](#7-penalizaci%C3%B3n-por-contradicciones)
8. [Veredicto y semáforo](#8-veredicto-y-sem%C3%A1foro)
9. [Índice de incertidumbre y confianza](#9-%C3%ADndice-de-incertidumbre-y-confianza)
10. [Consejo de Inversión](#10-consejo-de-inversi%C3%B3n)
11. [Casos de prueba](#11-casos-de-prueba)
12. [Resultados del benchmark](#12-resultados-del-benchmark)
13. [Historial de versiones](#13-historial-de-versiones)
14. [Preguntas frecuentes](#14-preguntas-frecuentes)

---

## 1. ¿Qué es Concili_ON?

Concili_ON es un motor de validación de ideas de negocio que simula un consejo de 9 expertos con personalidades, sesgos y pesos definidos. Cada experto analiza la idea desde su especialidad, asigna un score y justifica su posición. Luego, un juez (Zeus) detecta contradicciones entre ellos, aplica penalizaciones y calcula un Score Real ponderado. Finalmente, el Consejo de Inversión vota si poner dinero propio en la idea.

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
├── SKILL.md              ← Motor principal (257 líneas)
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

El motor ejecuta 5 fases automáticamente. Cada fase despliega el análisis de las personalidades correspondientes. Al final obtienes:

- Score Matemático (ponderación pura)
- Tabla de contradicciones detectadas
- Penalización aplicada por Zeus
- Score Real (después de penalizar)
- Índice de incertidumbre
- Nivel de confianza del análisis
- Veredicto con semáforo
- Votos del Consejo de Inversión

### Paso 3: iteración

Si el veredicto es 🟠 REQUIERE PIVOTE o 🔴 RECHAZAR, puedes modificar la idea con los datos que faltaban y volver a ejecutar el análisis.

---

## 4. Las 9 personalidades

### 4.1 Perfiles con score (pesan en el resultado final)

| # | Personalidad | Rol | Peso | Enfoque principal |
|---|---|---|---|---|
| 1 | **Warren Buffett** | Financiero | **25%** | Costos, margen, ROI, punto de equilibrio |
| 2 | **Midas** | El Cliente | **25%** | Disposición al pago, competencia, demanda real |
| 3 | **Eva Perón** | Risk Manager | **15%** | Riesgos críticos, costos ocultos, fortalezas/debilidades |
| 4 | **Nikola Tesla** | Ingeniero | **15%** | Viabilidad técnica, complejidad, dependencias |
| 5 | **Adán** | Visionario | **7%** | Impacto, escalabilidad, visión a 5 años |
| 6 | **Bruno Munari** | El Lego | **7%** | Claridad conceptual, comunicación de la idea |
| 7 | **Benjamin Graham** | UX / Niño 12 años | **6%** | Fricción de uso, intuición, experiencia |
| | **Total** | | **100%** | |

### 4.2 Perfiles sin score (analíticos/decisorios)

| # | Personalidad | Rol | Función |
|---|---|---|---|
| 8 | **Zeus** | El Juez | Compila scores, detecta contradicciones, aplica penalizaciones, calcula Score Real |
| 9 | **Salomón** | El Estratega | Diseña experimento barato para validar la hipótesis crítica |

---

## 5. Las 5 fases del análisis

### FASE 1 — Análisis Inicial

| Personalidad | Qué hace | Output |
|---|---|---|
| **Adán (Visionario)** | Describe por qué la idea va a ganar. Cero negatividad. Proyecta a 5 años. | Score /10 + Razón + Visión |
| **Eva (Risk Manager)** | Enumera riesgos clasificados por severidad. Da Top 3 Fortalezas y Top 3 Debilidades. | Score /10 + Razón + Riesgos clasificados + F/D |
| **Bruno (El Lego)** | Explica la idea en lenguaje simple. Detecta confusión conceptual. | Score /10 + Razón |

### FASE 2 — Validación de Mercado

| Personalidad | Qué hace | Output |
|---|---|---|
| **Midas (El Cliente)** | Analiza disposición al pago. Estudia competencia (alternativa actual, competidor fuerte, ventaja diferencial, motivo de cambio). | Score /10 + Razón + Análisis competencia |
| **Ben (Niño 12 años)** | Evalúa fricción de uso. ¿Un niño lo usaría sin instrucciones? | Score /10 + Razón |

### FASE 3 — Evaluación Técnica y Financiera

| Personalidad | Qué hace | Output |
|---|---|---|
| **Tesla (Ingeniero)** | Viabilidad técnica. ¿MVP en <3 meses? Clasifica complejidad y dependencias. | Score /10 + Razón + Complejidad + Dependencias |
| **Warren (Financiero)** | Métricas financieras concretas: inversión inicial, margen, punto de equilibrio, mayor gasto. | Score /10 + Razón + 5 métricas |

### FASE 4 — Decisión y Estrategia

| Personalidad | Qué hace | Output |
|---|---|---|
| **Zeus (El Juez)** | Compila tabla de scores, detecta contradicciones, aplica penalización y calcula Score Real. | Score Matemático → Penalización → Score Real |
| **Salomón (El Estratega)** | Diseña experimento de validación con protocolo científico completo. | Hipótesis, Experimento, KPI, Criterios |

### FASE 5 — Consejo de Inversión

| Personalidad | Qué hace | Output |
|---|---|---|
| **Todas (7 votantes)** | Cada una responde si invertiría dinero propio. | Sí / No / Solo después de validar + Razón |
| **Zeus (resume)** | Cuenta votos y da decisión del consejo. | Votos finales + Decisión |

---

## 6. Sistema de puntuación

### Pesos asignados

```
Warren:  [X] * 0.25 = [Y]
Midas:   [X] * 0.25 = [Y]
Eva:     [X] * 0.15 = [Y]
Tesla:   [X] * 0.15 = [Y]
Adán:    [X] * 0.07 = [Y]
Bruno:   [X] * 0.07 = [Y]
Ben:     [X] * 0.06 = [Y]
                         ——
TOTAL:   [Suma de Y] / 10 = [Z]%
```

**Interpretación de los pesos:**
- **50%** va a Finanzas y Mercado (Warren + Midas) — lo que realmente determina si un negocio funciona
- **30%** va a Riesgos y Tecnología (Eva + Tesla) — los dos grandes filtros de realidad
- **20%** va a Visión, Claridad y UX (Adán + Bruno + Ben) — importante pero no determinante

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

### Ejemplo

```
Contradicción detectada   Grado       Penalización
──────────────────────    ─────       ────────────
Mercado 10 vs Tecnología 2  Crítica    -15%
Adán 9 vs Warren 3          Importante  -8%
                           ──────────
Penalización base total:              -23% → recortado a -20%
Ajuste Zeus (±5%):                    +2% (las métricas de Warren son robustas)
Penalización final Zeus:              -18%
```

---

## 8. Veredicto y semáforo

Basado en el **Score Real (Z2%)**:

| Rango | Símbolo | Decisión | Acción |
|---|---|---|---|
| Z2 > 80% | 🟢 **APROBAR** | Viabilidad alta | Ejecutar el experimento de Salomón |
| Z2 60–79% | 🟡 **APROBAR CON MODIFICACIONES** | Requiere pivotear según alertas de Zeus |
| Z2 40–59% | 🟠 **REQUIERE PIVOTE SIGNIFICATIVO** | Volver a Fase 1 |
| Z2 < 40% | 🔴 **RECHAZAR** | Warren/Tesla no soportan la visión de Adán |

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
| Adán         | Sí                          | Tiene potencial de 10x |
| Eva          | No                          | Demasiados riesgos regulatorios |
| Midas        | Solo después de validar     | El mercado no está probado |
| Tesla        | No                          | MVP requiere 6+ meses |
| Warren       | Solo después de validar     | Gastos iniciales altos |
| Bruno        | Sí                          | La idea es muy clara |
| Ben          | Sí                          | Experiencia intuitiva |
```

### Votos finales

- ✅ A favor: 3
- ❌ En contra: 2
- ⏳ Condicionales: 2

### Decisión del Consejo

Una frase que resume qué haría el consejo con su dinero.

---

## 11. Casos de prueba

La skill incluye 3 casos de prueba en `evals/evals.json`:

| # | Caso | Input | Expected |
|---|---|---|---|
| 1 | **App Paseo Perros** | App tipo Uber para paseo de perros, con todos los datos completos (problema, solución, cliente, modelo de negocio) | Análisis completo con 5 fases, scores, contradicciones, veredicto y consejo |
| 2 | **Idea vaga — bowls** | "Un negocio de comida saludable, algo de bowls" — sin datos concretos | La skill debe BLOQUEAR y pedir los 4 campos obligatorios |
| 3 | **Red Doctores + Crypto** | Red social descentralizada para doctores con pagos en crypto. Tiene datos completos pero contradicciones internas | Tesla marca baja factibilidad técnica, Warren critica el modelo crypto, Zeus detecta contradicciones |

---

## 12. Resultados del benchmark

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

## 13. Historial de versiones

### v2.0 (Julio 2026) — Mejoras estructurales

- Separación de Score Matemático → Penalización Zeus → Score Real
- Penalización por contradicciones con tabla fija (-15%/-8%/-3%) + ajuste Zeus ±5%
- Nueva FASE 5: Consejo de Inversión con votos
- Cada personalidad justifica su score (1-3 oraciones)
- Eva clasifica riesgos por severidad (🔴 Crítico / 🟠 Importante / 🟡 Menor)
- Warren exige métricas cuantitativas (inversión inicial, margen, punto de equilibrio, mayor gasto)
- Tesla mide complejidad técnica (Muy Baja → Muy Alta) + dependencias externas
- Midas analiza competencia (alternativa actual, competidor fuerte, ventaja diferencial, motivo de cambio)
- Salomón usa protocolo científico (hipótesis, KPI, criterio de éxito, criterio de abandono)
- Índice de incertidumbre con 3 supuestos y rango probable
- Nivel de confianza del análisis (Alta / Media / Baja)
- Eva reporta Top 3 Fortalezas y Top 3 Debilidades
- 257 líneas, 9.7 KB

### v1.0 (Julio 2026) — Lanzamiento inicial

- 4 fases, 9 personalidades, score ponderado
- Detección de contradicciones (Zeus)
- Semáforo de veredicto (🟢🟡🟠🔴)
- 135 líneas, 5.5 KB

---

## 14. Preguntas frecuentes

**¿Puedo usar Concili_ON sin internet?**
Sí. La skill es 100% offline. No requiere APIs externas, CDNs ni conexión a internet.

**¿Qué pasa si no tengo todos los datos de mi idea?**
La skill te pedirá los 4 campos obligatorios (Problema, Solución, Cliente, Modelo de negocio) antes de comenzar. No evalúa hasta tenerlos.

**¿Cuánto tiempo toma el análisis?**
Depende del LLM, pero típicamente 10-30 segundos para generar las 5 fases completas.

**¿Puedo modificar los pesos de las personalidades?**
Los pesos están fijos en el SKILL.md (Warren 25%, Midas 25%, Eva 15%, Tesla 15%, Adán 7%, Bruno 7%, Ben 6%). Si quieres modificarlos, edita el SKILL.md directamente.

**¿Qué significa que Zeus aplique una penalización?**
Significa que encontró contradicciones graves entre las personalidades (ej: Madas da 10/10 en mercado pero Tesla da 2/10 en tecnología). En lugar de ignorar el conflicto, Zeus reduce el Score Matemático para reflejar la inconsistencia.

**¿Qué hago si el veredicto es 🟠 o 🔴?**
Revisa las alertas de Zeus y las debilidades que identificó Eva. Consigue más datos sobre los puntos débiles y vuelve a ejecutar el análisis. Muchas ideas fracasan en la primera pasada.

**¿Funciona para ideas no tecnológicas?**
Sí. Tesla evaluará la viabilidad técnica (que aplica a cualquier proceso, no solo software) y las demás personalidades analizan sin asumir tecnología.

---

*Concili_ON v2.0 — Creado con el stack offline-first (Skill System + Markdown)*
