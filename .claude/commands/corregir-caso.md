# Corregir Caso — Evaluación y corrección iterativa

**Uso:** `/corregir-caso casos/codex/narrativa.md`
(también acepta directorio: `/corregir-caso casos/codex/`)

El argumento es la ruta al archivo o directorio del caso: $ARGUMENTS

---

## Instrucciones de ejecución

Sigue estos pasos en orden. No los omitas ni combines.

### Paso 0 — Preparación

1. La ruta recibida es: **$ARGUMENTS**

2. **Determinar archivos:**
   - Si `$ARGUMENTS` es un directorio: busca en él un archivo con "narrativa" en el nombre → ese es el archivo de narrativa. Busca también uno con "arquitectura" en el nombre.
   - Si `$ARGUMENTS` es un archivo: ese es el archivo de narrativa. Busca en el mismo directorio un archivo con "arquitectura" en el nombre.

3. **Lee el archivo de narrativa** con el tool Read.

4. **Arquitectura:**
   - Si existe un archivo con "arquitectura" en el nombre en el mismo directorio: léelo → `tiene_arquitectura = true`
   - Si no existe: `tiene_arquitectura = false` (el evaluador evaluará solo con narrativa, con limitación anotada)

5. **Determinar slug:** extrae el nombre de la carpeta padre de la ruta (ej: `casos/codex/narrativa.md` → slug = `codex`).

6. **Timestamp:** usa el formato `YYYYMMDD_HHMM` (obtén fecha/hora actual con `date +%Y%m%d_%H%M`).

7. Crea directorio de corrección: `casos/{slug}/correccion_{timestamp}/`
   ```bash
   mkdir -p casos/{slug}/correccion_{timestamp}
   ```

8. Lee los cuatro archivos de prompt y extrae el bloque de código (entre las primeras ``` y las últimas ```) de cada uno:
   - `01_arquitecto.md` → system prompt del arquitecto
   - `02_redactor.md` → system prompt del redactor
   - `03_jugador.md` → system prompt del jugador
   - `04_evaluador_de_casos.md` → system prompt del evaluador

---

### Paso 1 — Bucle de corrección (máximo 5 iteraciones)

Inicializa: `iter = 1`, `feedback_arquitectura = ""`, `feedback_narrativa = ""`, `arquitectura_actual = {contenido leído en paso 0 o vacío}`, `narrativa_actual = {contenido leído en paso 0}`

Repite hasta APTO, DESCARTAR, o iter > 5:

---

#### 1a. JUGADOR

Usa el Agent tool (subagent_type: general-purpose) con:
- **System prompt:** contenido extraído de `03_jugador.md` (reemplaza `[PEGA AQUÍ EL CASO COMPLETO — SOLO LA NARRATIVA, SIN LA ARQUITECTURA INTERNA]` con el contenido de `narrativa_actual`)
- **User message:** *(vacío)*

⚠️ IMPORTANTE: El Jugador NO recibe arquitectura_actual. Solo recibe la narrativa.

Guarda el output en `casos/{slug}/correccion_{timestamp}/iter_{iter:02d}_jugador.md`

**Parsear veredicto del Jugador** — busca en `[REPORTE DEL JUGADOR]`:
- `VEREDICTO: FÁCIL` → veredicto_jugador = FÁCIL
- `VEREDICTO: CALIBRADO` → veredicto_jugador = CALIBRADO
- `VEREDICTO: DIFÍCIL` → veredicto_jugador = DIFÍCIL
- `VEREDICTO: IRRESOLUBLE` → veredicto_jugador = IRRESOLUBLE

**Si veredicto_jugador = FÁCIL:**
- Extrae del reporte la sección "SI EL VEREDICTO ES FÁCIL"
- `feedback_narrativa` += " El Jugador identificó el caso como FÁCIL. Oscurece la pista que delata demasiado: {texto extraído}."
- Continúa a 1c (ROUTING → Redactor en lugar de Evaluador)

**Si veredicto_jugador = IRRESOLUBLE:**
- Extrae del reporte la sección "SI EL VEREDICTO ES IRRESOLUBLE"
- `feedback_arquitectura` += " El Jugador no pudo llegar a ninguna conclusión. Información faltante: {texto extraído}."
- Continúa a 1c (ROUTING → Arquitecto)

**Si veredicto_jugador = CALIBRADO o DIFÍCIL:**
- Continúa a 1b (EVALUADOR)

---

#### 1b. EVALUADOR

Usa el Agent tool (subagent_type: general-purpose) con:
- **System prompt:** contenido extraído de `04_evaluador_de_casos.md` (reemplaza `[PEGA AQUÍ EL CASO COMPLETO]` con el contenido de `narrativa_actual`)
- **User message:**
  ```
  {si tiene_arquitectura:}
  ARQUITECTURA DEL CASO:
  {arquitectura_actual}

  NARRATIVA DEL CASO:
  {narrativa_actual}

  REPORTE DEL JUGADOR INDEPENDIENTE (Etapa 2.5):
  {contenido de iter_{iter:02d}_jugador.md}

  {si NO tiene_arquitectura:}
  NOTA: No se dispone de la arquitectura interna. Evalúa solo con la narrativa. Indica en tu evaluación esta limitación.

  NARRATIVA DEL CASO:
  {narrativa_actual}

  REPORTE DEL JUGADOR INDEPENDIENTE (Etapa 2.5):
  {contenido de iter_{iter:02d}_jugador.md}
  ```

Guarda el output en `casos/{slug}/correccion_{timestamp}/iter_{iter:02d}_evaluacion.md`

---

#### 1c. Parsear veredicto

Lee el archivo de evaluación y busca:

**En PASO 1:**
- `✅ APTO` → veredicto = APTO
- `❌ DESCARTAR` → veredicto = DESCARTAR
- `⚠️ MEJORAR` → veredicto = MEJORAR

**En PASO 14 (si veredicto = MEJORAR):**
- Si menciona "Etapa 1" o "volver a Etapa 1" → `falla_arquitectura = true`
- Si menciona "solo Etapa 2" o "solo a Etapa 2" o "solo narración" → `falla_arquitectura = false`
- Si menciona ambas etapas → `falla_arquitectura = true`
- Extrae el feedback específico de PASO 14

---

#### 1c. Routing

**Si veredicto = APTO:**
- Guarda `narrativa_actual` en `casos/{slug}/caso_corregido.md`
- Informa: "✅ Caso aprobado en iteración {iter}. Guardado en `casos/{slug}/caso_corregido.md`\n\n💡 Próximo paso opcional: ejecuta `/generar-imagenes {slug}` para crear los prompts de Midjourney del caso."
- TERMINAR

**Si veredicto = DESCARTAR:**
- Informa al usuario con las razones específicas del evaluador
- TERMINAR

**Si veredicto = MEJORAR o si el Jugador forzó routing (FÁCIL o IRRESOLUBLE):**

  **Si `falla_arquitectura = true` (fallo en arquitectura — por Evaluador o Jugador IRRESOLUBLE):**

  Usa Agent tool con system prompt de `01_arquitecto.md`:
  ```
  Corrige esta arquitectura de caso.

  ARQUITECTURA ACTUAL:
  {arquitectura_actual}

  FEEDBACK — problemas a corregir:
  {feedback_arquitectura}
  ```
  Guarda en `casos/{slug}/correccion_{timestamp}/iter_{iter:02d}_arquitectura.md`
  Actualiza `arquitectura_actual` con este nuevo contenido.

  Luego regenera narrativa con system prompt de `02_redactor.md`:
  ```
  {arquitectura_actual actualizada}

  FEEDBACK — problemas a corregir en narrativa:
  {feedback_narrativa, si lo hay}
  ```
  Guarda en `casos/{slug}/correccion_{timestamp}/iter_{iter:02d}_narrativa.md`
  Actualiza `narrativa_actual` con este nuevo contenido.

  **Si `falla_arquitectura = false` (solo corregir narrativa — por Evaluador o Jugador FÁCIL):**

  Usa Agent tool con system prompt de `02_redactor.md`:
  ```
  {arquitectura_actual}

  FEEDBACK — problemas a corregir:
  {feedback_narrativa}
  ```
  Guarda en `casos/{slug}/correccion_{timestamp}/iter_{iter:02d}_narrativa.md`
  Actualiza `narrativa_actual` con este nuevo contenido.

- `iter += 1`
- Continuar bucle (volver a 1a — Jugador primero — con los archivos actualizados)

**Si iter > 5:**
- Informa: "⚠️ Se alcanzó el máximo de 5 iteraciones sin lograr APTO. Última evaluación en `casos/{slug}/correccion_{timestamp}/iter_05_evaluacion.md`"
- TERMINAR

---

### Estructura de salida esperada

```
casos/{slug}/
├── correccion_{timestamp}/
│   ├── iter_01_jugador.md         ← nuevo
│   ├── iter_01_evaluacion.md
│   ├── iter_02_narrativa.md       ← si hubo corrección solo narrativa
│   ├── iter_02_jugador.md
│   ├── iter_02_evaluacion.md
│   ├── iter_03_arquitectura.md    ← si hubo corrección de arquitectura
│   ├── iter_03_narrativa.md
│   ├── iter_03_jugador.md
│   ├── iter_03_evaluacion.md
│   └── ...
└── caso_corregido.md              ← cuando evaluador dice APTO
```
