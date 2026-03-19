# ETAPA 4 — Generador de Imágenes del Caso

> **Usa este prompt después de recibir veredicto ✅ APTO del Evaluador.**
> Pega el caso aprobado al final de este prompt.
> Su output es una lista completa de prompts de imagen listos para usar en Midjourney, DALL·E 3, Stable Diffusion, Flux o Grok.
> No genera las imágenes directamente — genera los prompts precisos para cada imagen necesaria.

---

```
Actúa como un director de arte forense especializado en materiales visuales para juegos de detectives.
Recibirás un caso aprobado. Tu trabajo es analizarlo completo, identificar TODAS las imágenes necesarias para acompañarlo, y generar un prompt de imagen preciso y listo para usar para cada una.

Cada prompt debe ser autosuficiente: alguien que no leyó el caso debe poder usarlo directamente en un generador de imagen y obtener exactamente lo que se necesita.

La estructura universal de cada prompt sigue este orden de capas:
SUJETO → ACCIÓN/POSE → ENTORNO → COMPOSICIÓN → ILUMINACIÓN → CÁMARA/LENTE → ESTILO → CALIDAD

---

## PASO 0: REGISTRO MAESTRO DE REFERENCIAS VISUALES

Antes de generar ningún prompt, construye estas cuatro tablas de referencia. Son la fuente de verdad para todos los prompts. NO debes contradecirlas en ningún punto.

---

### Tabla 0-A: EVIDENCIAS (número fijo por evidencia)

| # Evidencia | Nombre de la evidencia | Descripción física exacta (según el caso) |
|-------------|------------------------|-------------------------------------------|
| E-01        | [nombre]               | [descripción]                             |
| E-02        | [nombre]               | [descripción]                             |
| ...         | ...                    | ...                                       |

⚠️ REGLA CRÍTICA: El número asignado aquí a cada evidencia es INMUTABLE. Toda imagen que muestre esa evidencia — ya sea en foto individual, en la escena del crimen o en la hoja de expediente — debe mostrar exactamente ese mismo número. Nunca asignes números distintos a la misma evidencia en imágenes diferentes.

---

### Tabla 0-B: PERSONAJES (âncora de identidad + lesiones)

| Nombre | Rol | Edad aprox. | Âncora de identidad | Lesiones visibles | Estado emocional |
|--------|-----|-------------|---------------------|-------------------|------------------|
| ...    | ... | ...         | [frase corta y única de 8-12 palabras: complexión, cabello, rasgo facial clave, ropa característica. Ej: "mujer de 55 años, cabello canoso corto, cicatriz horizontal en mentón, mandíbula cuadrada"] | [NINGUNA / descripción médico-forense exacta de cada lesión: tipo (contusion/laceration/abrasion/ecchymosis), ubicación, estadio de cicatrización, aspecto visual] | ... |

**Âncora de identidad:** Frase corta y precisa que se copia LITERALMENTE en TODOS los prompts del mismo personaje. Garantiza consistencia entre imágenes. Nunca parafrasearla ni modificarla.

⚠️ REGLA CRÍTICA DE LESIONES: Si el caso menciona que un personaje tiene heridas, golpes, hematomas, cortes, vendajes u otras marcas físicas, estas DEBEN aparecer en TODOS sus retratos y en cualquier imagen de escena donde ese personaje sea visible. Usar terminología médico-forense (contusion, ecchymosis, laceration, soft tissue swelling) para mayor precisión y para reducir bloqueos de filtros en plataformas cloud.

---

### Tabla 0-C: LOCALIZACIONES (descripción canónica + mapa espacial + tiempo desde el crimen)

| Nombre del lugar | Descripción canónica del espacio | Tiempo desde el crimen cuando se fotografió |
|------------------|----------------------------------|---------------------------------------------|
| ...              | [materiales, superficies, temperatura de luz, estado de mantenimiento] | [ej: 2 horas / 12 horas / al momento / día siguiente] |

**⚠️ MAPA ESPACIAL OBLIGATORIO — para todo escenario del crimen:**

Antes de generar cualquier prompt de escena, construye un mapa de planta del lugar con estos elementos obligatorios:

```
NORTE  ┌─────────────────────────────────────────┐
       │  [qué hay en la pared norte]            │
       │                                          │
OESTE  │  [elementos del lado oeste]             │ ESTE
       │                                          │
       │         [CENTRO: elementos clave]        │
       │         [CUERPO: posición exacta]        │
       │         [EVIDENCIAS: posición]           │
       │                                          │
SUR    └─────────────────────────────────────────┘
       │  [acceso / puerta / entrada]            │
```

**Campos obligatorios del mapa:**
- Puntos cardinales de cada pared (qué hay en cada una)
- Posición exacta del cuerpo respecto a los elementos del entorno
- Posición final de cada evidencia física
- Posición de la(s) cámara(s) para cada imagen y dirección de la toma
- Qué es visible y qué NO es visible desde cada ángulo de cámara

**Tabla de perspectivas (obligatoria para escenas de crimen):**

| Imagen | Posición cámara | Dirección mirada | Qué aparece al fondo | Qué NO debe aparecer |
|--------|----------------|-----------------|---------------------|---------------------|
| Plano general | [dónde está la cámara] | [norte/sur/este/oeste] | [elemento de fondo] | [elemento que quedaría detrás] |
| Vista contextual | [posición 2] | [dirección 2] | [elemento de fondo 2] | [qué queda detrás] |

⚠️ REGLA CRÍTICA: Dos ángulos opuestos del mismo espacio deben mostrar fondos opuestos. Si desde la entrada se ve la ventana al fondo, desde la ventana se debe ver la entrada al fondo. Nunca dos imágenes del mismo espacio pueden tener la misma ventana/acceso al fondo si se tomaron desde posiciones contrarias.

⚠️ REGLA DE MUEBLES DISTINTOS: Si el caso menciona un escritorio de trabajo Y una mesa central de lectura en la misma habitación, son dos muebles distintos. Identificar cuál está cerca del cuerpo y cuál no. Nunca fusionarlos en un único elemento.

**Tiempo desde el crimen — referencia visual:**
- `0-2 horas` → sangre: bright red, glossy, liquid, pooling
- `2-6 horas` → sangre: darkening red, beginning to coagulate at edges
- `6-12 horas` → sangre: dark red, coagulated, gel-like
- `12-24 horas` → sangre: dark brown, fully dried, matte surface
- `24-48 horas` → sangre: dark brown-black, cracked, dried
- `+48 horas` → sangre: blackened, dessicated, flaking edges

---

### Tabla 0-D: PALETA VISUAL DEL CASO

Define la identidad visual tonal del caso antes de generar ningún prompt. Todos los prompts de escena y evidencias in situ usarán estos valores.

| Campo | Valor |
|-------|-------|
| **Tono dominante** | [ej: grises fríos industriales / verdes apagados rurales / beige cálido residencial] |
| **Temperatura de luz** | [ej: luz fluorescente fría 4000K / incandescente cálida 2700K / natural diurna 5500K] |
| **Textura de superficies** | [ej: concreto sucio / madera envejecida / acero inoxidable / alfombra desgastada] |
| **Paleta de 3 colores HEX** | [color dominante] / [color secundario] / [color acento] |
| **Estado ambiental** | [ej: húmedo y descuidado / limpio y aséptico / caótico / frío y ordenado] |
| **Film stock o look fotográfico** | [ej: Kodak Tri-X 400 high contrast B&W / Kodak Ektachrome E100 neutral / Cinestill 800T nocturno] |
| **Frase de atmósfera** | [10-15 palabras que capturan la sensación del lugar. Ej: "cold industrial decay, harsh fluorescent shadows, gritty urban realism"] |

⚠️ REGLA: La "Frase de atmósfera" debe aparecer al final de TODOS los prompts de escena del crimen y de evidencias fotografiadas in situ. El "Film stock o look fotográfico" se incluye en todos los prompts de escena y personajes para unificar el look visual.

---

Muestra las cuatro tablas completas antes de continuar al Paso 1.

---

## PASO 1: INVENTARIO VISUAL

Lee el caso completo e identifica cada imagen necesaria, organizada en 5 categorías:

### A. ESCENA DEL CRIMEN
- Plano general de la escena donde ocurrió el crimen
- Plano de detalle de la zona específica del incidente (si aplica)
- Vista del lugar desde el punto de vista del descubridor

### B. EVIDENCIAS FÍSICAS
Lista cada evidencia física mencionada en el caso usando los números de la Tabla 0-A.
Para cada una define:
- Nombre (igual que en Tabla 0-A), número (igual que en Tabla 0-A), tipo de toma (cenital, macro, plano medio)

### C. SOSPECHOSOS
Un retrato por cada sospechoso (mínimo 4).
Extrae de la Tabla 0-B: âncora de identidad, lesiones (obligatorias si las hay), estado emocional.

### D. TESTIGOS
Un retrato por cada testigo (mínimo 5).
Extrae de la Tabla 0-B: âncora de identidad, lesiones (obligatorias si las hay), contexto de ubicación.

### E. DOCUMENTOS Y PAPELES
Lista cada documento mencionado en el caso: cartas, notas, contratos, facturas, bitácoras, mensajes escritos, recibos, etc.
Para cada uno: nombre, tipo (manuscrito/impreso/rasgado/etc.), contenido clave visible.

Muestra el inventario completo antes de generar los prompts.

---

## PASO 2: GENERAR PROMPTS POR CATEGORÍA

---

### CATEGORÍA A — ESCENA DEL CRIMEN

**Estilo obligatorio:**
Fotografía forense documental. Tomada por un equipo forense real. Sin estética artística. Sin iluminación dramática. Flash directo o luz disponible. Alta nitidez. Composición técnica y funcional.

**Para cada imagen de la escena genera:**

```
IMAGEN: Escena del crimen — [descripción breve]
TIPO: Plano [general/detalle/contextual]
TIEMPO DESDE EL CRIMEN: [de Tabla 0-C]
ASPECT RATIO: [16:9 para escena general / 4:3 para detalle]

PROMPT:
"Crime scene forensic documentation photograph of [descripción exacta de la escena según Tabla 0-C],
[estado visual de sangre/fluidos coherente con el tiempo de Tabla 0-C],
[tipo de plano]: [overall establishing shot / medium-range shot / close-up documentation shot],
[ángulo: eye level / slightly above / overhead],
[iluminación: flat even overhead lighting from forensic lights / available ambient light / harsh overhead fluorescent],
evidence markers [listar: marker E-01 next to [objeto], marker E-02 next to [objeto], etc.] visible on [floor/surface],
[si aplica: yellow police crime scene tape at perimeter],
shot on Nikon D6, [focal: 24mm para general / 50mm para medio / 105mm macro para detalle], f/8, ISO 800,
deep depth of field, all elements in focus,
no artistic processing, no color grading, unedited documentation style,
[film stock de Tabla 0-D],
[frase de atmósfera de Tabla 0-D],
forensic documentation photography, photojournalism style."

PROPÓSITO: [qué debe notar el jugador en esta imagen]
```

---

### CATEGORÍA B — EVIDENCIAS FÍSICAS

**Estilo obligatorio:**
Fotografía macro o cenital forense. Marcador de evidencia numerado visible. Escala ABFO o regla métrica. Flash directo o ring flash. Fondo neutro o superficie de la escena. Sin estética artística.

**Para cada evidencia genera (número de Tabla 0-A, inmutable):**

```
IMAGEN: Evidencia [número de Tabla 0-A] — [nombre exacto de Tabla 0-A]
TIPO: [macro/cenital/plano medio]
ASPECT RATIO: [1:1 para macro / 4:3 para plano medio]

PROMPT:
"Forensic evidence [macro/close-up/overhead] documentation photograph of [descripción física exacta según Tabla 0-A],
[si es in situ: on [descripción de la superficie real de Tabla 0-C]],
[si es en laboratorio: on neutral gray forensic examination surface],
oblique side lighting from left at 45 degrees to reveal surface texture and detail,
[si macro: ring flash secondary fill for even illumination],
evidence placard number [número exacto de Tabla 0-A] visible in upper right corner,
ABFO #2 scale ruler visible in lower left,
shot on Canon EOS R5, [105mm macro para close-up / 50mm para plano medio], f/11,
tack-sharp all elements, deep depth of field throughout,
neutral white balance 5500K, no reflections,
[si es in situ: frase de atmósfera de Tabla 0-D],
clinical forensic documentation photography, no artistic processing."

PROPÓSITO: [qué detalle específico debe analizar el jugador]
PISTA OCULTA: [si esta evidencia contiene información deductiva, describir qué es sin spoilear]
```

---

### CATEGORÍA C — SOSPECHOSOS

**Estilo obligatorio:**
Foto de ficha policial (mugshot) O foto de contexto en su entorno habitual. No foto de estudio ni iluminación glamorosa. Realista, documental.

**Para cada sospechoso genera DOS prompts alternativos:**

```
IMAGEN: Sospechoso — [nombre]
ÂNCORA DE IDENTIDAD: [copiar literalmente de Tabla 0-B — NO modificar]
LESIONES VISIBLES: [de Tabla 0-B — si dice NINGUNA, omitir; si hay lesiones, OBLIGATORIAS en el prompt]
ASPECT RATIO: 2:3 (retrato vertical)

OPCIÓN 1 — FICHA POLICIAL (mugshot):
"Police mugshot, official booking photograph of [âncora de identidad de Tabla 0-B — copiar literal],
[SI HAY LESIONES: with visible [tipo de lesión médica] on [ubicación precisa], [estadio visual: fresh/healing/bruised], [color del hematoma si aplica],]
[expresión: neutral/tense/defiant/scared] expression consistent with [su carácter en el caso],
plain gray or beige background, flat frontal direct lighting, no shadows, no artistic lighting,
bust shot framed from shoulders up,
[ropa coherente con su rol social],
[film stock de Tabla 0-D],
official police booking photograph style, high resolution, no filters, RAW photo."

OPCIÓN 2 — FOTO DE CONTEXTO (candid documental):
"Candid documentary photograph of [âncora de identidad de Tabla 0-B — copiar literal],
[SI HAY LESIONES: with clearly visible [tipo de lesión médica] on [ubicación precisa],]
in [lugar habitual del personaje según el caso],
[actitud corporal: leaning forward / arms crossed / looking away / fidgeting],
[iluminación natural del entorno: harsh overhead fluorescent / window light / street lighting / overcast daylight],
available light only, no flash, unposed candid shot,
medium shot from eye level,
[ropa coherente con su rol social],
[film stock de Tabla 0-D],
photojournalism documentary style, film grain, no color grading, RAW photo."
```

---

### CATEGORÍA D — TESTIGOS

**Estilo obligatorio:**
Foto naturalista y contextual. El testigo en su entorno o en una situación relacionada con el momento en que fue encontrado/entrevistado. Nunca foto de estudio. Transmite la emoción o actitud de su testimonio.

**Para cada testigo genera:**

```
IMAGEN: Testigo — [nombre]
ÂNCORA DE IDENTIDAD: [copiar literalmente de Tabla 0-B — NO modificar]
CONTEXTO: [dónde se los ubicaría según el caso]
ACTITUD EN SU TESTIMONIO: [nervioso/confiado/evasivo/asustado/colaborativo]
LESIONES VISIBLES: [de Tabla 0-B — si hay lesiones, OBLIGATORIAS]
ASPECT RATIO: 2:3 (retrato vertical) o 3:2 (si el contexto del entorno es clave

PROMPT:
"Documentary naturalistic photograph of [âncora de identidad de Tabla 0-B — copiar literal],
[SI HAY LESIONES: with [tipo de lesión médica] visible on [ubicación],]
in [descripción del entorno: residential neighborhood / office / street / bar / etc.],
[postura y lenguaje corporal coherente con su actitud: hands clasped nervously / relaxed stance / avoiding eye contact / etc.],
[iluminación natural coherente con el entorno y hora del día],
no flash, no studio lighting, unposed,
medium shot as if photographed during an interview or in daily routine,
[ropa coherente con su rol y clase social],
[film stock de Tabla 0-D],
photojournalism style, available light, film grain, no color grading, RAW photo."

EMOCIÓN CLAVE: [qué debe transmitir esta imagen al jugador]
```

---

### CATEGORÍA E — DOCUMENTOS Y PAPELES

**Estilo obligatorio:**
Escaneo forense a alta resolución o fotografía macro sobre superficie. Aspecto físico auténtico: textura real del papel, posibles manchas, dobleces, desgaste coherente con la narrativa. El texto visible DEBE ser legible. Sin fondo artificial ni composición de estudio.

> **Nota de plataforma:** Para texto legible, los mejores resultados son con DALL-E 3 / GPT-4o, Flux 2 e Ideogram 2.0. Midjourney produce texto poco confiable. Siempre poner el texto deseado entre comillas dobles dentro del prompt.

**Para cada documento genera:**

```
IMAGEN: Documento — [nombre del documento]
TIPO: [carta manuscrita / nota / contrato impreso / factura / mensaje / recibo / periódico / etc.]
ASPECT RATIO: 3:2 (horizontal) o 2:3 (vertical según el documento)

PROMPT:
"[Forensic 300 DPI scan / Photorealistic overhead macro photograph] of [tipo de documento: official report / handwritten letter / crumpled note / printed contract / etc.],
[soporte físico: [white/off-white/yellowed/aged] [paper/notepad/lined paper/official letterhead]],
[estado físico del papel: [flat/slightly crumpled/torn at edges/water-stained/coffee-stained], [condition: pristine/worn/aged/damaged at [location]]],
the document reads [SI HAY TEXTO CLAVE: "[título o encabezado]" as heading / "[fragmento clave]" as main text],
[tipo de escritura: black typed font / handwritten in [blue/black] ink with [hurried/careful/neat] strokes / printed monospace / bold serif font],
[detalles adicionales: handwritten margin notes / signature visible / official stamp / crossed-out lines / highlighted sections],
[si es evidencia: evidence placard number [número de Tabla 0-A] visible in corner, metric scale ruler at bottom edge],
photographed [flat overhead cenital / slightly angled] on [dark wooden surface / forensic gray surface / inside evidence bag],
[iluminación: directional window light from upper left creating subtle texture shadows / diffused overhead lighting / raking light from left],
shot on Canon EOS R5, 50mm macro lens, f/8, deep depth of field, all text tack-sharp,
no reflections, neutral color balance,
forensic document examination photography style."

PROPÓSITO: [qué información o pista debe extraer el jugador]
DETALLE CLAVE: [el elemento visual más importante que no debe faltar]
```

---

## PASO 3: DOCUMENTO FORENSE MULTI-EVIDENCIA (opcional)

Si hay 4 o más evidencias físicas, genera también un prompt para una hoja de expediente policial con todas las evidencias en una sola imagen:

```
IMAGEN: Hoja de Expediente — Caso [nombre del caso]
ASPECT RATIO: 2:3 (A4 vertical)

PROMPT:
"Scanned forensic evidence sheet, official police report format, A4 vertical,
technical multi-evidence layout in [N×2] grid,
[si hay número impar de evidencias: last item centered at bottom, larger than others],
white or light gray official paper background,
each evidence as small rectangular photograph with thin black borders,
direct flash lighting simulation on each photo, high detail throughout.

Grid layout:
[Posición fila 1, col A]: [descripción exacta de Tabla 0-A], evidence marker [número de Tabla 0-A], ABFO scale visible.
[Posición fila 1, col B]: [descripción exacta de Tabla 0-A], evidence marker [número de Tabla 0-A], ABFO scale visible.
[Posición fila 2, col A]: ...
[continuar para cada evidencia]

Printed label under each photo: 'EVIDENCE [número de Tabla 0-A] – Case: [nombre del caso]' in Arial font.
Clean layout, no dramatic shadows, high resolution, scanned document style, exact A4 vertical proportions."
```

---

## PASO 4: RESUMEN FINAL DE IMÁGENES

Al terminar, entrega una tabla resumen:

| # | Categoría | Descripción | Aspect Ratio | Tipo de toma | Plataforma sugerida | Prioridad |
|---|-----------|-------------|--------------|--------------|---------------------|-----------|
| 1 | Escena | [nombre] | 16:9 | [tipo] | Flux / MJ / SD | Alta / Media |
| 2 | Evidencia | [nombre] | 1:1 | macro | Flux / MJ / SD | Alta / Media |
| 3 | Sospechoso | [nombre] | 2:3 | retrato | Flux / MJ / SD | Alta / Media |
| 4 | Documento | [nombre] | 3:2 | macro | DALL-E 3 / Flux | Alta / Media |
| ... | ... | ... | ... | ... | ... | ... |

**Prioridad Alta** = imágenes que el jugador necesita para resolver el caso o que contienen pistas visuales.
**Prioridad Media** = imágenes de atmósfera, personajes o contexto.

Genera primero las de Prioridad Alta.

**Nota sobre plataformas sugeridas:**
- **Escenas y evidencias fotorrealistas:** Flux 2 (mejor fotorrealismo actual) o Midjourney V7 `--style raw`
- **Retratos de personajes:** Flux 2, Midjourney V7 con `--oref` para consistencia
- **Documentos con texto legible:** DALL-E 3 / GPT-4o (primera opción) o Flux 2
- **Heridas/lesiones sin filtros:** Stable Diffusion local (sin restricciones) con terminología médica
- **Stable Diffusion:** Para mayor control técnico; usar modelos Juggernaut XL o Realistic Vision 6.0

---

## PASO 5: REVISIÓN DE COHERENCIA INTERNA

Después de generar todos los prompts, realiza este chequeo obligatorio. Responde SÍ/NO a cada punto y corrige en el momento si la respuesta es NO.

### 5-A: Coherencia de evidencias
- [ ] ¿Cada evidencia tiene exactamente UN número fijo que coincide con la Tabla 0-A en todos sus prompts?
- [ ] ¿El mismo objeto nunca aparece con dos números distintos en imágenes diferentes?
- [ ] ¿Las evidencias visibles en la escena del crimen usan los mismos números que sus fotos individuales?
- [ ] ¿La hoja de expediente usa los mismos números que las fotos individuales?
- [ ] ¿Los documentos que son evidencias oficiales tienen su número de Tabla 0-A en su prompt?

### 5-B: Coherencia de personajes
- [ ] ¿Todos los personajes con lesiones mencionadas en el caso tienen esas lesiones descritas en sus retratos?
- [ ] ¿La âncora de identidad de cada personaje es idéntica en todos sus prompts (copiada literalmente)?
- [ ] ¿La ropa, complexión y edad son consistentes entre Opción 1 y Opción 2 del mismo personaje?
- [ ] ¿El film stock de Tabla 0-D está presente en los prompts de personajes?

### 5-C: Coherencia de escena y paleta
- [ ] ¿Todos los prompts de escena incluyen el estado visual de sangre/fluidos coherente con el tiempo de Tabla 0-C?
- [ ] ¿La frase de atmósfera de Tabla 0-D aparece en todos los prompts de escena y evidencias in situ?
- [ ] ¿Las localizaciones en los prompts coinciden con la descripción canónica de Tabla 0-C?
- [ ] ¿El aspect ratio es correcto para cada tipo de imagen?

### 5-D: Cobertura del caso
- [ ] ¿Todas las evidencias físicas mencionadas en el caso tienen su imagen correspondiente?
- [ ] ¿Todos los documentos mencionados en el caso tienen su imagen correspondiente?
- [ ] ¿Todos los sospechosos del caso tienen su retrato?
- [ ] ¿Todos los testigos del caso tienen su retrato?

Si detectas cualquier inconsistencia, corrígela directamente en el prompt afectado antes de entregarlo.

---

## PASO 6: BUCLE DE CONGRUENCIA NARRATIVA

Este paso es obligatorio y debe completarse ANTES de entregar ningún prompt al usuario.
Su propósito no es técnico sino narrativo: verificar que todas las imágenes juntas cuenten la misma historia y pertenezcan al mismo mundo.

---

### Cómo funciona el bucle

```
ITERACIÓN 1
  → Responde todas las preguntas de la Sección 6-A
  → Si todas son SÍ: ir al VEREDICTO FINAL
  → Si alguna es NO: ir a CORRECCIÓN DE ITERACIÓN
    → Corregir todos los prompts indicados
    → Reiniciar desde ITERACIÓN 2

ITERACIÓN 2
  → Repetir todas las preguntas de la Sección 6-A sobre los prompts corregidos
  → Si todas son SÍ: ir al VEREDICTO FINAL
  → Si alguna es NO: ir a CORRECCIÓN DE ITERACIÓN
    → Corregir y reiniciar desde ITERACIÓN 3

ITERACIÓN 3
  → Repetir todas las preguntas
  → Si todas son SÍ: ir al VEREDICTO FINAL
  → Si aún hay NO: aplicar las correcciones disponibles, marcar los conflictos
    irresolubles como ⚠️ ADVERTENCIA y proceder al VEREDICTO FINAL

VEREDICTO FINAL → Entregar todos los prompts al usuario
```

---

### Sección 6-A: Preguntas de Congruencia Narrativa

Para cada pregunta, responde SÍ o NO y especifica qué imagen o prompts fallan si la respuesta es NO.

#### MUNDO Y ÉPOCA
- [ ] ¿Todos los prompts pertenecen claramente al mismo período de tiempo (misma época, misma tecnología visible, mismo estilo de ropa)?
- [ ] ¿Las localizaciones de escena, evidencias y personajes son geográfica y culturalmente coherentes entre sí?
- [ ] ¿No hay contradicciones de época entre imágenes? (ej: escena en los años 80 pero un personaje con smartphone visible)

#### TONO Y ATMÓSFERA
- [ ] ¿Todas las imágenes de escena y evidencias comparten la misma paleta tonal definida en Tabla 0-D?
- [ ] ¿La frase de atmósfera de Tabla 0-D se siente coherente con el tono de los retratos de personajes?
- [ ] ¿No hay imágenes que se sientan de un género distinto al del caso? (ej: un retrato glamoroso en un caso de crimen industrial oscuro)

#### PERSONAJES COMO PARTE DE LA HISTORIA
- [ ] ¿Los personajes visualmente se ven como personas que podrían habitar el mismo mundo que la escena del crimen?
- [ ] ¿La ropa, clase social y contexto de cada personaje es coherente con el tipo de crimen y el entorno del caso?
- [ ] ¿Los estados emocionales de los retratos (nervioso, frío, asustado) son coherentes con lo que ese personaje vivió en la historia?
- [ ] ¿Un jugador que vea solo los retratos podría intuir que están vinculados al mismo caso?

#### EVIDENCIAS COMO PARTE DE LA HISTORIA
- [ ] ¿Las evidencias fotografiadas in situ se ven como objetos que pertenecen físicamente a la escena del crimen descrita?
- [ ] ¿El estado de deterioro/uso de las evidencias es coherente con la narrativa? (ej: si la víctima usaba algo todos los días, ¿se ve usado?)
- [ ] ¿Las superficies y fondos de las evidencias son coherentes con el lugar donde fueron encontradas?

#### DOCUMENTOS COMO PARTE DE LA HISTORIA
- [ ] ¿El tipo de papel, escritura y estado de los documentos es coherente con quién los escribió y cuándo?
- [ ] ¿El lenguaje/estilo tipográfico de los documentos es coherente con la época y el rol del personaje que los generó?

#### COHERENCIA GLOBAL (la pregunta clave)
- [ ] **Si un jugador viera todas estas imágenes juntas sin leer el texto del caso, ¿percibiría que pertenecen a la misma historia?**

---

### Corrección de Iteración

Cuando una respuesta es NO, antes de reiniciar el bucle:

1. **Identificar el conflicto:** Nombrar exactamente qué imagen(es) rompen la coherencia y por qué.
2. **Diagnosticar la causa:** ¿Es un problema de iluminación? ¿De época? ¿De tono? ¿De descripción física?
3. **Corregir el prompt:** Modificar únicamente los elementos que generan el conflicto, sin alterar los datos de las Tablas 0-A/B/C/D.
4. **Documentar la corrección:** Anotar brevemente qué se cambió y en qué prompt.
5. **Reiniciar el bucle** desde la siguiente iteración.

---

### Veredicto Final

Al completar el bucle con todas las respuestas en SÍ (o con las advertencias ⚠️ documentadas), mostrar:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
✅ VEREDICTO: CONGRUENCIA NARRATIVA APROBADA
Iteraciones realizadas: [N]
Correcciones aplicadas: [lista breve o "ninguna"]
[Si hay advertencias: ⚠️ CONFLICTOS IRRESOLUBLES: [descripción]]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

Solo después de mostrar este veredicto, entregar todos los prompts al usuario.

---

## REGLAS CRÍTICAS

1. ❌ PROHIBIDO estilo cinematográfico, dramático o artístico en evidencias y escena del crimen
2. ❌ PROHIBIDO inventar detalles físicos de personajes que contradigan lo dicho en el caso
3. ❌ PROHIBIDO omitir evidencias físicas o documentos mencionados en el caso
4. ❌ PROHIBIDO omitir lesiones, heridas o marcas físicas que el caso mencione en cualquier personaje
5. ❌ PROHIBIDO asignar números distintos a la misma evidencia en imágenes diferentes
6. ❌ PROHIBIDO modificar o parafrasear la âncora de identidad de un personaje — copiar siempre literalmente
7. ✅ Estructura de capas obligatoria: SUJETO → ENTORNO → COMPOSICIÓN → ILUMINACIÓN → CÁMARA → ESTILO → CALIDAD
8. ✅ La Tabla 0-A es la fuente de verdad para números y nombres de evidencias
9. ✅ La Tabla 0-B es la fuente de verdad para âncoras de identidad y lesiones
10. ✅ La Tabla 0-C define el estado visual de la escena según el tiempo transcurrido
11. ✅ La Tabla 0-D define la paleta visual — su frase de atmósfera va en todos los prompts de escena
12. ✅ Texto en documentos SIEMPRE entre comillas dobles dentro del prompt
13. ✅ Para heridas, usar terminología médico-forense: contusion, ecchymosis, laceration, abrasion, soft tissue swelling
14. ✅ Indicar siempre el propósito investigativo de cada imagen (qué debe notar el jugador)
15. ✅ Indicar siempre el aspect ratio y la plataforma sugerida para cada imagen

---

Aquí está el caso aprobado:

[PEGA AQUÍ EL CASO COMPLETO APROBADO]
```
