# GUÍA COMPLETA: MEJORES PRÁCTICAS PARA PROMPTS DE IMÁGENES CON IA

## Investigación profunda — Midjourney, DALL-E 3, Stable Diffusion, Grok/Aurora, Flux

---

## 1. ESTRUCTURA ÓPTIMA DE UN PROMPT DE IMAGEN

### El Orden Universal de los Elementos

El orden importa. Todos los modelos ponderan los elementos al principio del prompt con mayor peso semántico. La estructura estándar recomendada en 2025-2026 es:

```
[SUJETO] + [ACCIÓN/POSE] + [ENTORNO] + [COMPOSICIÓN] + [ILUMINACIÓN] + [CÁMARA/LENTE] + [ESTILO] + [ESTADO ÁNIMO] + [PARÁMETROS TÉCNICOS]
```

**Fórmula básica:**
```
Sujeto + Medio fotográfico + Iluminación + Aspect Ratio
```

Ejemplo:
```
Woman sitting in a cafe, analog 35mm photography, golden hour window light --ar 4:5 --v 7
```

---

### Estructura Detallada por Capas (prompts avanzados)

| Capa | Contenido | Ejemplo |
|------|-----------|---------|
| 1. Sujeto (PRIMERO, siempre) | Persona, objeto, escena principal | "A 35-year-old Latino man with a beard" |
| 2. Acción/Pose | Qué hace o cómo está | "sitting at a wooden table, leaning forward" |
| 3. Entorno | Dónde está, qué lo rodea | "in a dimly lit interrogation room, concrete walls" |
| 4. Composición | Tipo de plano, ángulo | "medium shot, slightly above eye level" |
| 5. Iluminación | Fuente, dirección, calidad | "single overhead fluorescent light, harsh shadows" |
| 6. Cámara y lente | Equipo, focal, apertura | "shot on Canon EOS R5, 50mm lens, f/2.8" |
| 7. Estilo fotográfico | Género, referencia | "documentary photography, candid style" |
| 8. Calidad | Keywords de calidad | "photorealistic, RAW photo, 8K, sharp focus" |

---

### Ejemplo de Prompt Completo con todas las Capas

```
A weathered 45-year-old man with tired eyes and three-day stubble, sitting hunched in a plastic chair, hands on the table, inside a bare interrogation room with peeling paint and fluorescent lights, medium shot from slightly above, harsh overhead lighting casting deep shadows under his eyes, shot on Sony Alpha a7 III, 35mm lens, f/2.8, photorealistic documentary photography, RAW photo, available light, no flash, film grain, 4K --ar 3:2 --style raw --v 7
```

---

### Fórmula Universal (funciona en todos los modelos)

```
[Tipo de imagen] of [sujeto principal], [descripción del sujeto], [acción], [entorno/fondo], [iluminación], [estilo fotográfico], [cámara y lente], [palabras de calidad]
```

---

### Diferencias de Estructura por Plataforma

**Midjourney V7:**
```
Frases cortas y de alto impacto — Sujeto, medio, estado de ánimo, parámetros técnicos
"exhausted detective, fluorescent office lighting, close-up, 35mm --ar 16:9 --style raw --ow 100"
```

**Stable Diffusion (SDXL / Pony / Juggernaut):**
```
Keywords con pesos — (masterpiece:1.2), (photorealistic:1.1), separados por coma
Prompt: "RAW photo, (photorealistic:1.4), man in dark room, harsh lighting, 35mm lens, f2.8, film grain, (best quality:1.3)"
Negative: "cartoon, 3d, anime, CGI, painting, blurry, bad anatomy, deformed"
```

**DALL-E 3 / GPT-4o:**
```
Lenguaje natural conversacional, frases completas
"A high-resolution documentary photograph of an exhausted middle-aged detective sitting in a fluorescent-lit office..."
```

**Flux 1/2:**
```
Lenguaje natural detallado, sujeto primero, sin negative prompts
"A 35-year-old man with tired eyes, sitting at a cluttered wooden desk under harsh fluorescent lighting, shot on Canon 5D Mark IV, 35mm lens at f/2.8..."
```

**Grok/Aurora:**
```
Descriptivo y específico, iterar gradualmente, comenzar simple
"Product photo of [subject] on [surface], [lighting] lighting, [composition] composition"
```

---

## 2. PARÁMETROS TÉCNICOS: RESOLUCIÓN, ASPECT RATIO, CÁMARA, LENTES, ILUMINACIÓN

### Aspect Ratios Estándar

| Ratio | Uso | Plataformas |
|-------|-----|-------------|
| `1:1` | Cuadrado, redes sociales, producto | Todas |
| `4:3` | Fotografía clásica, presentaciones | Todas |
| `3:2` | DSLR estándar, impresión fotográfica | Todas |
| `16:9` | Cine, pantallas, paisajes | Todas |
| `9:16` | Vertical, móvil, retratos | Todas |
| `2:3` | Retrato vertical, impresión | Todas |
| `21:9` | Ultra panorámico, cine amplio | Midjourney, Flux |

**En Midjourney:** `--ar 16:9` | **En SD:** definir resolución (1920×1080, 1024×1024, etc.) | **En DALL-E 3:** "landscape format" o "portrait format"

---

### Cámaras por Uso y Efecto

| Propósito | Cámara Recomendada |
|-----------|-------------------|
| Retratos profesionales | Sony Alpha a7R V, Nikon Z9, Canon EOS R5 |
| Fotografía de acción | Sony A9 III, Canon EOS R10 |
| Paisajes | Fujifilm GFX100S, Hasselblad X1D |
| Vintage/Analógica | Canon AE-1, Nikon FM2, Pentax K1000 |
| Formato medio | Hasselblad 500c/m, Fujifilm GFX100S |
| Documental/Street | Leica M10, Leica M6, Fujifilm X-T5 |
| Fotoperiodismo | Canon EOS-1DX, Nikon D6 |

---

### Lentes y sus Efectos

| Focal/Lente | Efecto Visual | Uso |
|------------|---------------|-----|
| `16mm` | Ultra gran angular, distorsión espacial | Arquitectura, espacio amplio |
| `24mm` | Gran angular suave | Paisaje, interior |
| `28mm` | Reportaje, documentales | Fotoperiodismo |
| `35mm` | Perspectiva natural, calle | Documental, street, cine |
| `50mm` | "Ojo humano", neutro | Retratos ambientales, documental |
| `85mm` | Retrato clásico, bokeh | Retratos, intimidad |
| `105mm` | Macro, detalle extremo | Close-up, heridas, evidencia |
| `135mm` | Compresión, aislamiento | Teleobjetivo suave |
| `200mm+` | Teleobjetivo, compresión extrema | Vigilancia, sport |
| `Macro lens` | Detalles extremos, 1:1 | Evidencia forense, heridas |

> **Nota:** En Midjourney no uses shutter speed ni ISO como números directos — describe el efecto: "shallow depth of field", "motion blur", "film grain from high ISO".

---

### Apertura y Profundidad de Campo

| Apertura | Efecto | Descripción en prompt |
|---------|--------|----------------------|
| f/1.2 - f/1.8 | Bokeh extremo, sujeto aislado | "very shallow depth of field, dreamy bokeh" |
| f/2.8 | Bokeh suave, retrato | "shallow depth of field, soft bokeh background" |
| f/5.6 | Transición | "moderate depth of field" |
| f/8 | Todo enfocado | "deep depth of field" |
| f/11 - f/16 | Nitidez total | "tack-sharp from foreground to background, f/11" |

---

### Películas / Film Stock

| Película | Efecto | Uso |
|---------|--------|-----|
| `Kodak Portra 400` | Skin tones cálidos, grano fino | Retratos, fotomoda |
| `Kodak Tri-X 400` | B&N, grano alto contraste | Fotoperiodismo, documental |
| `Fujifilm Pro 400H` | Tonos fríos, delicados | Retratos suaves |
| `Fujifilm Velvia 50` | Colores saturados, intensos | Paisaje, naturaleza |
| `Kodak Ektachrome E100` | Colores fieles, neutros | Documental, periodismo |
| `Cinestill 800T` | Halos rojos, noche urbana | Nocturno, street |

---

## 3. PALABRAS CLAVE QUE MEJORAN LA CALIDAD

### Keywords de Calidad Universal

```
RAW photo
DSLR photo
analog photography
photorealistic
hyperrealistic
ultra-realistic
photorealism
award-winning photo
National Geographic photography
professional photograph
8K / 4K UHD
HDR / high dynamic range
ultra-sharp / sharp focus / tack-sharp
high detail / fine detail / intricate details
highly detailed
skin pores visible
natural skin texture
```

---

### Para Stable Diffusion (con sintaxis de peso)

```
(RAW photo:1.3), (photorealistic:1.4), (realistic:1.2), (masterpiece:1.2),
(best quality:1.3), (ultra high res:1.2), (detailed skin:1.1), (sharp focus:1.2)
```

---

### Para Midjourney

```
--style raw          → Reduce estilización artística, más realista
--stylize 0          → Mínima estilización (más fiel al prompt)
--stylize 250        → Balance recomendado para fotorrealismo
--v 7                → Versión más reciente, mejor fotorrealismo
photo realistic
shot on [camera model]
```

---

### Keywords para "Imperfecciones Realistas" (más auténtico)

Una foto real NO es perfecta. Estas keywords rompen la "perfección artificial":

```
film grain
high ISO noise
slight motion blur
lens vignetting
chromatic aberration
slight overexposure
dust particles
visible pores
natural skin texture
candid shot / unposed
slight camera shake
handheld camera
available light / no flash
unedited RAW
IMG_[número].CR2       (truco Flux — simula archivo RAW de Canon)
```

---

### Keywords para Fotografía Documental / Periodística

```
documentary photography
photojournalism style
reportage photography
available light / ambient light
candid / unposed / natural expression
35mm documentary
Leica documentary style / Magnum Photos style
street photography
no studio lighting
fluorescent light / existing light conditions
```

---

### Keywords Anti-Artísticos (rompe la tendencia AI hacia arte digital)

```
not a painting / not an illustration / not digital art
no artistic filter / no color grading
not stylized / unprocessed / straight from camera
```

---

## 4. CONSISTENCIA DE PERSONAJES ENTRE MÚLTIPLES IMÁGENES

### Midjourney V6: Parámetro `--cref` (Character Reference)

```
/imagine [descripción de nueva escena] --cref [URL de imagen del personaje] --cw 100
```

**`--cw` (Character Weight):**
- `--cw 0`: Solo copia el estilo/ropa, no el rostro
- `--cw 50`: Balance entre cara y estilo
- `--cw 100`: Copia maximamente la apariencia (default)

---

### Midjourney V7: Omni Reference `--oref`

```
/imagine [descripción] --oref [URL imagen referencia] --ow [1-1000]
```

| Rango `--ow` | Efecto | Uso recomendado |
|-------------|--------|-----------------|
| `25-50` | Influencia sutil | Foto → Anime, variaciones estéticas |
| `100-300` | Balance — guía sin dominar | Uso general, escenas diferentes |
| `400-1000` | Preservación fuerte de detalles faciales | Cuando la cara exacta es crítica |

**Diferencia clave:**
- `--cref` controla el "quién" (sujeto)
- `--sref` controla el "cómo" (estética)
- `--oref` en V7 unifica ambos en un solo parámetro

---

### Stable Diffusion: InstantID + ControlNet

Para consistencia de personajes, el método más potente es **InstantID**:

1. InsightFace extrae los embeddings faciales de la imagen de referencia
2. IP-Adapter usa esos embeddings para controlar la generación
3. ControlNet detecta y preserva los puntos de referencia faciales

**IP-Adapter FaceID Plus v2:** Copia solo el rostro — permite diferentes ángulos manteniendo la identidad.

---

### Tips Universales para Consistencia

1. **Âncora textual:** Repetir la descripción EXACTA del personaje en cada prompt (mismo orden, mismas palabras)
2. **Misma seed numérica** cuando sea posible
3. **Misma cámara y lente** en todos los prompts del mismo personaje
4. **La imagen fuente**: una sola persona, de frente, buena iluminación, rasgos faciales claros, fondo neutro
5. **No cambiar demasiado a la vez:** cambiar fondo y pose a la vez reduce consistencia

---

## 5. ILUMINACIÓN FORENSE, DOCUMENTAL Y PERIODÍSTICA

### Vocabulario Técnico de Iluminación Forense

```
harsh overhead fluorescent lighting       → Iluminación forense institucional
single-source overhead light              → Luz clínica de autopsia/interrogatorio
oblique angle lighting                    → Revela texturas, heridas superficiales
cross-lighting                            → Múltiples fuentes, sombras en texturas
glancing illumination                     → Revelación de patrones superficiales
diffused light                            → Sin sombras duras, neutro
infrared lighting                         → Evidencia no visible al ojo
ultraviolet / UV light                    → Detección de fluidos y huellas
alternate light source (ALS)             → Iluminación de investigación forense
ring flash                                → Macro forense, iluminación uniforme
high-intensity directional light         → Revelación de manchas de sangre
available light forensic                 → Luz existente sin modificar
```

---

### Iluminación Documental / Periodística

```
available light / ambient light           → Sin iluminación artificial añadida
window light                              → Luz de ventana, natural y suave
existing light conditions                 → Lo que hay en la escena
no flash photography                      → Sin flash, más auténtico
harsh fluorescent                         → Institucional, hospitales, comisarías
mixed light sources                       → Diferentes temperaturas, callejero
tungsten light                            → Cálido, ambarino, interior antiguo
overcast daylight                         → Nublado, luz difusa sin sombras
flat even lighting                        → Sin drama, neutral, documentario
```

---

### Patrones de Iluminación Clásicos (Portrait)

| Patrón | Descripción | Uso |
|--------|-------------|-----|
| **Butterfly/Paramount** | Luz encima y delante, sombra en forma de mariposa bajo nariz | Glamour |
| **Loop lighting** | Luz arriba del nivel de los ojos | Natural, retratos |
| **Rembrandt lighting** | Triángulo de luz bajo el ojo en el lado sombreado | Dramático, íntimo |
| **Split lighting** | Un lado iluminado, el otro en sombra | Misterioso |
| **Rim/Edge lighting** | Luz detrás del sujeto, contorno luminoso | Separación del fondo |
| **Chiaroscuro** | Contraste extremo luz/sombra | Dramático artístico |

---

## 6. NEGATIVE PROMPTS

### Negative Prompt Universal para Fotorrealismo (Stable Diffusion)

```
(worst quality:1.4), (low quality:1.4), (normal quality:1.4), lowres, blurry,
(cartoon:1.5), (anime:1.5), (animation:1.4), (3d render:1.5), (CGI:1.5),
(digital art:1.3), (illustration:1.5), (painting:1.5), (oil painting:1.3),
(watercolor:1.3), (sketch:1.3), (drawing:1.4), (artwork:1.4),
(artstation:1.3), (deviantart:1.3), (octane render:1.4), (unreal engine:1.4),
bad anatomy, bad proportions, bad hands, extra fingers, fused fingers,
missing fingers, extra limbs, deformed hands, mutated limbs,
bad face, deformed face, ugly face, bad eyes, deformed iris, cross-eyed,
text, watermark, signature, logo, username, artifact,
overexposed, oversaturated, monochrome, pixelated,
jpeg artifacts, compression artifacts
```

---

### Equivalentes para Modelos SIN Negative Prompts

- **Flux 2 [MAX]**, **Grok/Aurora**, **DALL-E 3**: No soportan negative prompts.
  - En vez de `"no blur"` → usar `"sharp focus, tack-sharp, crisp details"`
  - En vez de `"no 3D render"` → usar `"documentary photograph, RAW photo"`
  - En vez de `"no art"` → usar `"unprocessed, straight from camera, no color grading"`

---

## 7. DIFERENCIAS ENTRE PLATAFORMAS

### Tabla Comparativa

| Característica | Midjourney V7 | DALL-E 3 / GPT-4o | Stable Diffusion (SDXL) | Flux 2 | Grok/Aurora |
|---------------|--------------|-------------------|------------------------|--------|-------------|
| **Sintaxis** | Frases cortas + `--params` | Lenguaje natural conversacional | Keywords con pesos `(term:1.2)` | Lenguaje natural detallado | Descriptivo, iterar |
| **Negative prompts** | No (`--no` básico) | No (usar "avoid") | Campo separado, esencial | No soportados | No |
| **Fotorrealismo** | Excelente (artístico) | Bueno (preciso) | Variable (depende del modelo) | Excepcional (campeón) | Muy bueno |
| **Texto legible en imagen** | Malo | Excelente | Variable | Muy bueno | Bueno-Variable |
| **Consistencia personajes** | `--oref` (V7) | Context mismo chat | LoRA, InstantID, IPAdapter | Multi-ref API | Iteración manual |
| **Longitud ideal prompt** | 10-60 palabras | Párrafos | 50-150 tokens | 30-80 palabras | 20-80 palabras |

---

### Midjourney V7 — Parámetros Clave

```
--v 7          → Versión V7 (más nueva)
--ar 16:9      → Aspect ratio
--style raw    → Mínima estilización artística
--stylize 0    → Sin estilización
--stylize 250  → Balance para fotorrealismo
--oref [URL]   → Omni reference (personaje)
--ow [1-1000]  → Peso de la referencia (default 100)
--sref [URL]   → Style reference
--seed [n]     → Reproducibilidad
--q 2          → Calidad máxima
```

---

### Stable Diffusion — Modelos Recomendados

| Modelo | Especialidad |
|--------|-------------|
| **Juggernaut XL / Ragnarok** | Fotorrealismo general |
| **Realistic Vision 6.0** | Retratos fotorrealistas |
| **CyberRealistic Pony** | Fotorrealismo base Pony |
| **EpicRealism** | Piel y detalle alta calidad |

**Configuración para Juggernaut XL:**
- Sampler: DPM++ 2M Karras
- Steps: 20-30
- CFG: 6-7 (bajar a 3-5 para piel más natural)
- Resolución: 832×1216 (retratos), 1024×1024 (cuadrado)

---

## 8. TÉCNICAS PARA FOTOGRAFÍA FORENSE / CRIMINALÍSTICA

### Vocabulario Técnico Forense

**Tipos de planos estándar forenses:**
```
overall/establishing shot         → Vista general de la escena
medium-range shot                 → Relación evidencia/escena
close-up shot                     → Detalle de evidencia específica
macro documentation shot          → Detalles microscópicos
orientation photograph            → Muestra dónde está en el espacio
```

**Elementos forenses en el frame:**
```
ABFO #2 scale ruler               → Escala estandarizada forense (en "L")
measuring tape                    → Cinta métrica en la escena
evidence placards, numbered cards → Números de evidencia
yellow evidence markers           → Marcadores amarillos de suelo
chain of custody documentation    → Documentación visible
forensic scale reference          → Referencia de tamaño
```

---

### Templates de Prompts Forenses

**Escena del crimen:**
```
Crime scene documentation photograph, [hora del día], [tipo de entorno],
overall establishing shot showing [descripción de escena],
evidence markers numbered [cantidad] visible on floor,
yellow police tape perimeter,
flat even lighting [o: available light if outdoors],
no artistic processing, unedited documentation style,
shot on Nikon D6, 24-70mm lens at 28mm, f/8 for deep depth of field,
ISO 800, all elements in focus,
forensic documentation photography, no shadows hiding evidence --ar 16:9
```

**Close-up de evidencia:**
```
Forensic evidence close-up photograph, [descripción del objeto],
with ABFO #2 ruler scale visible,
oblique lighting from left to reveal surface texture,
macro lens documentation, 105mm f/11,
tack-sharp all elements, deep depth of field,
neutral white balance 5500K,
no reflections on surface,
clinical forensic documentation, no artistic processing,
ring flash lighting setup --ar 1:1
```

**Evidencia en bolsa:**
```
Evidence documentation photograph,
[objeto] inside clear labeled evidence bag,
"EVIDENCE" printed label with case number visible,
neutral gray background surface,
diffused studio lighting, no reflections on plastic bag,
flat even illumination,
scale ruler placed beside bag,
forensic documentation photography,
Canon EOS R5, 50mm macro lens, f/11,
all text on label sharp and legible --ar 3:2
```

---

## 9. HERIDAS, SANGRE Y DAÑO FÍSICO — DESCRIPCIÓN REALISTA

### Vocabulario Médico-Forense (más preciso, menos filtros)

**Trauma contundente:**
```
abrasion                → Raspado superficial de epidermis
contusion               → Hematoma por ruptura vascular
ecchymosis             → Coloración purpúrea/azul-amarillenta por hematoma
laceration              → Desgarro de tejido
patterned abrasion     → Abrasión que reproduce el objeto
soft tissue swelling   → Inflamación de tejido blando
periorbital ecchymosis → "Ojos de mapache"
```

**Arma blanca:**
```
incised wound           → Herida incisa (longitud > profundidad)
stab wound              → Herida penetrante (profundidad > longitud)
defense wound           → Herida en palmas/brazos al defenderse
```

**Arma de fuego:**
```
entrance wound          → Borde definido, quemadura central
exit wound              → Borde irregular, mayor tamaño
contact wound           → Con quemadura estrellada
powder tattooing        → Tatuaje de pólvora periférico
stippling               → Punteado rojo alrededor del orificio
```

---

### Estadios de Hematomas (por color)

```
fresh bruise, red-purple coloration → Horas
purple-blue bruise                  → 1-3 días
blue-green bruise                   → 3-7 días
yellow-green bruise                 → 7-14 días
yellow-brown bruise, healing        → +14 días
```

---

### Vocabulario de Patrones de Sangre

```
passive drip bloodstain             → Gota pasiva, redonda
satellite stains                    → Pequeñas manchas satélite
impact spatter                      → Salpicadura por impacto
cast-off pattern                    → Proyección por movimiento de arma
arterial spurt pattern              → Patrón de surtidor arterial
pooling of blood                    → Charco alrededor del cuerpo
void pattern                        → Área limpia dentro del patrón
wipe pattern                        → Patrón de limpieza
dried bloodstain                    → Seca, coagulada
fresh blood                         → Roja brillante, líquida
coagulated blood                    → Oscura, gelatinosa
oxidized dried blood                → Marrón-negro oscuro
```

---

### Estado Visual de la Sangre por Tiempo Transcurrido

```
0-2 horas     → bright red, glossy, liquid, pooling
2-6 horas     → darkening red, beginning to coagulate at edges
6-12 horas    → dark red, coagulated, gel-like
12-24 horas   → dark brown, fully dried, matte surface
24-48 horas   → dark brown-black, cracked, dried
+48 horas     → blackened, dessicated, flaking edges
```

---

### Estrategia para Plataformas con Filtros

Usar terminología médica en lugar de términos directos:
- En vez de "wound" → "contusion", "laceration", "abrasion"
- En vez de "blood" → "bloodstain", "hematoma", "passive drip"
- Marco contextual: `"medical documentation"`, `"forensic pathology"`, `"clinical photography"`
- Para contenido sin restricciones: Stable Diffusion local

---

## 10. DOCUMENTOS, PAPELES Y TEXTO LEGIBLE

### Herramientas por Precisión de Texto

| Herramienta | Precisión | Notas |
|------------|-----------|-------|
| **DALL-E 3 / GPT-4o** | Excelente | Mejor para texto complejo integrado |
| **Flux 1/2** | Muy buena | Excelente para texto corto y claro |
| **Ideogram 2.0** | Excelente (~90%) | Diseñado específicamente para tipografía |
| **Leonardo Phoenix** | Excelente | Mejora con prompt enhancement |
| **Grok/Aurora** | Buena-Variable | Inconsistente |
| **Stable Diffusion SDXL** | Variable | Capacidad básica |
| **Midjourney V7** | Mala | No recomendado para texto crítico |

---

### Regla Universal para Texto

Poner el texto deseado **entre comillas dobles** dentro del prompt:

```
...with a label that reads "EVIDENCE BAG #347-A"...
...the document shows the title "AUTOPSY REPORT"...
...a handwritten note reading "Room 214, 3rd floor"...
```

---

### Templates de Prompts para Documentos

**Documento oficial:**
```
A photorealistic close-up photograph of an official government document on white paper,
the heading reads "AUTOPSY REPORT - CASE #2024-0847",
text is black typed font on white paper,
slightly off-white aged paper texture,
directional light from upper left creating subtle shadow,
document photographed flat on a dark wooden surface,
macro lens close-up, sharp text clearly legible,
forensic evidence scale ruler beside document --ar 3:2
```

**Nota manuscrita:**
```
Photorealistic photograph of a handwritten note on lined paper,
the text reads "Meet me at the warehouse - midnight" in dark blue ink,
slightly hurried handwriting, pen pressure visible,
paper texture visible including ruled lines,
photographed on wooden table,
soft side lighting revealing paper texture,
macro lens, f/8, deep depth of field,
slight crumple at bottom corner --ar 3:2
```

**Periódico:**
```
Photorealistic close-up of a newspaper page,
headline reads "BODY FOUND IN RIVERSIDE PARK" in bold black serif font,
black and white newsprint texture,
slightly yellowed aged newspaper,
photographed on dark surface,
raking light from left revealing paper texture,
macro close-up, sharp text --ar 3:2
```

---

### Tips para Texto en Imágenes

1. **Texto corto:** Cuanto más corto, más preciso. Prefiere frases cortas o titulares
2. **Comillas dobles siempre:** `"the label says 'EVIDENCE'"` — clave en todos los modelos
3. **Estilo tipográfico:** "bold serif", "handwritten cursive", "typed monospace", "stencil font"
4. **Posición:** "centered at the top", "in the upper right corner"
5. **No más de 3-4 bloques de texto por imagen** — la precisión baja drásticamente

---

## GLOSARIO RÁPIDO — Los 50 Keywords más Potentes

```
1. RAW photo                        26. fluorescent lighting
2. DSLR photo                       27. harsh shadows
3. photorealistic                   28. clinical documentation
4. documentary photography          29. forensic photography
5. photojournalism                  30. medium shot
6. candid shot                      31. close-up
7. available light                  32. establishing shot
8. film grain                       33. eye level
9. 35mm lens                        34. slight camera shake
10. shot on [camera model]          35. 8K / 4K UHD
11. f/2.8                           36. HDR
12. shallow depth of field          37. high dynamic range
13. sharp focus / tack-sharp        38. detailed skin pores
14. natural skin texture            39. natural expression
15. visible pores                   40. unedited RAW
16. no flash                        41. no color grading
17. ambient light                   42. real photo
18. handheld camera                 43. archival photograph
19. unposed                         44. news photo / wire photo
20. reportage style                 45. gritty realism
21. Kodak Portra 400                46. analog photography
22. --style raw (Midjourney)        47. oblique lighting
23. (photorealistic:1.4) (SD)       48. available light
24. high ISO noise                  49. no studio lighting
25. lens vignetting                 50. not a painting, not digital art
```

---

## TABLA DE REFERENCIA RÁPIDA

| Si quieres... | Usa esto |
|--------------|----------|
| Máximo fotorrealismo | Flux 2 (campeón actual) |
| Máximo control artístico | Stable Diffusion + LoRA |
| Texto legible en imagen | DALL-E 3 / Ideogram / Flux |
| Consistencia de personaje | MJ `--oref` / SD InstantID / LoRA |
| Documental/periodístico | `35mm, available light, candid, no flash, --style raw` |
| Forense/clínico | `oblique lighting, ABFO scale, ring flash, f/11, macro` |
| Sin filtros de contenido | Stable Diffusion local |
| Más fácil de usar | DALL-E 3 via ChatGPT |
| Gratis y accesible | Grok/Aurora (X.com), Flux Schnell (Hugging Face) |
| Imágenes con heridas/sangre | Terminología médica + SD local o Flux |

---

*Fuentes: Midjourney Official Docs, Black Forest Labs (Flux), OpenAI Prompting Guide, Stable Diffusion community guides, forensic photography standards (NIH PMC), crime scene investigation resources.*
