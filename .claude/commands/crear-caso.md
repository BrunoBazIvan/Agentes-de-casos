# Crear Caso — Orquestador completo

**Uso:** `/crear-caso "El Reloj de Medianoche"`

El argumento es el nombre del caso: $ARGUMENTS

---

## Instrucciones de ejecución

Sigue estos pasos en orden. No los omitas ni combines.

### Paso 0 — Preparación

1. El nombre del caso es: **$ARGUMENTS**
2. Genera el slug: nombre en minúsculas, sin tildes, espacios reemplazados por `_`, sin caracteres especiales.
   - Ejemplo: "El Reloj de Medianoche" → `el_reloj_de_medianoche`
3. Crea el directorio base `casos/{slug}/` si no existe (usa Bash: `mkdir -p casos/{slug}`)
4. Lee los cuatro archivos de prompt y extrae el bloque de código (entre las primeras ``` y las últimas ```) de cada uno:
   - `01_arquitecto.md` → system prompt del arquitecto
   - `02_redactor.md` → system prompt del redactor
   - `03_jugador.md` → system prompt del jugador
   - `04_evaluador_de_casos.md` → system prompt del evaluador

### Paso 1 — Bucle de iteraciones (máximo 5)

Inicializa: `iter = 1`, `feedback_arquitectura = ""`, `feedback_narrativa = ""`, `saltar_arquitecto = false`

Repite hasta APTO, DESCARTAR, o iter > 5:

---

#### 1a. ARQUITECTO (saltar si `saltar_arquitecto = true`)

Si `saltar_arquitecto` NO está activo:

Usa el Agent tool (subagent_type: general-purpose) con:
- **System prompt:** contenido extraído de `01_arquitecto.md`
- **User message:**
  ```
  Genera caso: $ARGUMENTS

  {si feedback_arquitectura no está vacío:}
  ---
  FEEDBACK DE ITERACIÓN ANTERIOR — corrige estos problemas:
  {feedback_arquitectura}
  ```

Guarda el output en `casos/{slug}/iter_{iter:02d}/arquitectura.md`

---

#### 1b. REDACTOR

Usa el Agent tool (subagent_type: general-purpose) con:
- **System prompt:** contenido extraído de `02_redactor.md`
- **User message:**
  ```
  {contenido completo de arquitectura.md de esta iteración}

  {si feedback_narrativa no está vacío:}
  ---
  FEEDBACK DE ITERACIÓN ANTERIOR — corrige estos problemas:
  {feedback_narrativa}
  ```

Guarda el output en `casos/{slug}/iter_{iter:02d}/narrativa.md`

---

#### 1c. JUGADOR

Usa el Agent tool (subagent_type: general-purpose) con:
- **System prompt:** contenido extraído de `03_jugador.md` (reemplaza `[PEGA AQUÍ EL CASO COMPLETO — SOLO LA NARRATIVA, SIN LA ARQUITECTURA INTERNA]` con el contenido de narrativa.md)
- **User message:** *(vacío — el caso ya está en el system prompt)*

⚠️ IMPORTANTE: El Jugador NO recibe el contenido de arquitectura.md. Solo recibe la narrativa.

Guarda el output en `casos/{slug}/iter_{iter:02d}/jugador.md`

---

#### 1d. Parsear veredicto del Jugador

Lee `casos/{slug}/iter_{iter:02d}/jugador.md` y busca en la sección `[REPORTE DEL JUGADOR]`:

- `VEREDICTO: FÁCIL` → veredicto_jugador = FÁCIL
- `VEREDICTO: CALIBRADO` → veredicto_jugador = CALIBRADO
- `VEREDICTO: DIFÍCIL` → veredicto_jugador = DIFÍCIL
- `VEREDICTO: IRRESOLUBLE` → veredicto_jugador = IRRESOLUBLE

**Routing del Jugador:**

**Si veredicto_jugador = FÁCIL:**
- Extrae del reporte la sección "SI EL VEREDICTO ES FÁCIL" para obtener qué pista/sección delata demasiado
- `feedback_narrativa` = "El Jugador identificó el caso como FÁCIL. Pista o sección que delata demasiado: {texto extraído}. Oscurece esa pista o refuerza el error óptimo antes de que el Evaluador lo vea."
- `saltar_arquitecto = true`
- `iter += 1`
- **Vuelve a 1b (REDACTOR)** — no pasa por el Evaluador

**Si veredicto_jugador = IRRESOLUBLE:**
- Extrae del reporte la sección "SI EL VEREDICTO ES IRRESOLUBLE"
- `feedback_arquitectura` = "El Jugador no pudo llegar a ninguna conclusión defendible. Información que faltó: {texto extraído}. Revisa la ruta deductiva y asegúrate de que la solución sea deducible con la información disponible."
- `saltar_arquitecto = false`
- `iter += 1`
- **Vuelve a 1a (ARQUITECTO)**

**Si veredicto_jugador = CALIBRADO o DIFÍCIL:**
- Continúa a 1e (EVALUADOR)

---

#### 1e. EVALUADOR

Usa el Agent tool (subagent_type: general-purpose) con:
- **System prompt:** contenido extraído de `04_evaluador_de_casos.md` (reemplaza `[PEGA AQUÍ EL CASO COMPLETO]` con el contenido de narrativa.md)
- **User message:**
  ```
  ARQUITECTURA DEL CASO:
  {contenido de arquitectura.md}

  NARRATIVA DEL CASO:
  {contenido de narrativa.md}

  REPORTE DEL JUGADOR INDEPENDIENTE (Etapa 2.5):
  {contenido de jugador.md}
  ```

Guarda el output en `casos/{slug}/iter_{iter:02d}/evaluacion.md`

---

#### 1f. Parsear veredicto del Evaluador

Lee `casos/{slug}/iter_{iter:02d}/evaluacion.md` y busca:

**En PASO 1:**
- `✅ APTO` → veredicto = APTO
- `❌ DESCARTAR` → veredicto = DESCARTAR
- `⚠️ MEJORAR` → veredicto = MEJORAR

**En PASO 14 (si veredicto = MEJORAR):**
- Si menciona "Etapa 1" o "volver a Etapa 1" → `falla_arquitectura = true`
- Si menciona "solo Etapa 2" o "solo a Etapa 2" o "solo narración" → `falla_arquitectura = false`
- Si menciona ambas etapas → `falla_arquitectura = true`
- Extrae el feedback específico de PASO 14 para usar en la siguiente iteración

---

#### 1g. Routing del Evaluador

**Si veredicto = APTO:**
- Copia `casos/{slug}/iter_{iter:02d}/narrativa.md` a `casos/{slug}/caso_final.md`
- **Actualiza el registro** (ver Paso 2)
- Informa al usuario: "✅ Caso **$ARGUMENTS** aprobado en iteración {iter}. Guardado en `casos/{slug}/caso_final.md`\n\n💡 Próximo paso opcional: ejecuta `/generar-imagenes {slug}` para crear los prompts de Midjourney del caso."
- TERMINAR

**Si veredicto = DESCARTAR:**
- Informa al usuario con las razones específicas del evaluador
- TERMINAR

**Si veredicto = MEJORAR:**
- Si `falla_arquitectura = true`:
  - `saltar_arquitecto = false`
  - `feedback_arquitectura` = feedback de PASO 14 relacionado con la arquitectura
  - `feedback_narrativa` = feedback de PASO 14 relacionado con la narrativa (si lo hay)
- Si `falla_arquitectura = false`:
  - `saltar_arquitecto = true`
  - `feedback_narrativa` = feedback completo de PASO 14
- `iter += 1`
- Continuar bucle

**Si iter > 5:**
- Informa: "⚠️ Se alcanzó el máximo de 5 iteraciones sin lograr APTO. Última evaluación en `casos/{slug}/iter_05/evaluacion.md`"
- TERMINAR

---

### Paso 2 — Actualizar el registro de patrones

Solo ejecutar si el caso fue aprobado (veredicto = APTO).

1. Lee `casos/_registro.md`
2. Lee `casos/{slug}/iter_{iter:02d}/arquitectura.md` para extraer:
   - `culpable_tipo`: tipo de culpable (amante / socio / familiar / desconocido / empleado / rival / otro)
   - `metodo`: método del crimen
   - `escenario`: tipo de escenario
   - `motivo_tipo`: tipo de motivo real
   - `error_optimo`: nombre del sospechoso trampa principal (del PASO H)
3. Lee `casos/{slug}/iter_{iter:02d}/jugador.md` para extraer `dificultad_jugador`
4. Agrega al final de `casos/_registro.md`:

```
## {nombre del caso} — {fecha YYYY-MM-DD}
- culpable_tipo: {valor}
- metodo: {valor}
- escenario: {valor}
- motivo_tipo: {valor}
- dificultad_jugador: {valor del VEREDICTO del jugador de la última iteración aprobada}
- error_optimo: {nombre del sospechoso trampa}
- iteraciones: {número total de iteraciones}
```

---

### Resumen de estructura de salida esperada

```
casos/{slug}/
├── iter_01/
│   ├── arquitectura.md
│   ├── narrativa.md
│   ├── jugador.md         ← nuevo
│   └── evaluacion.md
├── iter_02/          ← si hubo correcciones
│   └── ...
└── caso_final.md     ← cuando evaluador dice APTO
casos/_registro.md    ← actualizado al aprobar
```
