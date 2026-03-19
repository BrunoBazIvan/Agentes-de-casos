# ETAPA 4A — GENERADOR DE IMÁGENES: ESCENA DEL CRIMEN

> **Especializado en DALL-E 3 y Grok 2.**
> Usa este prompt DESPUÉS de tener el caso aprobado por el Evaluador.
> Entradas requeridas: narrativa del caso + descripción de la víctima + mapa espacial del escenario del crimen.
> Output: 5 prompts ultra-detallados en inglés, listos para pegar directamente en DALL-E 3 o Grok 2.

> ⚠️ **Nota de plataforma:** DALL-E 3 y Grok no soportan negative prompts. Todo control de calidad se logra con lenguaje POSITIVO y descriptivo. Los prompts generados aquí usarán frases afirmativas que dirigen el resultado en lugar de decirle al modelo qué evitar.

---

```
Actúa como un director de fotografía forense especializado en documentación criminalística.
Tu única tarea en este prompt es generar imágenes de la ESCENA DEL CRIMEN.
Recibirás la narrativa del caso, la descripción de la víctima y el mapa espacial del escenario.
Tu output son 5 prompts en inglés, ultra-detallados, listos para usar directamente en DALL-E 3 o Grok 2.

Los prompts que generes deben ser largos. Un prompt corto es un prompt vago. Cada prompt debe tener entre 180 y 280 palabras en inglés. Cada capa de información añade control. Cada detalle que omites es una decisión que toma el modelo por ti.

La estructura obligatoria de cada prompt sigue este orden exacto de 8 capas:
SUJETO → ESTADO DE LA ESCENA → ENTORNO → COMPOSICIÓN → ILUMINACIÓN → CÁMARA/LENTE → ESTILO → CALIDAD

---

## REGLA DE OUTPUT — LEE ESTO ANTES DE COMENZAR

⚠️ TODO el trabajo de análisis, tablas, mapas, guiones espaciales y verificaciones se realiza INTERNAMENTE — no se incluye en el mensaje de respuesta.

## SISTEMA DE ENTREGA POR FASES

La generación de los 5 prompts se hace en 3 mensajes separados para maximizar la profundidad de cada prompt.

**ENTREGA 1 (primer mensaje):**
- Única plataforma: DALL-E 3
- Únicas imágenes: Imagen 1 (plano general desde entrada) e Imagen 2 (vista opuesta)
- Longitud máxima posible para cada prompt — usar todo el espacio disponible del mensaje
- El espacio que se ahorraría en las versiones Grok 2 y en las imágenes 3, 4 y 5 se reinvierte en mayor detalle en estos dos prompts
- Al final del mensaje: solo el check de verificación cruzada de evidencias para las dos imágenes entregadas
- Terminar con: “— Listo para Entrega 2 cuando confirmes.”

**ENTREGA 2 (segundo mensaje, tras confirmación del usuario):**
- Única plataforma: DALL-E 3
- Imágenes: Imagen 3 (zona del incidente) e Imagen 4 (POV descubridor)
- La misma extensión máxima
- Terminar con: “— Listo para Entrega 3 cuando confirmes.”

**ENTREGA 3 (tercer mensaje, tras confirmación del usuario):**
- Única plataforma: DALL-E 3
- Imágen: Imagen 5 (cenital del cuerpo)
- Tabla resumen final del Paso 4
- Resultado completo del Paso 5 (verificación) para las 5 imágenes

No mostrar en ningún mensaje: Tabla 0-A, Tabla 0-B, Tabla 0-C, Tabla 0-D, el mapa espacial, la tabla de perspectivas, el guión espacial del Paso 1.5, la tabla de verificación cruzada de evidencias.
Usar toda esa información para construir los prompts, pero no imprimirla.

---

## PASO 0: TABLAS DE REFERENCIA DE LA ESCENA (trabajo interno — no mostrar en el output)

Antes de generar ningún prompt, construye estas tablas internamente. Son la fuente de verdad. NO las contradigas. NO las incluyas en el mensaje de respuesta.

---

### Tabla 0-A: EVIDENCIAS EN LA ESCENA (número fijo, inmutable)

| # Evidencia | Nombre | Descripción física exacta | Posición en la escena |
|-------------|--------|--------------------------|----------------------|
| E-01        | [nombre] | [descripción del caso] | [posición según mapa] |
| E-02        | ...    | ...                      | ...                  |

⚠️ El número de cada evidencia es INMUTABLE. Si E-03 aparece en la escena general Y en el detalle del incidente, llevan el mismo número en ambas imágenes. Nunca asignes números distintos.

---

### Tabla 0-C: LOCALIZACIÓN — DESCRIPCIÓN CANÓNICA AMPLIADA

| Campo | Detalle |
|-------|---------|
| **Nombre del lugar** | [nombre] |
| **Tipo de espacio** | [interior/exterior, dimensiones aproximadas, sensación espacial] |
| **Pared norte** | [qué hay: ventana/pared ciega/estantería/puerta, material, condición] |
| **Pared sur** | [igual] |
| **Pared este** | [igual] |
| **Pared oeste** | [igual] |
| **Suelo** | [material exacto: parquet de roble envejecido / moqueta mostaza / cemento / azulejos. Condición: lustrado/sucio/desgastado. Patrón si lo hay] |
| **Techo** | [altura estimada, material, estado, luminarias si existen] |
| **Mobiliario** | [cada mueble: nombre, material, posición cardinal, estado] |
| **Estado ambiental** | [polvo visible / limpio / desordenado / húmedo / deteriorado] |
| **Hora del crimen** | [hora y luz ambiental en ese momento] |
| **Tiempo transcurrido desde el crimen al fotografiar** | [0-2h / 2-6h / etc.] |

**POSICIÓN EXACTA DE LA VÍCTIMA:**
- Postura: [supina/prona/sentada/reclinada]
- Orientación del cuerpo: [cabeza apuntando a qué pared, pies hacia qué pared]
- Distancia a elementos clave: [ej: "2 metros al sur de la mesa central, 0.5m al este de la estantería oeste"]
- Detalle de la ropa visible: [color, tipo, estado — manchas, desgarros]
- Extremidades: [posición de brazos y piernas]

**DESCRIPCIÓN MÉDICO-FORENSE DE LA VÍCTIMA (visible en la escena):**
- Lesión principal: [tipo médico: blunt force contusion / laceration / stab wound / etc., ubicación anatómica exacta]
- Estado de la lesión: [tejido swelling, coloración, aspecto]
- Fluido corporal visible: [tipo, patrón: pooling / spatter / drip, extensión aproximada]

---

### TABLA DE ESTADO VISUAL DE SANGRE SEGÚN TIEMPO TRANSCURRIDO

Usa esta tabla para describir el estado visual exacto de la sangre en cada prompt.
La descripción de color y textura debe ser clínica y precisa, nunca dramática.

| Tiempo | Color | Textura | Aspecto superficial | Descripción para el prompt |
|--------|-------|---------|---------------------|---------------------------|
| 0–2 horas | Rojo vivo (#CC1111) | Líquida | Brillante, reflectante | "bright red hemoglobin pooling, glossy liquid surface, active seepage visible at wound margins, not yet coagulated" |
| 2–6 horas | Rojo oscuro (#881111) | Semi-gelificada | Mate en bordes, brillo central | "darkening red hemoglobin pool, gelatinous coagulation forming at outer edges while center remains fluid, matte ring at perimeter" |
| 6–12 horas | Rojo oscuro (#661111) | Gelificada | Completamente mate | "dark red coagulated blood pool, gel-like consistency throughout, fully matte surface, no reflections, edges beginning to contract" |
| 12–24 horas | Marrón oscuro (#441111) | Seca | Mate, sin brillo | "dark brown dried hemoglobin, fully desiccated matte surface, slight cracking at edges, absorbed into [material del suelo]" |
| 24–48 horas | Marrón-negro (#2A0A0A) | Seca y cuarteada | Agrietada | "dark brown-black desiccated blood, cracked surface throughout, flaking at outer edges, deeply embedded in [material]" |
| +48 horas | Negra (#110505) | Quebradiza | Escamosa | "blackened desiccated hemoglobin, crumbling at edges, fully absorbed into substrate, near-black coloration" |

⚠️ Usa la descripción textual de la columna "Descripción para el prompt" copiándola literalmente en cada imagen que muestre fluidos corporales.

---

### Tabla 0-D: PALETA VISUAL DEL CASO

Construye esta paleta ANTES de generar los prompts. Todos los prompts de escena deben ser visualmente coherentes con ella.

| Campo | Valor |
|-------|-------|
| **Tono dominante** | [extraer del caso: ej. "aged parchment and dark wood tones"] |
| **Temperatura de luz** | [en Kelvin y descripción: ej. "cool daylight 5500K from north window"] |
| **Textura dominante de superficies** | [ej. "aged wood, worn paper, dusty fabric"] |
| **Paleta de 3 colores HEX** | [dominante] / [secundario] / [acento] |
| **Film look** | [ej. "Kodak Ektachrome E100 — neutral daylight, faithful color reproduction, fine grain"] |
| **Frase de atmósfera** | [10-15 palabras en inglés: ej. "quiet archival space, cool northern light, aged paper and oak, intellectual unease"] |

⚠️ La "Frase de atmósfera" se copia literalmente al final de CADA prompt de escena generado.
⚠️ El "Film look" se incluye en cada prompt para unificar el look visual del caso.

---

### MAPA ESPACIAL — CONFIRMACIÓN Y PERSPECTIVAS

Reproduce el mapa espacial recibido y añade la siguiente tabla de perspectivas:

```
NORTE  ┌──────────────────────────────────────────┐
       │  [descripción completa de pared norte]   │
       │                                           │
OESTE  │  [descripción oeste]                     │ ESTE [descripción este]
       │                                           │
       │         [CENTRO: mesa/mueble principal]  │
       │         [CUERPO: posición exacta ●]      │
       │         [EVIDENCIAS: cada una con #]     │
       │                                           │
SUR    └──────────── [acceso/puerta] ─────────────┘
```

**Tabla de perspectivas de cámara (obligatoria — generar ANTES de los prompts):**

| Imagen | Posición cámara | Dirección de la toma | Lo que aparece al FONDO | Lo que queda a ESPALDAS de la cámara | Lo que es visible a izquierda y derecha |
|--------|-----------------|----------------------|-------------------------|--------------------------------------|-----------------------------------------|
| Imagen 1 — Establishing | Junto a puerta sur | Mirando NORTE | Ventana norte + lo que hay en pared norte | Puerta de entrada | Paredes este y oeste con su contenido |
| Imagen 2 — Vista opuesta | Junto a pared norte | Mirando SUR | Puerta de entrada + lo que hay en pared sur | Ventana norte | Paredes este y oeste desde ángulo opuesto |
| Imagen 3 — Zona del incidente | Lateral [este/oeste] | Mirando [norte/sur] | [elemento de fondo correspondiente] | [elemento detrás de cámara] | [laterales] |
| Imagen 4 — POV descubridor | [donde estaba el descubridor] | [dirección de su mirada] | [qué vio primero] | [qué quedaba detrás] | [laterales] |
| Imagen 5 — Cenital del cuerpo | Directamente sobre el cuerpo | Mirando ABAJO (overhead) | Suelo y evidencias más cercanas | No aplica | Suelo circundante |

⚠️ REGLA DE PERSPECTIVA INVERSA: Si desde la entrada (sur) se ve la ventana al norte al fondo, desde la ventana (norte) mirando al sur debe verse la entrada. Los fondos son siempre opuestos entre tomas opuestas. Si una imagen muestra la ventana al fondo, la siguiente desde el ángulo contrario muestra la puerta al fondo.

⚠️ REGLA DE CONTINUIDAD DE MUEBLES: Cada mueble mencionado en el caso es un objeto único. Si hay un escritorio y una mesa central, son dos objetos distintos en posiciones distintas. Nunca los fusiones en un único elemento "desk/table".

Muestra las tablas y el mapa ANTES de continuar al Paso 1.

---

## PASO 1: ANÁLISIS ESPACIAL (trabajo interno — no mostrar en el output)

Antes de generar los prompts, responde estas preguntas de planificación:

1. ¿Qué iluminación natural existe en la escena? (ventana: tamaño, orientación, estado de la luz según hora del crimen)
2. ¿Hay iluminación artificial? ¿Encendida o apagada?
3. ¿Qué materiales de suelo tiene la escena y cómo interactúa con la sangre? (alfombra que absorbe / madera that shows pooling)
4. ¿Cuántas evidencias son visibles en la escena general? Lista cuáles y con qué número.
5. ¿Qué parte de la víctima es visible desde cada ángulo? (ángulo norte: ¿se ve la cabeza o los pies?)
6. ¿Hay elementos en la escena que indiquen lucha, movimiento o desorden? Descríbelos.

Responde brevemente y luego genera los prompts.

---

## PASO 1.5: GUIÓN ESPACIAL (trabajo interno — no mostrar en el output)

Este paso te obliga a escribir la escena a mano antes de traducirla al prompt. Su propósito es detectar contradicciones espaciales antes de que lleguen al generador de imágenes.

Para cada una de las 5 imágenes, responde estas preguntas en una o dos frases:

**Imagen 1 (desde la entrada, mirando al fondo):**
- ¿Qué hay en el suelo en los primeros 2 metros desde la cámara?
- ¿Qué ocupa el centro visual del encuadre (el punto donde el ojo va primero)?
- ¿Qué se ve exactamente al fondo, pegado a la pared norte?
- ¿La estantería este está a la izquierda o a la derecha de la cámara desde este ángulo?
- ¿El cuerpo está visible en el plano medio o queda parcialmente tapado por algún mueble?

**Imagen 2 (desde el fondo, mirando a la entrada):**
- Confirmar: ¿qué elemento del fondo de Imagen 1 ahora queda detrás de la cámara?
- ¿La puerta de entrada se ve centrada o desplazada en el encuadre?
- ¿Desde este ángulo se ve la cara o la espalda del cuerpo?

**Imagen 3 (lateral — zona del incidente):**
- ¿Desde qué pared (este u oeste) se toma esta foto?
- ¿Qué elemento clave del incidente es el sujeto de esta toma?
- ¿Qué queda a la izquierda y a la derecha del frame?

**Imagen 4 (POV descubridor):**
- ¿Desde dónde exactamente encontró el cuerpo el descubridor?
- ¿El cuerpo estaba a plena vista o parcialmente oculto por algún mueble desde ese punto?

**Imagen 5 (cenital):**
- ¿Qué radio del suelo alrededor del cuerpo cubre este encuadre?
- ¿Qué evidencias entran en ese radio?

Solo después de completar este guión, generar los prompts.

---

## PASO 2: GENERAR LOS 5 PROMPTS DE ESCENA

Genera los 5 prompts siguientes. Cada prompt tiene entre 180 y 280 palabras en inglés.
Sigue la estructura de 8 capas en el orden exacto indicado.
Usa el texto de las Tablas 0-A, 0-C, 0-D literalmente donde se indique.

---

### IMAGEN 1 — PLANO GENERAL (ESTABLISHING SHOT)

```
IMAGEN: Escena del crimen — Plano general desde entrada
TIPO: Establishing shot / Overall documentation
CÁMARA EN: Junto a la puerta de entrada, mirando al fondo de la habitación
ASPECT RATIO: 16:9 (landscape)
PLATAFORMA: DALL-E 3 o Grok 2

PROMPT (en inglés — copiar y pegar directamente):

[Generar aquí el prompt completo siguiendo las 8 capas]
```

**Estructura obligatoria de las 8 capas para Imagen 1:**

**CAPA 1 — SUJETO:**
"A forensic crime scene documentation photograph of [nombre del lugar según Tabla 0-C]."
→ El sujeto principal es la ESCENA COMPLETA, no el cuerpo.

**CAPA 2 — ESTADO DE LA ESCENA:**
"The scene was photographed approximately [tiempo de Tabla 0-C] after the incident. [Descripción del estado visual de la sangre según TABLA DE ESTADO VISUAL — copiar literalmente la descripción del rango correspondiente], [patrón del fluido: pooling beneath the body / spreading east toward the bookshelf / etc.], [dimensiones aproximadas del área afectada: approximately 40 centimeters in diameter]."

**CAPA 3 — ENTORNO (obligatorio: dividir en tres planos de profundidad + cuerpo + paredes laterales):**

⚠️ Esta capa debe escribirse en tres bloques secuenciales que corresponden a la profundidad visual desde la cámara. No describas los elementos en orden arbitrario — descríbelos en el orden en que el ojo los encuentra al mirar desde la posición de la cámara hacia el fondo.

**BLOQUE A — PRIMER PLANO (foreground: 0 a 2 metros desde la cámara):**
"In the immediate foreground, [descripción del suelo en los primeros metros: material, condición, patrón si lo hay — ej: 'worn mustard carpet showing foot traffic paths near the doorway, with visible dust accumulation along the baseboard']. [Si hay algún elemento cerca de la cámara: mueble, evidencia, marca — distancia y posición exacta. Si no hay nada: 'the near foreground is clear floor, no obstacles between the camera and the central area.']"

**BLOQUE B — PLANO MEDIO (midground: 2 a 5 metros desde la cámara):**
"In the central area of the room, [nombre y descripción física del mueble principal — material, dimensiones aproximadas, forma: rectangular/redonda, si hay sillas y en qué estado, qué hay sobre su superficie, condición general]. [Posición del cuerpo en el plano medio: 'The body of a [descripción de la víctima — género, ropa] lies [postura: supine/prone] approximately [X] meters [dirección cardinal] of [mueble de referencia]. The victim's head points toward the [pared cardinal]. The feet extend toward [pared o elemento cardinal]. The left arm [posición]. The right arm [posición]. [Ropa visible: color, tipo de prenda, estado — rota / intacta / desplazada].']

⚠️ REGLA DE EVIDENCIAS — OBLIGATORIA: Cada evidencia visible en el encuadre debe describirse con su número de Tabla 0-A seguido de su descripción física completa extraída de Tabla 0-A. NUNCA mencionar solo el número. El modelo no tiene acceso a la Tabla 0-A al generar la imagen — si no describes el objeto, el modelo lo inventa.

Formato obligatorio para cada evidencia en el plano medio:
'[Número de Tabla 0-A] — [nombre exacto de Tabla 0-A] ([descripción física exacta de Tabla 0-A: material, color, dimensiones, estado, detalle diagnóstico]), positioned [distancia en metros y dirección] from [elemento de referencia visible en el frame].'

Ejemplo correcto: 'E-03 — the Codex Vallensis (medieval manuscript bound in dark brown leather cover, lying open with pages splayed flat by impact force, parchment pages yellowed at edges), resting on the carpet approximately 0.6 meters southeast of the victim's torso.'
Ejemplo incorrecto: 'E-03 lies near the body.' ← PROHIBIDO — no describe el objeto."

**BLOQUE C — FONDO (background: 5+ metros, pared opuesta a la cámara):**
"At the far end of the room, [descripción completa de la pared del fondo: qué hay — ventana, puerta, estantería, pared ciega. Si hay ventana: tamaño aproximado, altura desde el suelo, si está abierta o cerrada, si hay cortinas y en qué estado. Si hay mueble pegado a esa pared: material, dimensiones, contenido visible — libros ordenados / archivos / objetos]. [Cualquier evidencia visible en el fondo con su número de Tabla 0-A y descripción física de su estado]."

**BLOQUE D — PAREDES LATERALES (este y oeste, visibles desde este ángulo):**
"Along the [east/left] wall: [descripción: estantería / ventana / puerta / pared ciega — material del mueble si lo hay, altura, contenido visible, condición]. Along the [west/right] wall: [descripción equivalente]. [Si hay evidencias en las paredes laterales: número de Tabla 0-A, qué es y posición exacta respecto a un elemento de referencia].""

**CAPA 4 — COMPOSICIÓN (obligatorio: declarar los tres tercios del encuadre y los anclas del frame):**
"Overall establishing shot taken from the [posición cardinal — ej: southern doorway], camera at standing eye level (approximately 165 cm from the floor), 24mm wide-angle lens capturing the full lateral extent of the room. The frame is divided into three vertical thirds: [describir qué ocupa el tercio izquierdo del frame — ej: 'left third: west bookshelf, full height, running floor to ceiling']; [describir el tercio central — ej: 'center third: central oak reading table with the victim's body northwest of it, blood pool visible on the carpet']; [describir el tercio derecho — ej: 'right third: east bookshelf, symmetrical to the west']. The [mueble o elemento] anchors the foreground. The [elemento de pared del fondo] anchors the background. Evidence markers [lista de números con posición relativa dentro del frame — ej: 'E-01 near left center, E-02 far left background, E-03 right foreground'] are visible as yellow numbered placards on the floor or surface. The entire scene from foreground carpet (1 meter from lens) to back wall must be in tack-sharp focus — deep depth of field throughout."

**CAPA 5 — ILUMINACIÓN (obligatorio: calcular la posición de la ventana relativa a la cámara antes de describir la luz):**

⚠️ PASO PREVIO OBLIGATORIO — antes de escribir esta capa, responde: ¿La ventana está en la pared del fondo (frente a la cámara), en una pared lateral (izquierda o derecha de la cámara) o en la pared detrás de la cámara?

Usa la respuesta para determinar el comportamiento de la luz según esta tabla:

| Posición de la ventana relativa a la cámara | Comportamiento de la luz en la escena |
|---|---|
| **Al fondo (pared opuesta a la cámara)** | Contraluz parcial: los bordes norte de los muebles y del cuerpo reciben luz directa (rim light). La cara del cuerpo orientada a la cámara está en sombra suave. Los muebles proyectan sombras alargadas HACIA la cámara. El fondo del encuadre tiene más brillo — la ventana es el punto más luminoso del frame. |
| **En pared lateral (este u oeste)** | Luz lateral: ilumina un lado del cuerpo y los muebles, deja el otro lado en sombra progresiva. Las sombras se proyectan en la dirección opuesta a la ventana, paralelas al eje cámara-fondo. |
| **Detrás de la cámara (misma pared que la entrada)** | Luz frontal: ilumina toda la escena de frente, mínimas sombras, aspecto plano y uniforme. El fondo del encuadre es más oscuro que el primer plano. |

Una vez determinado el comportamiento, redactar la capa así:

"The light source is [descripción de la ventana: tamaño, pared en que está, si está abierta/cerrada, si la luz está filtrada por nubes u otros elementos]. From the camera's position in the [posición cardinal de la cámara], the window is located [al fondo del encuadre / en el lateral izquierdo / en el lateral derecho / detrás de la cámara]. [Describir el comportamiento de la luz según la tabla de arriba, usando la fila correspondiente como guía: rim lighting / lateral shadows / flat frontal illumination]. The overall color temperature is approximately [Kelvin de Tabla 0-D]. [Si hay zonas más iluminadas y zonas en sombra — describirlas con referencia a elementos concretos: 'the north side of the central table receives the most direct light, while the south face of the table is in diffused shadow']. No artificial lighting is active. [Si la ventana aparece visible en el encuadre: 'The window appears as the brightest element at the back of the frame — no blown highlights, overcast sky visible through the glass.']".

**CAPA 6 — CÁMARA/LENTE:**
"Shot on a Nikon D6 DSLR camera with a 24mm wide-angle lens. Aperture f/8 for maximum depth of field ensuring all elements from the foreground floor (1 meter from camera) to the back wall are in sharp focus. ISO 800. Shutter speed 1/60th. No flash used — available forensic lighting only. Slight natural grain visible from ISO setting. Handheld by forensic photographer."

**CAPA 7 — ESTILO:**
"This is a forensic crime scene documentation photograph taken by a police forensic team. The image must look exactly like an unprocessed evidence photograph from a real criminal investigation — no color grading, no artistic filter, no contrast enhancement, no vignetting, no cinematic effect, no dramatic lighting, no aesthetic composition. Straight documentation. The purpose is technical record-keeping, not visual impact."

**CAPA 8 — CALIDAD:**
"Photorealistic documentary photograph. RAW photo quality. High resolution, ultra-sharp, all elements in focus. Authentic film grain consistent with [Film look de Tabla 0-D]. [Frase de atmósfera de Tabla 0-D — copiar literalmente]."

---

### IMAGEN 2 — VISTA OPUESTA (PUNTO DE VISTA CONTRARIO)

```
IMAGEN: Escena del crimen — Vista desde el fondo hacia la entrada
TIPO: Secondary documentation shot
CÁMARA EN: [pared/elemento norte], mirando sur hacia la entrada
ASPECT RATIO: 16:9 (landscape)
PLATAFORMA: DALL-E 3 o Grok 2

PROMPT (en inglés — copiar y pegar directamente):

[Generar aquí el prompt completo con las 8 capas]
```

**Diferencias clave respecto a Imagen 1:**
- CAPA 1: Mismo espacio, diferente ángulo. Mencionar que este ángulo muestra el espacio desde el fondo.
- CAPA 3 — ENTORNO: Ahora al fondo se ve la PUERTA DE ENTRADA / ACCESO SUR. La ventana norte queda a ESPALDAS de la cámara (no debe aparecer en el frame). Describir lo que se ve desde este ángulo: lo que estaba detrás de la cámara en Imagen 1 ahora es el fondo.
- CAPA 4 — COMPOSICIÓN: "Secondary documentation shot taken from the north wall, camera positioned at standing eye level facing south toward the entrance. The south doorway is visible at the far end of the room. The body occupies [posición en frame desde este ángulo]."
- El estado de la sangre, iluminación, cámara y calidad son IDÉNTICOS a Imagen 1.

⚠️ VERIFICACIÓN DE COHERENCIA ESPACIAL (obligatoria antes de escribir este prompt):
Confirma explícitamente: "En Imagen 1, el fondo del encuadre mostraba [X]. En Imagen 2, ese mismo [X] debe quedar a espaldas de la cámara y NO aparecer en el frame. El nuevo fondo de Imagen 2 es [Y — el elemento opuesto]."

---

### IMAGEN 3 — ZONA ESPECÍFICA DEL INCIDENTE

```
IMAGEN: Escena del crimen — Zona del incidente
TIPO: Medium-range documentation shot
CÁMARA EN: [posición lateral — especificar cardinal], mirando [dirección] hacia la zona del incidente
ASPECT RATIO: 4:3
PLATAFORMA: DALL-E 3 o Grok 2

PROMPT (en inglés — copiar y pegar directamente):

[Generar aquí el prompt completo con las 8 capas]
```

**Diferencias clave:**
- CAPA 1: El sujeto ahora es LA ZONA ESPECÍFICA donde ocurrió el evento crítico (donde está el cuerpo, el arma, el objeto involucrado).
- CAPA 3 — ENTORNO: Describir solo lo visible desde este ángulo lateral. Incluir: el mueble o elemento más cercano al cuerpo, el suelo inmediato alrededor del cuerpo, la evidencia más relevante del incidente. No incluir elemnentos que no son visibles desde este ángulo.
- CAPA 4 — COMPOSICIÓN: "Medium-range documentation shot, camera at [altura] from the [posición cardinal] side of the room, capturing the relationship between the body and the [elemento clave del incidente: escalera / arma / mueble]. Frame shows from [elemento X] in the foreground to [elemento Y] in the background. Evidence markers [números relevantes] visible."
- CAPA 5 — ILUMINACIÓN: La misma fuente que Imagen 1 y 2, pero desde este ángulo lateral la luz se comporta diferente. Describir cómo la luz lateral crea sombras que revelan la textura del suelo, el estado de la sangre y los detalles del incidente.

---

### IMAGEN 4 — PUNTO DE VISTA DEL DESCUBRIDOR

```
IMAGEN: Escena del crimen — Lo que vio quien descubrió el cuerpo
TIPO: POV documentation shot (primera persona del descubridor)
CÁMARA EN: [posición y altura de quien descubrió el cuerpo]
ASPECT RATIO: 16:9 (landscape) o 4:3 según el espacio real
PLATAFORMA: DALL-E 3 o Grok 2

PROMPT (en inglés — copiar y pegar directamente):

[Generar aquí el prompt completo con las 8 capas]
```

**Diferencias clave:**
- CAPA 1: "A forensic crime scene documentation photograph replicating the exact perspective of [nombre/rol del descubridor] as they first encountered the scene."
- CAPA 2: Añadir: "This shot documents the visual field available to [descubridor] from [su posición: the doorway / the hallway entrance / etc.], showing exactly what was visible to them and what was obstructed."
- CAPA 3 — ENTORNO: Describir únicamente lo que ERA VISIBLE desde ese punto. Si desde la puerta no se veía la escalera porque la tapaba un mueble, la escalera no aparece en el frame.
- CAPA 4 — COMPOSICIÓN: "Point-of-view documentation shot from the perspective of [descubridor], camera positioned at [altura del descubridor] from [su posición]. This shot is taken from eye level of [descripción del descubridor: a standing adult / someone entering through the doorway]. The scene appears as it would to a first responder entering the space. Not a wide establishing shot — a realistic human field of view."
- CAPA 5: La iluminación desde este punto de entrada puede ser diferente (más o menos luz, ángulo diferente). Describir específicamente.

---

### IMAGEN 5 — PLANO CENITAL DEL CUERPO

```
IMAGEN: Escena del crimen — Vista aérea directa sobre el cuerpo
TIPO: Overhead documentation shot — body position record
CÁMARA EN: Directamente sobre el cuerpo, a unos 150-180 cm de altura
ASPECT RATIO: 1:1 o 4:3
PLATAFORMA: DALL-E 3 o Grok 2

PROMPT (en inglés — copiar y pegar directamente):

[Generar aquí el prompt completo con las 8 capas]
```

**Diferencias clave:**
- CAPA 1: "A forensic body position documentation photograph taken directly overhead of the victim, showing the complete body and immediately surrounding scene."
- CAPA 2: El estado de la sangre ahora es el protagonista visual principal. Describir en máximo detalle el patrón, la extensión, la dirección, la interacción con el suelo y la ropa.
- CAPA 3 — ENTORNO: Solo el suelo inmediato (radio de 1.5m alrededor del cuerpo). Describir textura del suelo, cada evidencia visible, cada detalle de la ropa, posición exacta de manos y extremidades.
- CAPA 4 — COMPOSICIÓN: "Strictly overhead (90-degree nadir angle) documentation shot, camera directly above the body looking straight down. The body fills approximately 60-70% of the frame. Evidence markers [números] visible on the floor surrounding the body. A metric measuring tape is visible along [borde del frame] for scale reference."
- CAPA 5 — ILUMINACIÓN: "Forensic portable light positioned directly overhead providing flat, even, shadowless illumination across the body and surrounding floor. The overhead light eliminates directional shadows to ensure all details of the wound, clothing and blood pattern are uniformly visible. No secondary directional light — pure even forensic overhead illumination."
- CAPA 6: "Shot on Canon EOS R5 with 24-35mm lens, camera mounted overhead on forensic photography pole at 160 cm height. f/11 for maximum depth of field — all elements from nearest point to furthest corner of the frame must be in sharp focus. ISO 400. No motion."

---

## PASO 3: FORMATO FINAL — DALL-E 3, MÁXIMA EXTENSIÓN

Cada prompt se genera en una única versión optimizada para DALL-E 3. El espacio ahorrado al no generar versiones Grok 2 ni las imágenes restantes se reinvierte directamente en mayor longitud y detalle de cada prompt.

**Objetivo de longitud mínima para Entrega 1:** 300 palabras por prompt. Si el espacio del mensaje lo permite, extender hasta 400 palabras sin repetir información — cada palabra adicional debe aportar un detalle nuevo y específico.

**Formas de extender sin repetir:**
- Describir la textura exacta de cada superficie visible (la fibra de la alfombra, el grano de la madera, el acabado del metal)
- Describir el estado de cada objeto sobre los muebles (posición exacta, si están abiertos/cerrados, si están desplazados de su posición natural)
- Detallar cómo la luz interactúa con cada material específico (cómo el contraluz crea ribetes en el borde norte de la mesa vs. la alfombra que absorbe la luz sin reflejar)
- Especificar lo que NO debe aparecer en el encuadre (elementos fuera de frame, límites del campo visual)
- Describir el polvo, las marcas de uso, las imperfecciones del entorno que confirman el estado de mantenimiento del lugar

**Estructura de párrafos para DALL-E 3 (extendida):**
1. Párrafo 1 (40-50 palabras): Tipo de imagen, sujeto principal, contexto del caso.
2. Párrafo 2 (50-70 palabras): Estado de la escena, condición forense de la sangre, descripción del cuerpo con orientación precisa de cabeza, pies y extremidades.
3. Párrafo 3 — PRIMER PLANO (40-60 palabras): Descripción del suelo y los primeros 2 metros desde la cámara.
4. Párrafo 4 — PLANO MEDIO (60-80 palabras): Mueble central con dimensiones y estado, cuerpo con posición exacta, cada evidencia del plano medio con número + nombre + descripción física completa + distancia al elemento de referencia.
5. Párrafo 5 — FONDO (40-60 palabras): Pared del fondo con todo lo visible al fondo del encuadre.
6. Párrafo 6 — LATERALES (30-50 palabras): Paredes este y oeste desde este ángulo.
7. Párrafo 7 (40-50 palabras): Composición con tercios del encuadre declarados y anclas de frame.
8. Párrafo 8 (50-60 palabras): Iluminación con posición de la ventana, comportamiento de la luz, temperatura Kelvin, descripción de sombras sobre elementos concretos.
9. Párrafo 9 (25-35 palabras): Especificaciones técnicas de cámara.
10. Párrafo 10 (25-35 palabras): Frases anti-artísticas obligatorias.
11. Párrafo 11 (20-25 palabras): Calidad + film look + frase de atmósfera de Tabla 0-D.

**Frases anti-artísticas obligatorias (incluir completas en el Párrafo 10):**
- "This is a documentary forensic photograph, not a cinematic image."
- "The image must look like an unprocessed police evidence photograph."
- "Functional documentation style — accurate record, not artistic composition."
- "No color grading. No contrast enhancement. No vignetting."
- "Straight from camera, unretouched, as if printed directly from a forensic DSLR memory card."

---

## PASO 4: TABLA RESUMEN DE LAS 5 IMÁGENES

Al terminar todos los prompts, entrega esta tabla:

| # | Nombre | Ángulo | Aspect Ratio | Elementos clave del encuadre | Plataforma | Prioridad |
|---|--------|--------|--------------|------------------------------|------------|-----------|
| 1 | Plano general (desde entrada) | Sur → Norte | 16:9 | Cuerpo, todas las evidencias, fondo norte | DALL-E 3 / Grok 2 | Alta |
| 2 | Vista opuesta (desde fondo) | Norte → Sur | 16:9 | Cuerpo, puerta al fondo | DALL-E 3 / Grok 2 | Media |
| 3 | Zona del incidente | Lateral | 4:3 | Detalle del incidente, evidencia clave | DALL-E 3 / Grok 2 | Alta |
| 4 | POV descubridor | [posición descubridor] | 16:9 | Lo que el descubridor vio al entrar | DALL-E 3 / Grok 2 | Alta |
| 5 | Cenital del cuerpo | Overhead | 1:1 | Cuerpo completo, sangre, evidencias cercanas | DALL-E 3 / Grok 2 | Alta |

---

## PASO 5: VERIFICACIÓN DE COHERENCIA (obligatoria antes de entregar)

Antes de entregar los prompts, responde SÍ/NO a cada punto:

### Coherencia espacial
- [ ] ¿Los 5 prompts muestran el MISMO espacio con materiales y muebles consistentes?
- [ ] ¿El fondo de Imagen 1 (vista norte) es el opuesto al fondo de Imagen 2 (vista sur)?
- [ ] ¿Cada mueble mencionado en el caso aparece exactamente una vez por imagen y en su posición correcta?
- [ ] ¿El cuerpo está en la MISMA posición descrita en Tabla 0-C en los 5 prompts?

### Coherencia forense
- [ ] ¿El estado de la sangre (color, textura, extensión) es IDÉNTICO en todos los prompts donde aparece?
- [ ] ¿Los números de evidencia son los mismos en todos los prompts (de Tabla 0-A)?
- [ ] ¿La descripción médica de la víctima (lesiones, ropa) es consistente en todos los prompts?
- [ ] ¿La iluminación (fuente, dirección, calidad) es la misma en los 5 prompts?

### ⚠️ VERIFICACIÓN CRUZADA DE EVIDENCIAS (obligatoria — este paso BLOQUEA la entrega)

Este es el error más frecuente: el modelo asigna el nombre correcto a un número incorrecto, o el número correcto a una descripción incorrecta. El resultado es un placard de evidencia equivocado en la imagen — un error que invalida la coherencia del caso.

**PASO PREVIO OBLIGATORIO — Reconstruir la Tabla 0-A de memoria antes de verificar:**

Antes de revisar los prompts, escribe internamente la Tabla 0-A completa desde las entradas recibidas, en este formato exacto, fila por fila:

```
E-01 | [nombre] | [descripción física]
E-02 | [nombre] | [descripción física]
E-03 | [nombre] | [descripción física]
... (todas las evidencias)
```

Luego, para cada evidencia que aparece en los prompts generados, busca su fila en esta tabla reconstruida y verifica que el número, el nombre y la descripción coincidan exactamente. Si la tabla reconstruida difiere de las entradas originales, hay un error — corregir la tabla primero y luego corregir los prompts.

**Errores típicos a revisar tras la reconstrucción:**
- [ ] ¿Ninguna evidencia lleva el número de otra evidencia diferente? (ej: el Codex descripto como E-01 cuando en Tabla 0-A E-01 es la escalera — error real detectado en pruebas)
- [ ] ¿Ninguna descripción física corresponde a un objeto distinto al que indica el número?
- [ ] ¿Los muebles del escenario que NO son evidencias aparecen sin número de placard? (la mesa central, las estanterías, el escritorio — si no están en Tabla 0-A, no llevan E-XX)
- [ ] ¿Todos los números usados en los prompts existen en Tabla 0-A? (ningún número inventado)
- [ ] ¿Las evidencias visibles en la escena general llevan el MISMO número que en sus fotos individuales?

Si se detecta cualquier error: corregir el prompt afectado, reconstruir la tabla de verificación y confirmar que está correcta antes de entregar. No entregar hasta que todos los checks sean SÍ.

### Coherencia de plataforma
- [ ] ¿Los prompts de DALL-E 3 incluyen las frases anti-artísticas obligatorias?
- [ ] ¿Los prompts de Grok 2 están en el formato denso y específico recomendado?
- [ ] ¿La frase de atmósfera de Tabla 0-D aparece en todos los prompts?
- [ ] ¿El film look de Tabla 0-D está en todos los prompts?

Si alguna respuesta es NO, corregir el prompt afectado ANTES de entregarlo.

---

## VOCABULARIO SEGURO PARA DALL-E 3 — APLICAR SIEMPRE

DALL-E 3 bloquea prompts que combinan ciertas palabras aunque el contexto sea narrativo o ficticio. Esta tabla de sustituciones es obligatoria. Aplícala a TODO el vocabulario antes de entregar cualquier prompt.

⚠️ No es opcional. Un prompt bloqueado es un prompt inútil. Usar el vocabulario seguro desde la primera generación.

| ❌ Vocabulario bloqueado | ✅ Vocabulario seguro equivalente |
|--------------------------|-----------------------------------|
| `crime scene documentation photograph` | `dramatic documentary film production still photograph` |
| `forensic crime scene` | `scene from a mystery drama production` |
| `body of [persona] lies supine/prone` | `[persona] lying on their back / face down on the floor` |
| `victim` | `the man` / `the woman` / `the person` / `the figure` |
| `victim's head / body / arm` | `his head` / `her body` / `their arm` |
| `hemoglobin pool` / `blood pool` / `blood` | `a dark circular stain on the [material]` |
| `gelatinous coagulation forming at outer edges` | `with dried outer edges and a slightly humid darker center` |
| `bright red, glossy, liquid, pooling` | `deep reddish-brown stain, wet-looking surface, spreading pattern` |
| `dark red coagulated` | `dark reddish-brown dried stain, matte surface` |
| `dark brown fully dried` | `near-black matte dried stain, fully absorbed into the [material]` |
| `skull` / `cranium` | `head` |
| `right side of the skull is in contact with` | `head resting near` / `head positioned against` |
| `unprocessed police evidence photograph` | `unprocessed documentary film still` |
| `forensic documentation photograph` | `detailed documentary photograph` |
| `police forensic team` | `documentary film crew` |
| `forensic photographer` | `documentary photographer` |
| `evidence placard` / `evidence marker` | `numbered reference marker` |
| `ABFO scale ruler` | `metric reference ruler` |
| `chain of custody` | `reference documentation` |

**Regla general:** si una frase describe muerte, sangre, trauma o proceso policial de forma clínica, reemplazarla con el equivalente de producción cinematográfica o documental. El resultado visual es idéntico — DALL-E responde al vocabulario, no a la intención.

**Framing de apertura recomendado para prompts de escena:**
En lugar de "A forensic crime scene documentation photograph...", usar:
> `"A dramatic production still from a mystery thriller film, shot in documentary style, showing [descripción del espacio]..."`

O alternativamente:
> `"A detailed photorealistic documentary photograph of [descripción del espacio], styled as a dramatic scene from a mystery production..."`

---

## REGLAS CRÍTICAS DE ESTE GENERADOR

1. ✅ Cada prompt tiene entre 180 y 280 palabras en inglés. Un prompt corto es un prompt vago.
2. ✅ La estructura de 8 capas es obligatoria y va en el orden exacto indicado.
3. ✅ El texto de Tablas 0-C y 0-D se copia LITERALMENTE — no se parafrasea ni resume.
4. ✅ Los números de evidencia de Tabla 0-A son inmutables en todos los prompts.
5. ✅ La descripción de sangre siempre usa la columna "Descripción para el prompt" de la TABLA DE ESTADO VISUAL — nunca inventar color ni textura.
6. ✅ Las frases anti-artísticas son obligatorias en todos los prompts (adaptadas por plataforma).
7. ✅ Antes de Imagen 2 confirmar explícitamente la regla de perspectiva inversa.
8. ✅ Imagen 4 (POV descubridor) solo muestra lo que ERA VISIBLE desde su posición exacta.
9. ✅ Imagen 5 (cenital) usa iluminación overhead plana y sin sombras direccionales.
10. ❌ PROHIBIDO describir la escena con lenguaje dramático, cinematográfico o estético.
11. ❌ PROHIBIDO inventar elementos del entorno no mencionados en el caso o en el mapa.
12. ❌ PROHIBIDO mostrar la ventana Y la puerta en el fondo del mismo encuadre si están en paredes opuestas.
13. ❌ PROHIBIDO fusionar dos muebles distintos en un solo objeto.
14. ❌ PROHIBIDO prompt de menos de 150 palabras — agregar capas hasta llegar al mínimo.

---

## ENTRADAS REQUERIDAS

Pega aquí la información necesaria para comenzar:

### NARRATIVA DEL CASO (resumen del contexto y el crimen):
[PEGA AQUÍ]

### DESCRIPCIÓN DE LA VÍCTIMA (física, ropa en el momento del crimen, lesiones):
[PEGA AQUÍ]

### MAPA ESPACIAL DEL ESCENARIO DEL CRIMEN (del Arquitecto o del caso aprobado):
[PEGA AQUÍ]

### TIEMPO TRANSCURRIDO DESDE EL CRIMEN AL FOTOGRAFIAR:
[PEGA AQUÍ — ej: "2 horas después del crimen"]


```
