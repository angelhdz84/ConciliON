# Concili_ON — Análisis: Offline-First Apps + JutIA para MiPymes LATAM

**Problema:** MiPymes en Latinoamérica necesitan apps que funcionen 100% offline (conectividad inestable)
**Solución:** Apps offline-first con IA integrada (JutIA), 3 variantes: Lite (gratis ≤30 registros + IA Lite), Professional (IA Full, ingesta docs, predicciones), Enterprise (Pro + White Label)
**Cliente objetivo:** MiPymes en Latinoamérica
**Modelo de negocio:** Freemium (Lite gratis) + Professional ($29/mes) + Enterprise ($499/mes + $50/partner)

---

## FASE 1: Análisis Inicial

### 👤 Adán (Visionario)

**¿Por qué esta idea VA A GANAR?**
Latinoamérica tiene ~14 millones de MiPymes con conectividad inestable. Nadie atiende offline-first + IA local. JutIA como moat técnico real (no wrapper de API). En 5 años: capa base de operación — el "ERP invisible" sin internet.

**Mi SCORE: 9/10**
**Razón:** TAM masivo desatendido, barrera técnica real (offline + IA local), modelo freemium viral en MiPymes, white-label abre canal B2B2B masivo.
**Visión a 5 años:** Ser el sistema operativo offline de facto para MiPymes en LATAM, 500k+ usuarios activos, red de partners white-label en 12+ países.

---

### 👤 Eva (Risk Manager)

**Riesgos detectados:**

| Riesgo | Severidad |
|---|---|
| Distribución/descubrimiento (MiPymes no buscan "apps offline") | 🔴 Crítico |
| IA local full en móvil (RAM/CPU limitados, UX rota) | 🔴 Crítico |
| Fragmentación fiscal multi-país (MX, CO, CL, AR, PE) | 🟠 Importante |
| Competencia "good enough" (WhatsApp, Excel, Sheets) | 🟠 Importante |
| Conversión Lite→Pro incierta (30 registros techo) | 🟡 Menor |
| Mantenimiento white-label (fork, soporte, SLA) | 🟡 Menor |

**Mi SCORE: 4/10**
**Razón:** Dos riesgos críticos sin mitigación clara; fragmentación LATAM añade coste operativo masivo.

**🔝 Top 3 Fortalezas:**
1. Mercado real desatendido (offline real + IA local)
2. Modelo freemium con techo bajo que fuerza upgrade
3. White-label Enterprise = canal de distribución B2B2B

**🔻 Top 3 Debilidades:**
1. Canal de adquisición offline inexistente / CAC desconocido
2. IA local en móvil: técnicamente muy arriesgado
3. Fragmentación regulatoria LATAM por país

---

### 👤 Bruno (El Lego)

**Explicación simple:** "Una app que funciona SIN internet en el celular de un negocio pequeño. Guarda todo local. Tiene una IA que vive en el celular (no en la nube) y lee tus PDFs, Excel, facturas para darte respuestas y predicciones. Versión gratis hasta 30 cosas guardadas. Versión pro ilimitada + IA completa. Versión enterprise: te la ponen con tu marca."

**Preguntas sin respuesta:**
- ¿Cómo descubre la app el dueño de la tienda?
- ¿La IA en el celular no lo deja lento / consume mucha batería?
- ¿Sirve para facturación electrónica en MX/CO/CL/AR?
- ¿"30 registros" son facturas, clientes o productos?

**Mi SCORE: 6/10**
**Razón:** Concepto entendible pero "offline-first + IA local" suena a oxímoron para no técnicos; techo de 30 registros ambiguo; falta claridad en propuesta de valor país a país.

---

## FASE 2: Validación de Mercado

### 👤 Midas (El Cliente)

**Alternativa actual:** WhatsApp + Google Sheets/Excel + papel + memoria
**Competidor más fuerte:** Siigo, Alegra, Contabilium, Facturama — facturación nativa por país, pero fallan offline
**Ventaja diferencial única:** 100% offline real + IA que entiende documentos sin configurar
**Motivo real para cambiar:** "Ahorra 5 hrs/semana + nunca pierdo venta por falta de internet + IA predice stock"

**Mi SCORE: 7/10**
**Razón:** Dolor real (tiempo + errores + multas), ventaja técnica única, pero CAC alto y decisión de compra lenta en MiPyme; necesita demostrar ROI inmediato.

---

### 👤 Ben (Niño de 12 años — UX)

- Onboarding: "Abre → escanea factura → listo". Cero configuración.
- IA Lite debe responder en <2s offline. Si tarda 10s → borra la app.
- Límite 30 registros: debe ser suave (notificación), no muro duro.
- Sync eventual silencioso — usuario no debe saber que existe.
- Riesgo UX principal: IA local en móvil gama media = latencia/calidad impredecible.

**Mi SCORE: 5/10**
**Razón:** IA local en móvil = latencia/calidad riesgo UX alto; límite 30 registros = fricción brusca; onboarding multi-país = complejidad invisible pero fatal si falla.

---

## FASE 3: Evaluación Técnica y Financiera

### 👤 Tesla (Ingeniero)

| Aspecto | Valor |
|---|---|
| **Complejidad técnica** | **Muy Alta** |
| **MVP realista** | Offline CRUD + facturación 1 país + IA Lite = 4-5 meses (3-4 devs senior) |
| **Stack** | Capacitor + SQLite (FTS5) + Dexie + Transformers.js (quantized) + pako + workers |
| **Dependencias** | APIs facturación x país (PAC MX, DIAN CO, SII CL, AFIP AR, SUNAT PE), modelos IA, plugins nativos, regulación |

**Mi SCORE: 3/10**
**Razón:** Tres complejidades "Muy Alta" concurrentes (offline sync, IA local, multi-país) superan capacidad de equipo pequeño; MVP real >6 meses.

---

### 👤 Warren (Financiero)

| Concepto | Valor |
|---|---|
| **Inversión inicial** | $420k – $580k |
| **Tiempo primer ingreso** | 6–8 meses |
| **Margen bruto** | 85–90% |
| **Break-even** | 18–24 meses post-launch |
| **Mayor gasto** | Equipo técnico senior (perfiles escasos/caros) |
| **Precios** | Lite $0 / Pro $29/mes / Enterprise $499/mes + $50/partner |

**Mi SCORE: 5/10**
**Razón:** Unidad económica viable (LTV/CAC >3 si CAC <$150), pero capex alto ($500k), break-even lejano (20+ meses), CAC MiPyme offline es incógnita.

---

## FASE 4: Decisión y Estrategia

### 👤 Zeus (El Juez)

#### 1. Score Matemático

| Personalidad | Score | Peso | Ponderado |
|---|---|---|---|
| Adán | 9/10 | 7% | 0.63 |
| Eva | 4/10 | 15% | 0.60 |
| Bruno | 6/10 | 7% | 0.42 |
| Midas | 7/10 | 25% | 1.75 |
| Ben | 5/10 | 6% | 0.30 |
| Tesla | 3/10 | 15% | 0.45 |
| Warren | 5/10 | 25% | 1.25 |
| **TOTAL** | | **100%** | **5.40 / 10 = 54.0%** |

#### 2. Contradicciones

| Choque | Tensión | Ganador |
|---|---|---|
| Adán (9) vs Tesla (3) + Eva (4) | Visión vs Técnica+Riesgos | Eva + Tesla |
| Midas (7) vs Warren (5) + Ben (5) | Cliente vs Costos+UX | Warren |
| Eva (4) vs Adán/Midas | Distribución vs White-label | Eva |

#### 3. Penalizaciones

| Contradicción | Grado | Penalización |
|---|---|---|
| Visión vs Técnica+Riesgos | Crítica | -15% |
| Cliente vs Costos+UX | Importante | -8% |
| Distribución vs White-label | Menor | -3% |
| Penalización base total (capped) | | **-20%** |
| Ajuste Zeus (-3% optimismo residual) | | **-3%** |
| **Penalización final** | | **-20%** |

#### 4. Score Real

Score Matemático: 54.0%
Penalización final Zeus: -20%
**Score Real: 34.0%**

---

### 👤 Salomón (El Estratega)

**Experimento barato (4 semanas, $3,500):**

| Campo | Definición |
|---|---|
| **Hipótesis** | Dueños de MiPyme pagan $29/mes por app offline que gestione stock/ventas + IA que responda escaneando tickets |
| **Experimento** | Concierge MVP manual: 15 dueños (5 MX, 5 CO, 5 CL) reciben PWA simple CRUD offline + OCR local. Sin IA generativa, sin facturación. WhatsApp soporte. Medir 4 semanas. |
| **Duración** | 4 semanas (1 reclut. + 3 uso) |
| **Costo máximo** | $3,500 |
| **Usuarios mínimos** | 15 |
| **KPI de éxito** | WAU/MAU > 60% semana 3 |
| **Criterio de éxito** | WAU/MAU > 60% Y ≥8/15 pagan |
| **Criterio para abandonar** | WAU/MAU < 30% O <5/15 pagan |

---

## 📊 SCORE CONCILI_ON

### Cálculo paso a paso

```
Warren:  [5] * 0.25 = [1.25]
Midas:   [7] * 0.25 = [1.75]
Eva:     [4] * 0.15 = [0.60]
Tesla:   [3] * 0.15 = [0.45]
Adán:    [9] * 0.07 = [0.63]
Bruno:   [6] * 0.07 = [0.42]
Ben:     [5] * 0.06 = [0.30]
                         ——
TOTAL:   [5.40] / 10 = [54.0]%
```

### Score Real

Score Matemático: 54.0%
Penalización final Zeus: -20%
**Score Real: 34.0%**

### Índice de Incertidumbre

| Supuesto clave | Impacto |
|---|---|
| CAC MiPyme offline < $150 | ±12% |
| IA local latencia < 2s en móvil gama media | ±10% |
| Conversión Lite→Pro > 8% | ±8% |
| Facturación 1 país en MVP | ±6% |
| **Rango probable real** | **22% – 46%** |

### Nivel de Confianza

**Media-Baja.** Tres supuestos críticos sin validar: CAC real en canal offline, viabilidad UX IA local, disposición a pagar $29/mes.

### Veredicto final

| Rango | Decisión |
|---|---|
| 34.0% < 40% | 🔴 **RECHAZAR** |

**Veredicto Concili_ON:** 🔴 RECHAZADO — No construyas el producto aún. Ejecuta el experimento concierge de Salomón (4 sem, $3,500). Si WAU/MAU >60% y 8/15 pagan → reaplica. Si no → pivota.

---

## FASE 5: Consejo de Inversión

| Personalidad | Voto | Razón |
|---|---|---|
| Adán | ⏳ Solo después de validar | Visión gigante, necesito ver tracción |
| Eva | ❌ No | Dos riesgos críticos queman capital |
| Bruno | ⏳ Solo después de validar | Concepto ok, necesito ver uso real |
| Midas | ⏳ Solo después de validar | Dolor real, pero sin canal no hay negocio |
| Ben | ❌ No | IA local = UX rota garantizada hoy |
| Tesla | ❌ No | 3 frentes Muy Alta = proyecto 2 años |
| Warren | ❌ No | $500k capex + CAC desconocido = apuesta |

### Votos finales

- ✅ A favor: 0
- ❌ En contra: 4
- ⏳ Condicionales: 3

### Decisión del Consejo

El consejo NO INVIERTE. Exige validar primero el experimento concierge de Salomón (4 sem, $3,500). Solo si WAU/MAU >60% y 8/15 pagan $29/mes, reevaluaríamos.
