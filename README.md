# Prompts — Juego de Detectives

---

## Archivos

| Archivo | Etapa | Uso |
|---------|-------|-----|
| `00_concepto_del_juego.md` | — | Concepto, modelo de negocio y loop semanal |
| `01_arquitecto.md` | Etapa 1 | Diseña la lógica interna del caso |
| `02_redactor.md` | Etapa 2 | Redacta el caso narrativo para el jugador |
| `03_evaluador_de_casos.md` | Etapa 3 | Evalúa y aprueba el caso |
| `04_generador_imagenes.md` | Etapa 4 | Genera todos los prompts de imagen del caso |
| `05_estilo_forence_referencia.md` | Referencia | Guía de estilo visual forense + ejemplo aplicado |

---

## Flujo de trabajo completo

```
┌─────────────────────────────────────────────────────────────┐
│  ETAPA 1 — Arquitecto                                       │
│  Input: ninguno (o feedback del Evaluador si es iteración)  │
│  Output: solución, personajes, mapa de contradicciones,     │
│          línea de tiempo, ruta deductiva, error óptimo      │
└──────────────────────────┬──────────────────────────────────┘
                           │ pega el output completo
                           ▼
┌─────────────────────────────────────────────────────────────┐
│  ETAPA 2 — Redactor                                         │
│  Input: output del Arquitecto                               │
│  Output: caso narrativo completo para el jugador            │
│  (incidente, víctima, sospechosos, testimonios,             │
│   interrogatorios, evidencias)                              │
└──────────────────────────┬──────────────────────────────────┘
                           │ pega el caso generado
                           ▼
┌─────────────────────────────────────────────────────────────┐
│  ETAPA 3 — Evaluador                                        │
│  Input: caso del Redactor                                   │
│  Output: ✅ APTO / ⚠️ MEJORAR / ❌ DESCARTAR + feedback     │
└──────────────────────────┬──────────────────────────────────┘
                           │
               ┌───────────┴───────────┐
               ▼                       ▼
          ✅ APTO                ⚠️ / ❌ + feedback
               │                Volver a Etapa 1
               │                con el feedback
               ▼                como input adicional
┌─────────────────────────────────────────────────────────────┐
│  ETAPA 4 — Generador de Imágenes                            │
│  Input: caso aprobado                                       │
│  Output: prompts listos para cada imagen del caso           │
│  ├── 🏚️  Escena del crimen (plano general + detalle)        │
│  ├── 🔍  Evidencias (una por evidencia física)              │
│  ├── 🧑  Sospechosos (ficha policial + foto de contexto)    │
│  └── 👁️  Testigos (foto naturalista por testigo)            │
└─────────────────────────────────────────────────────────────┘
                           │
                           ▼
              Usar prompts en Midjourney /
              DALL·E / Stable Diffusion / Grok
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

## Imágenes que genera la Etapa 4 por caso

| Categoría | Cantidad mínima | Estilo |
|-----------|----------------|--------|
| Escena del crimen | 2–3 | Forense documental |
| Evidencias | 1 por evidencia física | Macro forense |
| Sospechosos | 4+ (2 opciones c/u) | Ficha policial + contexto |
| Testigos | 5+ | Naturalista documental |
| Hoja de expediente | 1 (opcional) | Documento A4 policial |

---

## Slash Commands de Claude Code

Dos comandos que orquestan el pipeline completo directamente desde Claude Code, sin intervención manual entre etapas.

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
│   └── evaluacion.md
├── iter_02/          ← si hubo correcciones
│   └── ...
└── caso_final.md     ← cuando el evaluador aprueba
```

**Lógica de routing:** el comando lee el PASO 1 del evaluador para el veredicto (`✅/⚠️/❌`) y el PASO 14 para decidir si el fallo está en la arquitectura (Etapa 1), en la narrativa (Etapa 2), o en ambas. Eso determina desde qué etapa se relanza la siguiente iteración.

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

### Tabla comparativa

| | `/crear-caso` | `/corregir-caso` |
|---|---|---|
| Punto de entrada | Arquitecto | Evaluador |
| Input | Nombre del caso | Archivo de narrativa existente |
| Output final | `caso_final.md` | `caso_corregido.md` |
| Usa arquitectura previa | No (la genera) | Sí, si existe en el directorio |
| Iteraciones máx. | 5 | 5 |

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
| Inventario visual automático | Generador de imágenes | No se olvida ninguna imagen necesaria |
| Prompts autosuficientes | Generador de imágenes | Cada prompt funciona solo en el generador |
