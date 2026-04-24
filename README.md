# Prompts — Juego de Detectives

---

## Archivos

| Archivo | Etapa | Uso |
|---------|-------|-----|
| `00_concepto_del_juego.md` | — | Concepto, modelo de negocio y loop semanal |
| `01_arquitecto.md` | Etapa 1 | Diseña la lógica interna del caso |
| `02_redactor.md` | Etapa 2 | Redacta el caso narrativo para el jugador |
| `03_jugador.md` | Etapa 3 | Resuelve el caso como jugador ciego (filtro de dificultad) |
| `04_evaluador_de_casos.md` | Etapa 4 | Evalúa y aprueba el caso |
| `05_generador_imagenes.md` | Etapa 5 | Genera los prompts de Midjourney del caso aprobado |
| `Creador de imagenes/STYLE_BIBLE.md` | Referencia | Guía visual oficial del proyecto (colores, proporciones, reglas) |

---

## Flujo de trabajo completo

```
┌─────────────────────────────────────────────────────────────┐
│  ETAPA 1 — Arquitecto                                       │
│  Input: ninguno (o feedback del Evaluador/Jugador)          │
│  Output: solución, personajes, mapa espacial (PASO B2),     │
│          contradicciones, línea de tiempo, ruta deductiva   │
└──────────────────────────┬──────────────────────────────────┘
                           ▼
┌─────────────────────────────────────────────────────────────┐
│  ETAPA 2 — Redactor                                         │
│  Input: output del Arquitecto                               │
│  Output: caso narrativo completo para el jugador            │
└──────────────────────────┬──────────────────────────────────┘
                           ▼
┌─────────────────────────────────────────────────────────────┐
│  ETAPA 3 — Jugador (filtro ciego de dificultad)             │
│  Input: SOLO la narrativa (no conoce la solución)           │
│  Output: 🟢 FÁCIL / 🟡 CALIBRADO / 🔴 DIFÍCIL / ⚫ IRRESOLUBLE │
│                                                             │
│  🟢 FÁCIL       → vuelve a Etapa 2 (oscurecer pistas)       │
│  ⚫ IRRESOLUBLE → vuelve a Etapa 1 (ruta deductiva rota)    │
│  🟡 / 🔴          → pasa a Etapa 4                          │
└──────────────────────────┬──────────────────────────────────┘
                           ▼
┌─────────────────────────────────────────────────────────────┐
│  ETAPA 4 — Evaluador                                        │
│  Input: narrativa + arquitectura + reporte del Jugador      │
│  Output: ✅ APTO / ⚠️ MEJORAR / ❌ DESCARTAR + feedback     │
│  ⚠️ MEJORAR → relanza Etapa 1 y/o 2 según PASO 14           │
│  ✅ APTO    → caso_final.md                                  │
└──────────────────────────┬──────────────────────────────────┘
                           │ disparo MANUAL (opcional)
                           ▼
┌─────────────────────────────────────────────────────────────┐
│  ETAPA 5 — Generador de Imágenes                            │
│  Input: caso_final.md + arquitectura (mapa espacial)        │
│  Output: 3 archivos en `casos/{slug}/imagenes/`             │
│  ├── personajes.md  (víctima + sospechosos × 5 ángulos,     │
│  │                   testigos × retrato)                    │
│  ├── escenas.md     (una por fila de la tabla PASO B2)      │
│  └── evidencias.md  (una tarjeta por evidencia)             │
│  Disparo: `/generar-imagenes {slug}`                         │
└──────────────────────────┬──────────────────────────────────┘
                           ▼
              Copiar cada prompt a Midjourney v6.1
```

---

## Mínimos obligatorios por caso

| Elemento | Mínimo |
|----------|--------|
| Sospechosos | 4 |
| Testigos con testimonio | 5 |
| Palabras por testimonio | 150 |
| Preguntas por interrogatorio | 8 |
| Datos distintos sobre la víctima | 5 |
| Datos a deducir (no declarados) | 3 |
| Mentiras activas en testimonios | 3 |
| Omisiones deliberadas | 3 |

---

## Imágenes que genera la Etapa 5 por caso

Ver `Creador de imagenes/STYLE_BIBLE.md` para colores, proporciones y reglas del universo visual (cartoon caricatura, outlines negros, cel-shading, teal dominante).

| Categoría | Cantidad | Formato |
|-----------|----------|---------|
| Víctima | 5 ángulos | Retrato + frente + espalda + 2 perfiles |
| Sospechosos | 5 ángulos c/u | Retrato + frente + espalda + 2 perfiles |
| Testigos | 1 retrato c/u | Retrato 2:3 |
| Escenas | Una por fila de la tabla PASO B2 del Arquitecto | Plano 2:3, cámara fija |
| Evidencias | Una tarjeta por evidencia física | Tarjeta 2:3 con etiqueta E-XX |

---

## Slash Commands de Claude Code

Tres comandos orquestan el pipeline directamente desde Claude Code:
- `/crear-caso` y `/corregir-caso` encadenan las etapas 1–4 hasta llegar a `✅ APTO`.
- `/generar-imagenes` es **manual** y se dispara solo cuando ya hay `caso_final.md` — convierte el caso aprobado en prompts de Midjourney.

---

### `/crear-caso "Nombre del Caso"`

Genera un caso nuevo desde cero, iterando automáticamente hasta que el evaluador diga APTO.

**Ejemplo:**
```
/crear-caso "El Reloj de Medianoche"
```

**Qué hace internamente:**

```
1. Genera slug: "El Reloj de Medianoche" → el_reloj_de_medianoche
2. Crea casos/el_reloj_de_medianoche/

Iteración 1:
  ├── ARQUITECTO → iter_01/arquitectura.md
  ├── REDACTOR   → iter_01/narrativa.md
  └── EVALUADOR  → iter_01/evaluacion.md
       │
       ├── ✅ APTO     → copia narrativa a caso_final.md, termina
       ├── ❌ DESCARTAR → reporta razones, termina
       └── ⚠️ MEJORAR  → lee PASO 14 del evaluador y decide:
            ├── falla arquitectura → relanza Arquitecto + Redactor con feedback
            ├── solo falla narrativa → salta Arquitecto, relanza solo Redactor
            └── ambas → Arquitecto primero, luego Redactor con ambos feedbacks

Iteración 2, 3... (máximo 5)
```

**Estructura de salida:**
```
casos/el_reloj_de_medianoche/
├── iter_01/
│   ├── arquitectura.md
│   ├── narrativa.md
│   ├── jugador.md
│   └── evaluacion.md
├── iter_02/          ← si hubo correcciones
│   └── ...
└── caso_final.md     ← cuando el evaluador aprueba
```

**Lógica de routing:** el Jugador (Etapa 3) puede rebotar a Redactor (FÁCIL) o Arquitecto (IRRESOLUBLE) antes del Evaluador. El Evaluador (Etapa 4) usa PASO 1 para el veredicto y PASO 14 para decidir si el fallo está en arquitectura (Etapa 1), narrativa (Etapa 2), o ambas.

**Límite:** 5 iteraciones máximo como seguridad ante bucles infinitos.

---

### `/corregir-caso <ruta>`

Evalúa y corrige un caso existente. Arranca directamente desde el Evaluador (sin regenerar desde cero).

**Ejemplos:**
```
/corregir-caso casos/codex/narrativa.md
/corregir-caso casos/codex/
```

**Qué hace internamente:**

```
1. Lee el archivo de narrativa indicado
2. Busca en el mismo directorio un archivo con "arquitectura" en el nombre
   ├── Existe → lo usa como contexto para el evaluador
   └── No existe → evalúa solo con narrativa (con nota de limitación)
3. Crea casos/{slug}/correccion_{timestamp}/

Iteración 1:
  └── EVALUADOR → iter_01_evaluacion.md
       │
       ├── ✅ APTO     → guarda caso_corregido.md, termina
       ├── ❌ DESCARTAR → reporta razones, termina
       └── ⚠️ MEJORAR  → misma lógica de routing que /crear-caso:
            ├── falla arquitectura → ARQUITECTO → REDACTOR → volver a EVALUADOR
            └── solo narrativa → REDACTOR → volver a EVALUADOR

Iteración 2, 3... (máximo 5)
```

**Estructura de salida:**
```
casos/codex/
├── correccion_20260319_1430/
│   ├── iter_01_evaluacion.md
│   ├── iter_02_narrativa.md
│   ├── iter_02_evaluacion.md
│   └── ...
└── caso_corregido.md
```

**Diferencia clave con `/crear-caso`:** empieza desde el Evaluador, no desde el Arquitecto. Útil cuando ya tienes un caso escrito manualmente y quieres que el sistema lo evalúe y corrija.

---

### `/generar-imagenes <slug>`

Genera los prompts de Midjourney v6.1 de un caso ya aprobado. No regenera el caso.

**Ejemplo:**
```
/generar-imagenes codex
```

**Qué hace internamente:**

```
1. Verifica que exista casos/{slug}/caso_final.md y el arquitectura.md de la última iteración
2. Lanza el Agente Visual (Etapa 5) con narrativa + arquitectura como input
3. El agente escribe 3 archivos:
   casos/{slug}/imagenes/personajes.md
   casos/{slug}/imagenes/escenas.md
   casos/{slug}/imagenes/evidencias.md
4. Reporta conteo de prompts por archivo
```

Cada prompt de escena se deriva de la tabla de perspectivas del PASO B2 del Arquitecto — el mapa espacial es vinculante.

---

### Tabla comparativa

| | `/crear-caso` | `/corregir-caso` | `/generar-imagenes` |
|---|---|---|---|
| Punto de entrada | Arquitecto | Jugador | Generador de Imágenes |
| Input | Nombre del caso | Archivo de narrativa existente | Slug de un caso APTO |
| Output final | `caso_final.md` | `caso_corregido.md` | 3 archivos en `imagenes/` |
| Usa arquitectura previa | No (la genera) | Sí, si existe | Sí (obligatoria) |
| Iteraciones máx. | 5 | 5 | 1 (sin iteración) |

---

## Qué hace cada mejora de rendimiento

| Técnica | Dónde se aplica | Para qué sirve |
|---------|----------------|----------------|
| Chain of thought (3 soluciones previas) | Arquitecto Paso A | Evita elegir la primera idea |
| Mapa de contradicciones | Arquitecto Paso D | Diseña mentiras antes de redactar |
| Lista cerrada de personajes | Arquitecto Paso C | Impide personajes nuevos en testimonios |
| Ruta deductiva explícita | Arquitecto Paso F | Garantiza solución 100% deducible |
| Simulación del lector | Redactor, al final | Detecta si el caso es demasiado fácil |
| Mínimos de longitud | Redactor | Evita testimonios superficiales |
| Generación por etapas | Todo el flujo | Separa diseño lógico de redacción |
| Anti-continuidad | Redactor + Evaluador | Consistencia de personajes |
| Jugador ciego antes del Evaluador | Etapa 3 | Veredicto de dificultad sin sesgo cognitivo — no conoce la solución |
| Mapa espacial vinculante | Arquitecto Paso B2 + Redactor + Generador | Evita contradicciones entre narrativa e imágenes |
| Inventario visual automático | Generador de imágenes | Recorre la lista cerrada de personajes y evidencias |
| Prompts autosuficientes | Generador de imágenes | Cada prompt incluye el bloque de estilo fijo y funciona en aislamiento |
