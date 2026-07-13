# Concili_ON — Motor de Validación de Ideas

**Versión:** 2.3 | **Última actualización:** Julio 2026

---

## ¿Qué es Concili_ON?

Concili_ON es un **motor de evaluación de ideas de negocio** que simula un consejo de inversión con 10 personalidades especializadas. Cada personalidad analiza la idea desde su ángulo, emite un score, y al final se calcula un **Score Real** con penalizaciones por contradicciones.

**Resultado:** En 5 minutos obtienes un veredicto objetivo con datos concretos, no opiniones vagas.

---

## ¿Para quién funciona?

| Audiencia | Beneficio clave |
|-----------|-----------------|
| **Emprendedores** | Valida tu idea antes de invertir tiempo y dinero |
| **Desarrolladores** | Evalúa viabilidad técnica y costos reales |
| **Inversores/VC** | Framework estructurado para due diligence |
| **Product Managers** | Prioriza features con análisis de mercado |

---

## Las 10 Personalidades

### Las 7 que votan (pesan en el resultado)

| Emoji | Nombre | Rol | Peso | Qué evalúa |
|-------|--------|-----|------|------------|
| 👁️ | **Adán** | Visionario | 7% | Impacto, escalabilidad, visión a 5 años |
| 🛡️ | **Eva** | Risk Manager | 15% | Riesgos críticos, costos ocultos |
| 📢 | **Hermes** | El Mensajero | 7% | Claridad de la idea |
| 💰 | **Midas** | El Cliente | 25% | Disposición al pago, competencia |
| 🧒 | **Loki** | Niño UX | 6% | Experiencia de uso |
| 🔧 | **Tesla** | Ingeniero | 15% | Viabilidad técnica |
| 📊 | **Dédalo** | Financiero | 25% | Costos, ROI, punto de equilibrio |

### Las 3 analíticas (no votan)

| Emoji | Nombre | Rol | Cuándo actúa |
|-------|--------|-----|--------------|
| ⚡ | **Zeus** | El Juez | Fase 4 — detecta contradicciones |
| 🧭 | **Odiseo** | El Estratega | Fase 4 — diseña experimento barato |
| 🧶 | **Isis** | Plan de Rescate | Solo si Score < 60% |

---

## Las 5 Fases

```
┌─────────────────────────────────────────────────────────────┐
│  FASE 0 │ Hermes evalúa claridad mínima                     │
│         │ ¿Se entiende la idea en 1 frase?                  │
├─────────┼───────────────────────────────────────────────────┤
│  FASE 1 │ Adán (visión) + Eva (riesgos) + Hermes (claridad) │
├─────────┼───────────────────────────────────────────────────┤
│  FASE 2 │ Midas (mercado) + Loki (UX)                       │
├─────────┼───────────────────────────────────────────────────┤
│  FASE 3 │ Tesla (técnico) + Dédalo (financiero)             │
├─────────┼───────────────────────────────────────────────────┤
│  FASE 4 │ Zeus (contradicciones) + Odiseo (experimento)     │
├─────────┼───────────────────────────────────────────────────┤
│  POST   │ Isis (rescate) — solo si Score Real < 60%         │
└─────────┴───────────────────────────────────────────────────┘
```

---

## Cómo funciona el Score

### Fórmula

```
Score Matemático = Σ (Score_i × Peso_i)
Score Real = Score Matemático - Penalización Zeus
```

### Pesos fijos

| Bloque | Personalidades | Peso total |
|--------|----------------|------------|
| Finanzas y Mercado | Dédalo + Midas | **50%** |
| Riesgos y Tecnología | Eva + Tesla | **30%** |
| Visión, Claridad y UX | Adán + Hermes + Loki | **20%** |

### Veredicto

| Score Real | Decisión | Acción |
|------------|----------|--------|
| ≥ 80% | 🟢 **APROBAR** | Ejecutar experimento de Odiseo |
| 60-79% | 🟡 **APROBAR CON MODIFICACIONES** | Pivotear según alertas de Zeus |
| 40-59% | 🟠 **REQUIERE PIVOTE** | Volver a Fase 1 |
| < 40% | 🔴 **RECHAZAR** | Isis activa Plan de Rescate |

---

## Output de cada análisis

Cada ejecución genera **3 archivos** en `analisis/<slug-idea>/`:

| Archivo | Contenido | Uso |
|---------|-----------|-----|
| `<slug>-concili-on.md` | Volcado textual completo | Documentación, revisión |
| `<slug>-concili-on.json` | Datos estructurados | Integración, dashboards |
| `<slug>-concili-on.html` | Reporte visual offline | Presentación, sharing |

### Ejemplo de estructura JSON

```json
{
  "slug": "saas-facturacion-contadores",
  "fecha": "2026-07-13T10:00:00Z",
  "scores": {
    "adan": { "score": 8, "peso": 0.07 },
    "eva": { "score": 7, "peso": 0.15 },
    "midas": { "score": 9, "peso": 0.25 },
    "dedalo": { "score": 8, "peso": 0.25 }
  },
  "score_real": 82,
  "veredicto": "aprobado"
}
```

---

## Requisitos técnicos del HTML

- **0 dependencias externas** — Sin CDN, Google Fonts ni librerías JS
- **Offline 100%** — Abrible desde filesystem sin servidor
- **Light theme** — Fondo claro (#f8f9fa), cards blancas
- **Responsive** — Desktop + mobile
- **Visualizaciones incluidas:**
  - Gauge SVG del Score Real
  - Barras de scores por personalidad
  - Waterfall de penalizaciones
  - Tarjetas de contradicciones
  - Votación del consejo

---

## Cómo usar Concili_ON

### Opción 1 — Directa

```
Analiza esta idea: [describe tu idea aquí]
```

### Opción 2 — Con los 4 campos

```
Evalúa mi idea:
- Problema: [qué resuelve]
- Solución: [cómo lo resuelve]
- Cliente: [quién paga]
- Modelo: [cómo genera ingresos]
```

### Opción 3 — Con datos补充

```
Analiza esta idea con estos datos:
[campos obligatorios]
[datos adicionales: mercado, competencia, stack técnico, etc.]
```

---

## Casos de uso reales

### Caso 1: SaaS para contadores
- **Idea:** App de facturación automática para despachos contables
- **Score Real:** 82% 🟢
- **Resultado:** Aprobado. Dédalo validó márgenes, Tesla confirmó MVP en 2 meses

### Caso 2: App de delivery de mascotas
- **Idea:** Uber pero para pasear perros
- **Score Real:** 67% 🟡
- **Resultado:** Aprobado con modificaciones. Loki señaló fricción en onboarding

### Caso 3: Red social descentralizada con crypto
- **Idea:** Red para doctores con pagos en criptomonedas
- **Score Real:** 34% 🔴
- **Resultado:** Rechazado. Tesla marcó baja factibilidad, Dédalo critica modelo crypto

---

## FAQ

**¿Puedo cambiar los pesos?**
Sí. Editando `SKILL.md` en la skill.

**¿Funciona para ideas no-tech?**
Sí. Tesla evaluará viabilidad técnica (que aplica a cualquier proceso, no solo software).

**¿Cuánto tarda un análisis?**
~5 minutos con datos completos.

**¿Puedo re-ejecutar después de pivotear?**
Sí. Isis recomienda qué datos obtener antes de re-evaluar.

---

## Archivos del proyecto

| Archivo | Propósito |
|---------|-----------|
| `C:\Users\Angel\.agents\skills\concili-on\SKILL.md` | Skill principal (motor) |
| `docs/manual_ConciliON.md` | Manual completo |
| `docs/ConciliON_Presentacion.md` | Este documento |
| `specs/concili-on-skill-v2.md` | Especificación técnica |
| `AGENTS.md` | Configuración del agente |

---

## Contacto y soporte

- **Repositorio:** github.com/angelhdz84/ConciliON
- **Issues:** github.com/angelhdz84/ConciliON/issues

---

*Concili_ON v2.3 — Built with ❤️ for founders who validate before they build.*
