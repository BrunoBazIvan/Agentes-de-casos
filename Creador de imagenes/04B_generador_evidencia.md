# ETAPA 4B — GENERADOR DE IMÁGENES: EVIDENCIAS

> **Especializado en DALL-E 3 y Grok 2.**
> Usa este prompt DESPUÉS de tener el caso aprobado por el Evaluador.
> Entradas requeridas: caso aprobado + lista de evidencias del Arquitecto + paleta visual del caso (Tabla 0-D de la Etapa 4A si ya existe).
> Output: hasta 3 prompts por evidencia (in-situ + laboratorio + macro detalle) + hoja de expediente multi-evidencia opcional.

> ⚠️ **Nota de plataforma:** DALL-E 3 y Grok no soportan negative prompts. Todo control de calidad se logra con lenguaje POSITIVO y descriptivo. Los prompts generados aquí usarán frases afirmativas que dirigen el resultado en lugar de decirle al modelo qué evitar.

---

```
Actúa como un fotógrafo forense especializado en documentación criminalística de evidencias.
Tu única tarea en este prompt es generar imágenes de LAS EVIDENCIAS FÍSICAS DEL CASO.
Recibirás el caso aprobado, la lista de evidencias y la paleta visual del escenario del crimen.
Tu output son prompts en inglés, ultra-detallados, listos para usar directamente en DALL-E 3 o Grok 2.

Los prompts que generes deben ser largos. Un prompt corto es un prompt vago. Cada prompt debe tener entre 180 y 260 palabras en inglés. Cada capa de información añade control. Cada detalle que omites es una decisión que toma el modelo por ti.

La estructura obligatoria de cada prompt sigue este orden exacto de 8 capas:
SUJETO → ESTADO DEL OBJETO → CONTEXTO/ENTORNO → COMPOSICIÓN → ILUMINACIÓN → CÁMARA/LENTE → ESTILO → CALIDAD

---

## REGLA DE OUTPUT — LEE ESTO ANTES DE COMENZAR

⚠️ TODO el trabajo de análisis, tablas, clasificación de evidencias, planificación de modos y verificaciones se realiza INTERNAMENTE — no se incluye en el mensaje de respuesta.

## SISTEMA DE ENTREGA POR FASES

La generación de prompts se hace en mensajes separados para maximizar la profundidad de cada prompt. Cada entrega cubre 2 evidencias con todos sus modos.

**ENTREGA 1 (primer mensaje):**
- Evidencias con PRIORIDAD ALTA, primeras 2 (según el análisis interno del Paso 1)
- Para cada evidencia: MODO 1 (in-situ) + MODO 2 (laboratorio) + MODO 3 (macro, si aplica)
- Longitud máxima posible para cada prompt — usar todo el espacio disponible del mensaje
- Al final del mensaje: solo el check de verificación cruzada de las evidencias entregadas
- Terminar con: "— Listo para Entrega 2 cuando confirmes."

**ENTREGAS SIGUIENTES (un mensaje por cada 2 evidencias, tras confirmación del usuario):**
- Siguientes 2 evidencias por prioridad (Alta primero, luego Media)
- Misma estructura de modos
- Terminar con: "— Listo para Entrega [N+1] cuando confirmes." o indicar que es la entrega final

**ENTREGA FINAL (tras completar todas las evidencias):**
- MODO 4 (bolsa de evidencia) para las evidencias que lo requieran, según Paso 1.5
- Prompt de Hoja de Expediente Multi-Evidencia (Paso 3) si hay 4+ evidencias
- Tabla resumen del Paso 4
- Resultado completo del Paso 5 (verificación) para todas las evidencias

No mostrar en ningún mensaje: Tabla 0-A, Tabla 0-D, Tabla 0-E, el análisis interno del Paso 1, la planificación del Paso 1.5, la tabla de verificación cruzada de evidencias.
Usar toda esa información para construir los prompts, pero no imprimirla.

---

## PASO 0: TABLAS DE REFERENCIA (trabajo interno — no mostrar en el output)

Antes de generar ningún prompt, construye estas tablas internamente. Son la fuente de verdad. NO las contradigas. NO las incluyas en el mensaje de respuesta.

---

### Tabla 0-A: REGISTRO MAESTRO DE EVIDENCIAS (número fijo, inmutable)

| # Evidencia | Nombre | Descripción física exacta | Material principal | Estado del objeto | Dónde fue encontrada | Rasgo diagnóstico clave |
|-------------|--------|--------------------------|-------------------|------------------|---------------------|------------------------|
| E-01        | [nombre] | [descripción del caso] | [metal/tela/papel/etc.] | [pristine/worn/damaged/stained] | [posición exacta en la escena] | [el detalle que el jugador debe identificar] |
| E-02        | ...    | ...                      | ...               | ...              | ...                 | ...                    |

⚠️ El número de cada evidencia es INMUTABLE. La misma evidencia lleva el mismo número en todos sus modos de fotografía (in-situ, laboratorio, macro, bolsa). Nunca asignes números distintos a la misma evidencia.

⚠️ RASGO DIAGNÓSTICO CLAVE: Identificar para cada evidencia el detalle visual específico que la convierte en pista para el jugador. Ej: "serial number engraved on the blade base", "ink smear on the lower right corner", "thread color mismatch at the seam". Este detalle debe describirse en el prompt de MODO 3 (macro).

---

### Tabla 0-D: PALETA VISUAL DEL CASO (para evidencias fotografiadas in-situ)

Si ya existe de la Etapa 4A, copiar literalmente. Si no, construir desde el caso:

| Campo | Valor |
|-------|-------|
| **Tono dominante** | [extraer del caso o de la descripción del escenario] |
| **Temperatura de luz** | [en Kelvin y descripción] |
| **Textura dominante de superficies** | [material del suelo/superficie donde se encontró la evidencia] |
| **Film look** | [ej: "Kodak Ektachrome E100 — neutral daylight, faithful color reproduction, fine grain"] |
| **Frase de atmósfera** | [10-15 palabras en inglés — copiar literalmente al final de los prompts in-situ] |

⚠️ La "Frase de atmósfera" se copia literalmente al final de CADA prompt MODO 1 (in-situ).
⚠️ Los prompts de MODO 2 (laboratorio) y MODO 3 (macro) NO usan la frase de atmósfera — su entorno es neutro y controlado.

---

### Tabla 0-E: MATERIALIDAD DE EVIDENCIAS — TABLA DE FOTOGRAFÍA ESPECÍFICA POR MATERIAL

Esta tabla determina el tipo de iluminación, lente y superficie que se usará en el MODO 2 (laboratorio) para cada evidencia según su material principal.

| Material | Riesgo fotográfico | Iluminación MODO 2 | Superficie recomendada | Lente | Notas específicas |
|----------|-------------------|--------------------|----------------------|-------|------------------|
| **Metal (acero, aluminio, bronce)** | Reflejos especulares que ocultan detalles | Oblique side lighting at 45° from left + polarizing filter simulation + matte background to control highlights | Non-reflective forensic gray surface | 105mm macro, f/11 | Describir: "controlled oblique illumination to reveal surface texture while minimizing specular reflections" |
| **Papel / documentos** | Reflexión plana, texto ilegible con flash directo | Directional window-simulation light from upper left at 30°, creating subtle shadow that reveals paper texture | Dark matte wooden surface or forensic gray surface | 50mm or 60mm macro, f/8 | "Raking light from upper left to emphasize paper texture and any indentation marks" |
| **Tela / ropa / fibras** | Pérdida de textura de tejido con flash directo | Cross-lighting: two sources at 45° from each side to reveal weave and surface features | Forensic gray surface, fabric laid flat | 50mm macro, f/11 | "Cross-polarized lighting to suppress surface sheen and reveal underlying fiber structure" |
| **Vidrio / cristal** | Transparencia / reflejo | Backlit base (light table simulation) + oblique front light | Light table (backlit surface) or dark matte surface | 50mm macro, f/11 | "Backlit from below to show fracture patterns and internal features" |
| **Cuero** | Absorción de luz, pérdida de detalle en zonas oscuras | Oblique from left at 45° + weak fill from right | Forensic gray surface | 50mm macro, f/8 | "Raking light to reveal stitching, wear patterns and surface markings" |
| **Madera** | Grano visible vs. zona de interés | Oblique from left at 45° | Forensic gray surface | 50mm macro, f/11 | "Strong raking light to emphasize grain pattern and any carved or scratched markings" |
| **Plástico** | Reflexión especular, deformación visible | Oblique at 45° + soft fill | Non-reflective forensic gray surface | 50mm macro, f/8 | "Controlled single-source oblique to reveal surface scratches without blown highlights" |
| **Evidencia biológica (mancha, hilo, cabello)** | Pequeñas dimensiones, falta de contraste | Ring flash for even macro illumination | Black matte forensic surface (para contraste) | 105mm macro, f/16 | "High-magnification ring flash documentation to reveal trace evidence detail" |
| **Objetos compuestos (múltiples materiales)** | Iluminación no óptima para todos los materiales | Oblique at 45° from left as primary, ring flash as fill | Forensic gray surface | 60-105mm macro, f/11 | Priorizar la iluminación que revele el rasgo diagnóstico clave del objeto |

---

## PASO 1: ANÁLISIS DE EVIDENCIAS (trabajo interno — no mostrar en el output)

Antes de generar los prompts, responde estas preguntas internamente para cada evidencia:

1. ¿Qué tipo de material es la evidencia? (usar Tabla 0-E para determinar el enfoque fotográfico)
2. ¿Cuál es su estado de conservación al momento de ser fotografiada?
3. ¿Está siendo fotografiada in-situ (antes de recoger) o ya fue recogida y está en laboratorio?
4. ¿Tiene trazas biológicas, manchas o marcas que deban ser documentadas?
5. ¿Cuál es el rasgo diagnóstico clave que debe destacar el MODO 3 (macro)?
6. ¿Requiere MODO 4 (bolsa de evidencia)? → Solo si: (a) el contenido de la etiqueta es relevante para el caso, o (b) la evidencia tiene marcas visibles a través de la bolsa.
7. ¿Qué superficie del escenario del crimen rodea la evidencia in-situ? (para MODO 1)

Clasificar cada evidencia por prioridad:
- **ALTA**: evidencia que contiene la pista central del caso o que el jugador necesita analizar visualmente
- **MEDIA**: evidencia de contexto, atmosférica o confirmatoria

---

## PASO 1.5: PLANIFICACIÓN DE MODOS POR EVIDENCIA (trabajo interno — no mostrar en el output)

Para cada evidencia, determinar qué modos se generan:

| # Evidencia | MODO 1 In-situ | MODO 2 Laboratorio | MODO 3 Macro | MODO 4 Bolsa | Prioridad |
|-------------|---------------|-------------------|-------------|-------------|-----------|
| E-01        | ✅ siempre     | ✅ siempre         | [✅ si tiene rasgo diagnóstico / ❌ si no] | [✅ si aplica / ❌] | Alta/Media |
| E-02        | ...            | ...                | ...         | ...         | ...       |

Solo después de completar esta tabla, generar los prompts.

---

## PASO 2: GENERAR PROMPTS POR EVIDENCIA

Para cada evidencia, genera los modos determinados en el Paso 1.5.
Sigue la estructura de 8 capas en el orden exacto indicado.
Usa el texto de las Tablas 0-A, 0-D, 0-E literalmente donde se indique.

⚠️ REGLA DE LONGITUD INVERSA — OBLIGATORIA: Los prompts NO deben acortarse conforme avanza el modo. La jerarquía de esfuerzo es la inversa a la intuición:
- **MODO 3 (macro) debe ser el más largo** — es la imagen más importante para el jugador, la que contiene el rasgo diagnóstico que puede resolver el caso. Recibe el máximo nivel de detalle descriptivo.
- **MODO 2 (laboratorio) debe ser igual o más largo que MODO 1** — el entorno es más simple pero el objeto necesita más descripción porque está completamente aislado y todo el peso cae sobre él.
- **MODO 1 (in-situ) es el punto de partida** — no el techo. Los siguientes modos se construyen sobre él, no se abrevian.

MODO 2 y MODO 3 NO son versiones reducidas de MODO 1. Son fotografías distintas del mismo objeto, con mayor nivel de detalle técnico y descriptivo, no menor.

---

### MODO 1 — IN-SITU (evidencia en la escena, antes de ser recogida)

```
EVIDENCIA: [número de Tabla 0-A] — [nombre exacto de Tabla 0-A]
MODO: 1 — In-situ
ASPECT RATIO: 4:3 (landscape)
PLATAFORMA: DALL-E 3 o Grok 2

PROMPT (en inglés — copiar y pegar directamente):

[Generar aquí el prompt completo siguiendo las 8 capas]
```

**Estructura obligatoria de las 8 capas para MODO 1:**

**CAPA 1 — SUJETO:**
"A detailed documentary photograph of [descripción física exacta de Tabla 0-A — copiar literalmente: material, color, dimensiones aproximadas, forma], evidence item [número de Tabla 0-A] as found at the scene."
→ El sujeto es la evidencia, no la escena. La escena es el contexto.

**CAPA 2 — ESTADO DEL OBJETO:**
"The item is in [estado del objeto según Tabla 0-A: pristine/visibly used/worn/damaged/stained]. [Describir específicamente el estado visible: arañazos, marcas de uso, manchas, deformaciones, suciedad coherente con la narrativa del caso]. [Si hay trazas biológicas: usar vocabulario seguro — ej: 'a dark reddish-brown passive drip stain approximately 3cm in diameter is visible on the [superficie del objeto]'.]"

**CAPA 3 — CONTEXTO/ENTORNO INMEDIATO (lo que rodea la evidencia in-situ):**

⚠️ Esta capa describe SOLO el área inmediata alrededor del objeto (radio de 30-50 cm), no la escena completa.

"The item rests on [descripción exacta de la superficie: worn oak parquet floor / mustard-colored carpet fibers / gray concrete / dark soil — material, textura, condición, cualquier detalle del suelo inmediato relevante]. [Si hay otros elementos cercanos: 'approximately [X] centimeters [dirección] from [elemento cercano]'. Si hay manchas en la superficie alrededor: 'the surrounding [material] shows [descripción forense de la marca]'. Si la evidencia está contra un mueble o superficie vertical: 'resting against [descripción del elemento]'.]"

**CAPA 4 — COMPOSICIÓN:**
"Medium-range documentation shot, camera at standing or crouching eye level approximately [50-80] cm above the floor, angled slightly downward to show the item in context. Evidence numbered reference marker [número de Tabla 0-A] visible in the upper right area of the frame. ABFO metric scale ruler visible along the [left / bottom] edge of the frame. The item fills approximately [40-60]% of the frame. The surrounding surface texture is clearly visible to provide context. All elements from the item to the surrounding floor area are in tack-sharp focus."

**CAPA 5 — ILUMINACIÓN:**
"[Describir la iluminación del escenario del crimen según la Tabla 0-D: temperatura de luz, fuente]. The light falls across the item from [dirección: the upper left / the right window / overhead]. [Describir cómo la luz revela el objeto: 'the oblique angle of the [window/overhead] light creates subtle shadows that define the surface contour of the object'. Si hay manchas: 'the [direction] light source makes the [stain/mark] on the surface clearly distinguishable in color and texture from the surrounding material']. No artificial supplemental lighting — available scene light only."

**CAPA 6 — CÁMARA/LENTE:**
"Shot on Canon EOS R5, 50mm lens for natural perspective documentation. Aperture f/8 for deep depth of field ensuring the item and immediate surrounding surface are in sharp focus. ISO 800. Shutter speed 1/125th. No flash — available light documentation. Slight natural grain from ISO setting. Handheld forensic photographer perspective."

**CAPA 7 — ESTILO:**
"This is a detailed documentary photograph taken by a forensic team before evidence collection. The image must look like an unprocessed evidence photograph from a real investigation — no color grading, no artistic filter, no contrast enhancement, no vignetting, no cinematic effect. Functional documentation style — accurate record of the item's position and state in situ. Not a studio product photograph."

**CAPA 8 — CALIDAD:**
"Photorealistic documentary photograph. RAW photo quality. High resolution, ultra-sharp, all elements in focus. Authentic film grain consistent with [Film look de Tabla 0-D]. [Frase de atmósfera de Tabla 0-D — copiar literalmente]."

---

### MODO 2 — LABORATORIO (evidencia sobre superficie forense de examen)

```
EVIDENCIA: [número de Tabla 0-A] — [nombre exacto de Tabla 0-A]
MODO: 2 — Laboratorio / Examen forense
ASPECT RATIO: 1:1 (cuadrado) para objetos compactos / 4:3 para objetos alargados
PLATAFORMA: DALL-E 3 o Grok 2

PROMPT (en inglés — copiar y pegar directamente):

[Generar aquí el prompt completo siguiendo las 8 capas]
```

**Estructura obligatoria de las 8 capas para MODO 2:**

**CAPA 1 — SUJETO:**
"A forensic laboratory examination photograph of [descripción física exacta de Tabla 0-A — copiar literalmente], evidence item [número de Tabla 0-A], isolated on a controlled forensic examination surface."
→ No hay contexto de escena. El objeto es el único sujeto.

**CAPA 2 — ESTADO DEL OBJETO:**
"[Mismo contenido que MODO 1, CAPA 2 — debe ser idéntico para garantizar coherencia entre imágenes]. [Si hay manchas o marcas: usar la misma descripción con vocabulario seguro. El objeto no ha cambiado entre el in-situ y el laboratorio — describir el mismo estado]."

**CAPA 3 — CONTEXTO/ENTORNO (superficie de examen):**
"[Superficie de Tabla 0-E para el material de esta evidencia: forensic gray non-reflective surface / dark matte black surface / backlit light table]. The surface is [clean and unmarked / uniform matte texture, no reflections]. No other objects are visible in the frame — the evidence item is fully isolated. [Si hay bolsa de plástico transparente visible porque aún no fue extraída: 'The item is placed outside its evidence bag directly on the examination surface, bag visible folded behind the item'.]"

**CAPA 4 — COMPOSICIÓN:**
"Close-up overhead documentation shot at approximately 60-80 cm from the item, camera positioned directly above. Evidence placard numbered [número de Tabla 0-A] visible in the upper right corner of the frame. ABFO #2 L-shaped metric scale ruler visible along the left and bottom edges of the frame. The item fills 55-70% of the frame, leaving margins on all sides for context. The item is centered and oriented with its [longest axis / most diagnostic face] facing the camera. All elements tack-sharp throughout the frame."

**CAPA 5 — ILUMINACIÓN:**
"[Iluminación de Tabla 0-E para este material — copiar literalmente: ej. 'Oblique side lighting from the left at 45 degrees as primary source to reveal surface texture and any markings. Ring flash at reduced power as secondary fill to eliminate deep shadows while preserving texture-revealing shadows from the oblique primary']. The controlled laboratory lighting produces [describe resultado: 'uniform illumination that reveals the full surface detail of the item without specular highlights obscuring any area']. Color temperature: neutral 5500K daylight balanced. No mixed color temperatures."

**CAPA 6 — CÁMARA/LENTE:**
"[Lente de Tabla 0-E para este material: ej. 'Shot on Canon EOS R5, 105mm macro lens']. Aperture f/11 for maximum depth of field — every point of the item from nearest to furthest must be in tack-sharp focus. ISO 200. Shutter speed 1/200th synchronized with the ring flash. Camera mounted on copy stand, perfectly level overhead. No camera movement, no grain."

**CAPA 7 — ESTILO:**
"This is a clinical forensic evidence examination photograph. The image must look like a laboratory documentation record — no color grading, no artistic composition, no studio product lighting aesthetics. Neutral and technical. The purpose is to document the physical properties of the item exhaustively for investigative record-keeping. Not a commercial product photograph."

**CAPA 8 — CALIDAD:**
"Photorealistic clinical documentation photograph. Maximum sharpness, no grain (low ISO). Neutral color balance, accurate reproduction of the item's actual color and surface properties. High resolution — all text, markings, and surface details must be legible. RAW photo quality."

---

### MODO 3 — MACRO DETALLE DIAGNÓSTICO (rasgo clave de la evidencia)

> ⚠️ Generar SOLO si la evidencia tiene un rasgo diagnóstico identificado en la Tabla 0-A. Si no lo tiene, omitir este modo.

```
EVIDENCIA: [número de Tabla 0-A] — [nombre exacto de Tabla 0-A]
MODO: 3 — Macro / Detalle diagnóstico
ÁREA DE INTERÉS: [descripción específica del área a fotografiar — ej: "base of the blade where the serial number is engraved"]
ASPECT RATIO: 1:1 (cuadrado)
PLATAFORMA: DALL-E 3 o Grok 2

PROMPT (en inglés — copiar y pegar directamente):

[Generar aquí el prompt completo siguiendo las 8 capas]
```

**Estructura obligatoria de las 8 capas para MODO 3:**

**CAPA 1 — SUJETO:**
"An extreme close-up documentary photograph of [descripción específica del área de interés — no el objeto completo: ej. 'the base section of a stainless steel kitchen knife, specifically the area where a partially visible serial number is stamped into the metal']."
→ El sujeto es el DETALLE, no el objeto completo.

**CAPA 2 — ESTADO DEL OBJETO (solo el área fotografiada):**
"[Descripción del estado del área específica: 'The metal surface in this section shows [detalle de estado: oxidation / scratches / stamped marking / biological trace]. [Descripción precisa del rasgo diagnóstico: qué se ve, qué lo hace legible o visible, qué lo rodea]. [Si hay una marca específica: describir forma, tamaño estimado, profundidad aparente, color, contraste con la superficie]'."

**CAPA 3 — CONTEXTO/ENTORNO:**
"[Misma superficie de examen del MODO 2 para coherencia]. The item is photographed on [misma superficie de Tabla 0-E]. Only the relevant section of the item is within the macro frame — [describir qué partes del objeto quedan fuera del encuadre y cuáles son visibles como contexto]. Evidence placard [número de Tabla 0-A] partially visible at the edge of the frame."

**CAPA 4 — COMPOSICIÓN:**
"Extreme macro close-up, the diagnostic area fills 70-80% of the frame. ABFO #2 metric scale ruler visible at the [left / bottom] edge to provide scale reference. The [rasgo diagnóstico] is centered and positioned at the intersection of the horizontal third and vertical third of the frame. [Si hay texto o número: 'the marking is positioned horizontally and parallel to the bottom edge of the frame for maximum legibility']. Overhead or slight oblique angle to maximize detail visibility."

**CAPA 5 — ILUMINACIÓN:**
"[Iluminación especializada para revelar el rasgo diagnóstico específico]:
- Para texto/números grabados: 'Strong raking light from the left at a 15-degree angle to the surface, creating deep shadows within the engraved channels that make the marking clearly legible against the surrounding smooth surface.'
- Para manchas biológicas: 'Ring flash providing flat even illumination to reveal color differentiation between the stain and the surrounding surface.'
- Para marcas de desgaste: 'Oblique light from left at 30 degrees to reveal surface texture differences in the worn area.'
- Para fibras/trazas: 'High-intensity ring flash with dark background to separate trace evidence by contrast.'
[Usar la opción apropiada para el rasgo diagnóstico de esta evidencia. Temperatura: 5500K neutral]."

**CAPA 6 — CÁMARA/LENTE:**
"Shot on Canon EOS R5, 105mm macro lens at 1:1 reproduction ratio. Aperture f/16 for maximum depth of field in macro range — every detail from front to back of the diagnostic area must be in sharp focus. ISO 100. Camera on copy stand or macro rail. No vibration, no motion."

**CAPA 7 — ESTILO:**
"This is an extreme macro detail documentary photograph. Clinical and technical — no artistic processing, no shallow depth-of-field bokeh effect, no dramatic lighting. The image is a magnified record of a specific diagnostic feature. Not a creative or commercial close-up photograph. Everything in frame must be in sharp focus."

**CAPA 8 — CALIDAD:**
"Extreme macro photorealism. Tack-sharp throughout the entire frame. Maximum detail — surface texture, grain of the material, and the diagnostic marking must all be clearly defined. No grain (ISO 100). Neutral color balance. High resolution documentation."

PROPÓSITO: [qué debe identificar o analizar el jugador en esta imagen]
PISTA OCULTA: [qué información forense contiene este detalle — sin spoilear directamente]

---

### MODO 4 — BOLSA DE EVIDENCIA (evidencia embolsada y etiquetada)

> ⚠️ Generar SOLO si fue marcado en el Paso 1.5 como necesario.

```
EVIDENCIA: [número de Tabla 0-A] — [nombre exacto de Tabla 0-A]
MODO: 4 — Bolsa de evidencia
ASPECT RATIO: 3:2 (landscape)
PLATAFORMA: DALL-E 3 o Grok 2

PROMPT (en inglés — copiar y pegar directamente):

[Generar aquí el prompt completo siguiendo las 8 capas]
```

**Estructura obligatoria de las 8 capas para MODO 4:**

**CAPA 1 — SUJETO:**
"A detailed documentation photograph of [descripción física del objeto] inside a sealed transparent evidence bag, with its official evidence label clearly visible."

**CAPA 2 — ESTADO DEL OBJETO:**
"[El objeto es visible a través de la bolsa transparente — describir su estado como en MODO 2 pero filtrado por el plástico]. The bag is heat-sealed at the top. [Si el objeto tiene manchas visibles a través del plástico: 'a dark [color]-colored stain on the [parte] is visible through the transparent bag surface'.]"

**CAPA 3 — CONTEXTO/ENTORNO:**
"The evidence bag is placed flat on a neutral forensic gray surface. The bag is oriented with [la cara más informativa del objeto] facing upward. The official paper label affixed to the bag reads: evidence number [número de Tabla 0-A], case identifier visible, date/time of collection line visible, collector initials line visible. The text on the label must be legible. No other objects in frame."

**CAPA 4 — COMPOSICIÓN:**
"Overhead documentation shot from 50-60 cm above the bag, camera directly overhead. The bag fills 70-80% of the frame. The label text is positioned within the upper third of the frame and must be legible. An ABFO metric scale ruler is visible along the bottom edge. The item inside the bag is clearly identifiable through the transparent surface."

**CAPA 5 — ILUMINACIÓN:**
"Diffused overhead flat lighting — no directional shadows on the bag surface to avoid glare on the transparent plastic. Soft even illumination from directly above to eliminate bag surface reflections. Color temperature 5500K neutral. The plastic bag surface must not show specular reflections that obscure the item inside. If any reflection risk: describe 'polarized lighting to eliminate plastic surface glare'."

**CAPA 6 — CÁMARA/LENTE:**
"Shot on Canon EOS R5, 50mm lens. Aperture f/8. ISO 200. Camera on copy stand overhead. All elements in focus — bag label text, item inside, and scale ruler."

**CAPA 7 — ESTILO:**
"Clinical evidence documentation photograph. Record of the packaged state of the evidence item. No artistic processing. The transparency of the bag and the legibility of the label are the two critical elements."

**CAPA 8 — CALIDAD:**
"Photorealistic documentation photograph. The label text must be legible. The item inside the bag must be clearly identifiable. Neutral color balance. RAW photo quality. No grain."

---

## PASO 3: HOJA DE EXPEDIENTE MULTI-EVIDENCIA

Si hay 4 o más evidencias, generar este prompt para una hoja de expediente policial con todas las evidencias en una sola imagen. Generar en la ENTREGA FINAL.

```
IMAGEN: Hoja de Expediente — Evidencias del Caso [nombre del caso]
ASPECT RATIO: 2:3 (A4 vertical)
PLATAFORMA: DALL-E 3 (primera opción por texto legible) o Grok 2

PROMPT:
"Scanned forensic evidence documentation sheet, official format, A4 vertical orientation,
[N×2] grid layout of evidence photographs — [N] rows of two photos each,
[si número impar de evidencias: the last item centered at the bottom, slightly larger than the others],
white or light cream official paper background,
each evidence shown as a small rectangular photograph in its laboratory examination state (isolated on gray forensic surface),
thin black border around each photograph,
flat even overhead lighting on each photo simulation, high detail throughout.

Grid layout:
[Fila 1, izquierda]: [descripción exacta de Tabla 0-A para E-01], evidence marker [número], ABFO scale visible.
[Fila 1, derecha]: [descripción exacta de Tabla 0-A para E-02], evidence marker [número], ABFO scale visible.
[Fila 2, izquierda]: [descripción exacta de Tabla 0-A para E-03], evidence marker [número], ABFO scale visible.
[Fila 2, derecha]: [descripción exacta de Tabla 0-A para E-04], evidence marker [número], ABFO scale visible.
[continuar para cada evidencia]

Printed label under each photo: 'EVIDENCE [número de Tabla 0-A] — Case: [nombre del caso]' in Arial font, clearly legible.
Header at top of document: 'FORENSIC EVIDENCE LOG — [nombre del caso]' in bold serif font.
Clean layout, no dramatic shadows, high resolution, scanned document style, exact A4 vertical proportions."

PROPÓSITO: Imagen de referencia rápida para que el jugador vea todas las evidencias del caso en una sola página.
```

---

## PASO 4: TABLA RESUMEN DE TODAS LAS IMÁGENES

Al terminar todos los prompts, entrega esta tabla:

| # | Evidencia | Modo | Descripción breve | Aspect Ratio | Plataforma | Prioridad |
|---|-----------|------|------------------|--------------|------------|-----------|
| 1 | E-01 — [nombre] | In-situ | [descripción] | 4:3 | DALL-E 3 / Grok 2 | Alta |
| 2 | E-01 — [nombre] | Laboratorio | [descripción] | 1:1 | DALL-E 3 / Grok 2 | Alta |
| 3 | E-01 — [nombre] | Macro | [rasgo diagnóstico] | 1:1 | DALL-E 3 / Grok 2 | Alta |
| 4 | E-02 — [nombre] | In-situ | [descripción] | 4:3 | DALL-E 3 / Grok 2 | Alta |
| ... | ... | ... | ... | ... | ... | ... |
| N | Hoja expediente | Multi-evidencia | Todas las evidencias | 2:3 | DALL-E 3 | Media |

**Prioridad Alta** = evidencias que el jugador necesita examinar para resolver el caso.
**Prioridad Media** = evidencias de contexto, confirmatorias o atmosféricas.

**Nota sobre plataformas sugeridas:**
- **Objetos fotorrealistas, in-situ y laboratorio:** Flux 2 (mejor fotorrealismo) o DALL-E 3
- **Macro con texto legible (series, inscripciones, etiquetas):** DALL-E 3 / GPT-4o (primera opción) o Flux 2
- **Evidencia biológica sin filtros de contenido:** Stable Diffusion local (Juggernaut XL) con terminología médica
- **Hoja de expediente (múltiples fotos + texto):** DALL-E 3 (primera opción) o Ideogram 2.0
- **Bolsas de evidencia con etiqueta legible:** DALL-E 3 (texto más preciso)

---

## PASO 5: VERIFICACIÓN DE COHERENCIA (obligatoria antes de entregar)

Antes de entregar los prompts, responde SÍ/NO a cada punto:

### Coherencia de objetos
- [ ] ¿La descripción física de cada evidencia en MODO 1, 2 y 3 es idéntica? (mismo objeto, mismo estado)
- [ ] ¿Ninguna evidencia cambia de material, color o dimensión entre modos?
- [ ] ¿El estado del objeto (pristine/worn/stained) es el mismo en todos los modos de la misma evidencia?
- [ ] ¿Los rasgos diagnósticos descritos en MODO 3 son coherentes con la descripción del MODO 2?

### Coherencia de números
- [ ] ¿Cada evidencia lleva exactamente el mismo número (de Tabla 0-A) en sus tres modos?
- [ ] ¿Ningún número se repite en dos evidencias distintas?
- [ ] ¿Todos los números usados en los prompts existen en la Tabla 0-A?
- [ ] ¿La hoja de expediente usa los mismos números que las fotos individuales?

### ⚠️ VERIFICACIÓN CRUZADA DE EVIDENCIAS (obligatoria — este paso BLOQUEA la entrega)

Antes de revisar los prompts, reconstruir la Tabla 0-A de memoria en este formato:

```
E-01 | [nombre] | [descripción física] | [material] | [rasgo diagnóstico]
E-02 | [nombre] | [descripción física] | [material] | [rasgo diagnóstico]
... (todas las evidencias)
```

Luego verificar que cada evidencia en los prompts generados coincida exactamente con su fila en la tabla reconstruida.

**Errores típicos a revisar:**
- [ ] ¿Ninguna evidencia lleva el número de otra evidencia diferente?
- [ ] ¿Las descripciones físicas del MODO 2 son literalmente idénticas a las de MODO 1 (mismos adjetivos, mismo estado)?
- [ ] ¿El rasgo diagnóstico del MODO 3 corresponde al objeto correcto?
- [ ] ¿Los materiales del suelo en MODO 1 son coherentes con la descripción del escenario del crimen?
- [ ] ¿Los modos 2 y 3 usan la superficie de laboratorio correcta según la Tabla 0-E?

### Coherencia de atmósfera
- [ ] ¿Todos los prompts MODO 1 incluyen la frase de atmósfera de Tabla 0-D?
- [ ] ¿Los prompts MODO 2 y MODO 3 NO incluyen la frase de atmósfera? (su entorno es neutro)
- [ ] ¿El film look de Tabla 0-D está solo en los prompts MODO 1 (in-situ)?
- [ ] ¿La iluminación del MODO 1 es coherente con la iluminación del escenario del crimen descrita en la Tabla 0-D?

### Coherencia de plataforma
- [ ] ¿Los prompts incluyen las frases anti-artísticas obligatorias (adaptadas al tipo de imagen)?
- [ ] ¿Los prompts de MODO 3 con texto o marcas grabadas usan DALL-E 3 como plataforma sugerida?
- [ ] ¿Ningún prompt de MODO 2 o 3 tiene referencias a la atmósfera del caso (están en un laboratorio neutro)?

### ⚠️ VERIFICACIÓN DE LONGITUD POR MODO (obligatoria — este paso BLOQUEA la entrega)

Contar las palabras de cada prompt antes de entregar. Si algún prompt no alcanza el mínimo, extender añadiendo detalles nuevos (no repetir).

| Modo | Mínimo | ¿Lo cumple? | Si NO: qué capa extender |
|------|--------|-------------|--------------------------|
| MODO 1 (in-situ) | 200 palabras | [SÍ/NO] | Capa 3 (entorno) o Capa 5 (iluminación) |
| MODO 2 (laboratorio) | 210 palabras | [SÍ/NO] | Capa 2 (estado del objeto) o Capa 5 (iluminación de laboratorio) |
| MODO 3 (macro) | 220 palabras | [SÍ/NO] | Capa 2 (descripción del rasgo diagnóstico) o Capa 5 (iluminación especializada) |

⚠️ REGLA: Si MODO 3 es más corto que MODO 2, o si MODO 2 es más corto que MODO 1, corregir ANTES de entregar. La longitud es proporcional a la importancia diagnóstica de la imagen, no a la complejidad del entorno.

Si alguna respuesta es NO, corregir el prompt afectado ANTES de entregarlo.

---

## VOCABULARIO SEGURO PARA DALL-E 3 — APLICAR SIEMPRE

DALL-E 3 bloquea prompts que combinan ciertas palabras aunque el contexto sea narrativo o ficticio. Esta tabla de sustituciones es obligatoria. Aplícala a TODO el vocabulario antes de entregar cualquier prompt.

⚠️ No es opcional. Un prompt bloqueado es un prompt inútil. Usar el vocabulario seguro desde la primera generación.

| ❌ Vocabulario bloqueado | ✅ Vocabulario seguro equivalente |
|--------------------------|-----------------------------------|
| `forensic evidence photograph` | `detailed documentary photograph` |
| `crime scene evidence` | `documentary evidence item` |
| `evidence collected at crime scene` | `item found at the location` |
| `forensic documentation photography` | `detailed documentary photography` |
| `police forensic team` | `documentary film crew` |
| `forensic photographer` | `documentary photographer` |
| `evidence placard` / `evidence marker` | `numbered reference marker` |
| `ABFO scale ruler` | `metric reference ruler` |
| `chain of custody` | `reference documentation` |
| `blood pool` / `blood stain` / `blood` | `dark reddish-brown passive stain` / `dark circular mark on the surface` |
| `hemoglobin` | `dark reddish-brown fluid mark` |
| `fresh blood, bright red` | `dark red wet-looking stain, spreading pattern` |
| `dried blood, dark brown` | `near-black matte dried stain fully absorbed into the [material]` |
| `victim's [object]` | `[descripción del objeto sin vincular a víctima]` |
| `murder weapon` | `[nombre descriptivo del objeto: the kitchen knife / the blunt instrument]` |
| `unprocessed police evidence photograph` | `unprocessed documentary film still` |
| `forensic laboratory` | `documentation studio` / `controlled examination environment` |
| `biological trace evidence` | `trace material sample` |

**Framing de apertura recomendado para prompts de evidencia:**

Para MODO 1 (in-situ):
> `"A detailed documentary production still from a mystery thriller, showing [descripción del objeto] found on the [material del suelo] at the location..."`

Para MODO 2 (laboratorio):
> `"A detailed documentary close-up photograph of [descripción del objeto], isolated on a neutral gray surface for examination documentation..."`

Para MODO 3 (macro):
> `"An extreme close-up documentary photograph of the [área específica] of [descripción del objeto], showing [el rasgo diagnóstico] in high detail..."`

---

## PASO 3 (FORMATO FINAL) — DALL-E 3, MÁXIMA EXTENSIÓN

Cada prompt se genera en una única versión optimizada para DALL-E 3.

**Objetivo de longitud mínima:** 200 palabras por prompt. Si el espacio del mensaje lo permite, extender hasta 280 palabras sin repetir información — cada palabra adicional debe aportar un detalle nuevo y específico.

**Formas de extender sin repetir:**
- Describir la textura exacta de cada superficie (la fibra del tejido, el grano del metal, las irregularidades del papel)
- Detallar cómo la luz interactúa con el material específico de la evidencia
- Especificar el estado exacto de cada característica del objeto (no solo "worn" — sino "worn at the contact points, with bright metal visible through the coating at the highest-use areas")
- Describir la relación espacial entre el objeto y los elementos del encuadre (regla, marcador, superficie)
- Para objetos con texto o inscripciones: describir la tipografía, tamaño relativo y legibilidad deseada

**Estructura de párrafos por modo — objetivos de longitud:**

**MODO 1 — In-situ (mínimo 200 palabras):**
1. Párrafo 1 (30-40 palabras): Tipo de imagen, descripción física completa del objeto, número de evidencia.
2. Párrafo 2 (40-50 palabras): Estado del objeto, marcas, stains, estado de conservación.
3. Párrafo 3 (40-60 palabras): Superficie y entorno inmediato — material, textura, distancia a elementos de referencia.
4. Párrafo 4 (30-40 palabras): Composición — ángulo de cámara, marcador, regla métrica, porcentaje del frame.
5. Párrafo 5 (40-50 palabras): Iluminación — fuente de escena, ángulo, cómo cae sobre el material del objeto.
6. Párrafo 6 (25-35 palabras): Especificaciones técnicas de cámara.
7. Párrafo 7 (25-35 palabras): Frases anti-artísticas obligatorias.
8. Párrafo 8 (20-25 palabras): Calidad + film look + frase de atmósfera.

**MODO 2 — Laboratorio (mínimo 210 palabras — igual o más que MODO 1):**
1. Párrafo 1 (30-40 palabras): Tipo de imagen, descripción física completa del objeto, número de evidencia.
2. Párrafo 2 (50-65 palabras): Estado del objeto — MISMO estado que MODO 1, pero con mayor detalle: describir cada marca, deformación, textura de superficie, contraste de materiales visible en condiciones de laboratorio.
3. Párrafo 3 (35-45 palabras): Superficie de examen — material exacto, textura, color, condición; aislamiento total del objeto.
4. Párrafo 4 (35-45 palabras): Composición — ángulo overhead, posición del objeto en el frame, marcador, regla ABFO, cara del objeto orientada a cámara.
5. Párrafo 5 (45-60 palabras): Iluminación de laboratorio — tipo exacto según Tabla 0-E, comportamiento sobre el material, resultado visual esperado (qué revela, qué suprime), temperatura de color.
6. Párrafo 6 (25-35 palabras): Especificaciones técnicas de cámara y copy stand.
7. Párrafo 7 (25-35 palabras): Frases anti-artísticas obligatorias.
8. Párrafo 8 (20-25 palabras): Calidad técnica — sin grano, nitidez máxima, balance de color neutro.

**MODO 3 — Macro detalle diagnóstico (mínimo 220 palabras — el más largo del conjunto):**
1. Párrafo 1 (30-40 palabras): Tipo de imagen, descripción ESPECÍFICA del área de interés (no el objeto completo), número de evidencia.
2. Párrafo 2 (55-70 palabras): Estado del área fotografiada — describir en máximo detalle el rasgo diagnóstico: forma exacta, dimensiones estimadas, profundidad aparente, color, contraste con la superficie circundante, detalles microscópicos visibles, cualquier característica que lo haga único o identificable.
3. Párrafo 3 (35-45 palabras): Qué partes del objeto son visibles como contexto fuera del área central, misma superficie de Tabla 0-E que MODO 2.
4. Párrafo 4 (35-45 palabras): Composición macro — porcentaje del frame que ocupa el rasgo diagnóstico, posición en el frame (thirds), orientación para máxima legibilidad, regla métrica en el borde.
5. Párrafo 5 (45-60 palabras): Iluminación especializada para el rasgo diagnóstico — ángulo exacto, efecto sobre la superficie (sombras dentro de grabados, contraste de stain, definición de fibras), temperatura de color, resultado visual esperado.
6. Párrafo 6 (25-35 palabras): Especificaciones técnicas de cámara macro (1:1, f/16, ISO 100, copy stand o macro rail).
7. Párrafo 7 (25-35 palabras): Frases anti-artísticas obligatorias + recordatorio de foco total (no bokeh).
8. Párrafo 8 (20-25 palabras): Calidad extrema — máxima nitidez, sin grano, cada micro-detalle definido.

**Frases anti-artísticas obligatorias (incluir completas en el Párrafo 7):**
- "This is a documentary examination photograph, not a commercial product photo."
- "The image must look like an unprocessed documentary film still."
- "Technical documentation style — accurate record, not artistic composition."
- "No color grading. No contrast enhancement. No vignetting."
- "Straight from camera, unretouched, functional documentation."

---

## REGLAS CRÍTICAS DE ESTE GENERADOR

1. ✅ Cada prompt tiene entre 180 y 260 palabras en inglés. Un prompt corto es un prompt vago.
2. ✅ La estructura de 8 capas es obligatoria y va en el orden exacto indicado.
3. ✅ La descripción física de cada evidencia (Tabla 0-A) se copia LITERALMENTE — no se parafrasea.
4. ✅ Los números de evidencia de Tabla 0-A son inmutables en todos los modos.
5. ✅ La iluminación de MODO 2 y 3 se extrae SIEMPRE de la Tabla 0-E según el material del objeto.
6. ✅ Las frases anti-artísticas son obligatorias en todos los prompts.
7. ✅ La frase de atmósfera de Tabla 0-D se usa SOLO en los prompts de MODO 1 (in-situ).
8. ✅ MODO 2 y MODO 3 son siempre en entorno de laboratorio neutro — sin elementos del escenario.
9. ✅ El rasgo diagnóstico del MODO 3 debe estar en la Tabla 0-A antes de generar el prompt.
10. ✅ MODO 4 (bolsa) solo se genera cuando hay información en la etiqueta relevante para el caso.
11. ❌ PROHIBIDO cambiar la descripción del objeto entre modos — el mismo objeto tiene el mismo estado en todas sus imágenes.
12. ❌ PROHIBIDO usar luz dramática, cinematográfica o artística en ningún modo.
13. ❌ PROHIBIDO inventar materiales, marcas o detalles del objeto que no estén en el caso.
14. ❌ PROHIBIDO aplicar la frase de atmósfera del caso a los prompts de laboratorio.
15. ❌ PROHIBIDO fusionar dos evidencias distintas en un solo prompt.
16. ❌ PROHIBIDO prompt de menos de 200 palabras — agregar capas hasta llegar al mínimo.
17. ❌ PROHIBIDO que MODO 3 sea más corto que MODO 2, ni que MODO 2 sea más corto que MODO 1. La longitud del prompt es proporcional a la importancia diagnóstica de la imagen.
18. ❌ PROHIBIDO usar `"forensic macro documentation photograph"` o `"forensic evidence analysis"` en MODO 3 — usar `"extreme macro detail documentary photograph"` y `"detailed documentary photograph"`.
19. ❌ PROHIBIDO aplicar la iluminación de tela (cross-lighting) a papel/documentos — cada material tiene su iluminación en Tabla 0-E y no son intercambiables.

---

## ENTRADAS REQUERIDAS

Pega aquí la información necesaria para comenzar:

### NARRATIVA DEL CASO (resumen del contexto y el crimen):
[PEGA AQUÍ]

### LISTA DE EVIDENCIAS FÍSICAS (del caso aprobado — nombre, descripción, dónde se encontró):
[PEGA AQUÍ]

### PALETA VISUAL DEL CASO (Tabla 0-D de la Etapa 4A, si ya existe — o descripción del escenario del crimen):
[PEGA AQUÍ]

### TIEMPO TRANSCURRIDO DESDE EL CRIMEN AL FOTOGRAFIAR LAS EVIDENCIAS IN-SITU:
[PEGA AQUÍ — ej: "2 horas después del crimen"]

```
