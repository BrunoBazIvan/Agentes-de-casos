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

8. Lee los tres archivos de prompt y extrae el bloque de código (entre las primeras ``` y las últimas ```) de cada uno:
   - `01_arquitecto.md` → system prompt del arquitecto
   - `02_redactor.md` → system prompt del redactor
   - `03_evaluador_de_casos.md` → system prompt del evaluador

---

### Paso 1 — Bucle de corrección (máximo 5 iteraciones)

Inicializa: `iter = 1`, `feedback_arquitectura = ""`, `feedback_narrativa = ""`, `arquitectura_actual = {contenido leído en paso 0 o vacío}`, `narrativa_actual = {contenido leído en paso 0}`

Repite hasta APTO, DESCARTAR, o iter > 5:

---

#### 1a. EVALUADOR

Usa el Agent tool (subagent_type: general-purpose) con:
- **System prompt:** contenido extraído de `03_evaluador_de_casos.md` (reemplaza `[PEGA AQUÍ EL CASO COMPLETO]` con el contenido de `narrativa_actual`)
- **User message:**
  ```
  {si tiene_arquitectura:}
  ARQUITECTURA DEL CASO:
  {arquitectura_actual}

  NARRATIVA DEL CASO:
  {narrativa_actual}

  {si NO tiene_arquitectura:}
  NOTA: No se dispone de la arquitectura interna. Evalúa solo con la narrativa. Indica en tu evaluación esta limitación.

  NARRATIVA DEL CASO:
  {narrativa_actual}
  ```

Guarda el output en `casos/{slug}/correccion_{timestamp}/iter_{iter:02d}_evaluacion.md`

---

#### 1b. Parsear veredicto

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
- Informa: "✅ Caso aprobado en iteración {iter}. Guardado en `casos/{slug}/caso_corregido.md`"
- TERMINAR

**Si veredicto = DESCARTAR:**
- Informa al usuario con las razones específicas del evaluador
- TERMINAR

**Si veredicto = MEJORAR:**

  **Si `falla_arquitectura = true` (hay que corregir arquitectura):**

  Usa Agent tool con system prompt de `01_arquitecto.md`:
  ```
  Corrige esta arquitectura de caso.

  ARQUITECTURA ACTUAL:
  {arquitectura_actual}

  FEEDBACK DEL EVALUADOR — problemas a corregir:
  {feedback de PASO 14 relacionado con arquitectura}
  ```
  Guarda en `casos/{slug}/correccion_{timestamp}/iter_{iter:02d}_arquitectura.md`
  Actualiza `arquitectura_actual` con este nuevo contenido.

  Luego regenera narrativa con system prompt de `02_redactor.md`:
  ```
  {arquitectura_actual actualizada}

  FEEDBACK DEL EVALUADOR — problemas a corregir en narrativa:
  {feedback de PASO 14 relacionado con narrativa, si lo hay}
  ```
  Guarda en `casos/{slug}/correccion_{timestamp}/iter_{iter:02d}_narrativa.md`
  Actualiza `narrativa_actual` con este nuevo contenido.

  **Si `falla_arquitectura = false` (solo corregir narrativa):**

  Usa Agent tool con system prompt de `02_redactor.md`:
  ```
  {arquitectura_actual}

  FEEDBACK DEL EVALUADOR — problemas a corregir:
  {feedback completo de PASO 14}
  ```
  Guarda en `casos/{slug}/correccion_{timestamp}/iter_{iter:02d}_narrativa.md`
  Actualiza `narrativa_actual` con este nuevo contenido.

- `iter += 1`
- Continuar bucle (volver a 1a con los archivos actualizados)

**Si iter > 5:**
- Informa: "⚠️ Se alcanzó el máximo de 5 iteraciones sin lograr APTO. Última evaluación en `casos/{slug}/correccion_{timestamp}/iter_05_evaluacion.md`"
- TERMINAR

---

### Estructura de salida esperada

```
casos/{slug}/
├── correccion_{timestamp}/
│   ├── iter_01_evaluacion.md
│   ├── iter_02_narrativa.md      ← si hubo corrección solo narrativa
│   ├── iter_02_evaluacion.md
│   ├── iter_03_arquitectura.md   ← si hubo corrección de arquitectura
│   ├── iter_03_narrativa.md
│   ├── iter_03_evaluacion.md
│   └── ...
└── caso_corregido.md             ← cuando evaluador dice APTO
```
