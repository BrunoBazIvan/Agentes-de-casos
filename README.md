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
