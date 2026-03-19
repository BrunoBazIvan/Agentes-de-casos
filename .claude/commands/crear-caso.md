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
4. Lee los tres archivos de prompt y extrae el bloque de código (entre las primeras ``` y las últimas ```) de cada uno:
   - `01_arquitecto.md` → system prompt del arquitecto
   - `02_redactor.md` → system prompt del redactor
   - `03_evaluador_de_casos.md` → system prompt del evaluador

### Paso 1 — Bucle de iteraciones (máximo 5)

Inicializa: `iter = 1`, `feedback_arquitectura = ""`, `feedback_narrativa = ""`

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

#### 1c. EVALUADOR

Usa el Agent tool (subagent_type: general-purpose) con:
- **System prompt:** contenido extraído de `03_evaluador_de_casos.md` (reemplaza `[PEGA AQUÍ EL CASO COMPLETO]` con el contenido de narrativa.md)
- **User message:**
  ```
  ARQUITECTURA DEL CASO:
  {contenido de arquitectura.md}

  NARRATIVA DEL CASO:
  {contenido de narrativa.md}
  ```

Guarda el output en `casos/{slug}/iter_{iter:02d}/evaluacion.md`

---

#### 1d. Parsear veredicto

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

#### 1e. Routing

**Si veredicto = APTO:**
- Copia `casos/{slug}/iter_{iter:02d}/narrativa.md` a `casos/{slug}/caso_final.md`
- Informa al usuario: "✅ Caso **$ARGUMENTS** aprobado en iteración {iter}. Guardado en `casos/{slug}/caso_final.md`"
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

### Resumen de estructura de salida esperada

```
casos/{slug}/
├── iter_01/
│   ├── arquitectura.md
│   ├── narrativa.md
│   └── evaluacion.md
├── iter_02/          ← si hubo correcciones
│   └── ...
└── caso_final.md     ← cuando evaluador dice APTO
```
