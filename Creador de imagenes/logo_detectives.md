# LOGO — DETECTIVES
### Prompts Midjourney v6.1 para el isologo del proyecto
### Versión 2.0 — Concepto: Sello de cera con ojo

---

## CONCEPTO

**Símbolo:** Sello de cera rojo con un ojo grabado en relieve.

**Por qué funciona:**
- El sello de cera evoca directamente documentos sellados, secretos, lo confidencial — perfecto para el formato expediente
- El ojo es el símbolo más potente de misterio: vigilancia, omnisciencia, "alguien lo vio todo"
- El rojo (#8b1a1a) ya está definido en el STYLE BIBLE como "Rojo Misterio" — el color de sellos, alertas y el grito visual del universo
- Sin texto, funciona como marca universal a cualquier tamaño

**Por qué no texto en los prompts:**
Midjourney v6.1 renderiza texto de forma pobre. El texto se añade en post (Canva/Figma) con las fuentes del STYLE BIBLE.

---

## VARIANTE A — SELLO LIMPIO (recomendada para empezar)

El sello solo, con el ojo en el centro. La versión más directa y legible.

**Uso:** Favicon, avatar, watermark sobre imágenes de casos.

```
cartoon wax seal logo mark, circular deep crimson red wax seal in color #8b1a1a, slightly irregular organic outer edges as a real pressed wax seal, the wax surface has cel-shaded volume with a hard two-tone shadow area covering the bottom-left third of the seal in darker deep crimson #5c1010, a single small warm white specular glint at the upper-right of the seal surface, pressed into the center of the wax: a stylized cartoon eye engraved as a debossed relief into the wax, the engraved eye has an almond outer shape, a circular iris with a bold round pupil at center, the engraving lines appear in darker deep crimson as if stamped into the wax surface, the eye has a slightly unsettling all-seeing quality, the pupil is a solid dark circle, bold black ink outlines #0a0a0a on the outer silhouette of the entire wax seal with variable stroke weight heavier on outer edge lighter on the engraved interior details, isolated centered composition on deep teal background #0d2b38, subtle paper grain texture in background, no text no words no letters no numbers, Gravity Falls graphic design style, Hotel Transylvania aesthetic, same cel-shaded cartoon universe as all project visuals, flat bold graphic logo mark, reads clearly at thumbnail size --ar 1:1 --style raw --v 6.1
```

**Negative:** `photorealism, smooth gradients, painterly brushstrokes, realistic wax texture, white background, text, letters, words, multiple seals, wax drips, melting wax, realistic eye, photograph, anime`

---

## VARIANTE B — SELLO CON RAYOS

El sello con líneas radiales grabadas alrededor del ojo, como un sol oscuro o un ojo que irradia. Más elaborado, más impacto visual.

**Uso:** Portada del expediente PDF, cabecera del sitio web.

```
cartoon wax seal logo mark, circular deep crimson red wax seal in color #8b1a1a, slightly irregular organic outer edges as a real pressed wax seal, bold outer border ring with thick black ink outline, the wax surface has cel-shaded volume with a hard two-tone shadow in darker deep crimson #5c1010 at bottom-left, single warm white specular glint at upper-right, pressed into the center of the wax: a stylized cartoon eye engraved as debossed relief at the center, almond eye shape with circular iris and bold solid round pupil, surrounding the eye at equal intervals: eight short bold straight lines radiating outward from the eye like dark rays stamped into the wax, the eye and rays form a single unified sun-eye symbol, all engraving lines appear in darker deep crimson as if pressed into the wax, bold black ink outlines #0a0a0a on the outer silhouette of the seal with heavier stroke on outer edge lighter on interior engravings, isolated centered on deep teal background #0d2b38, subtle paper grain texture in background, no text no words no letters, Gravity Falls graphic design style, same cel-shaded cartoon universe as project visuals, flat bold graphic emblem, high contrast, reads at small size --ar 1:1 --style raw --v 6.1
```

**Negative:** `photorealism, smooth gradients, painterly, realistic wax texture, white background, text, letters, words, melting wax drips, realistic eye, anime, multiple seals, complex pattern`

---

## FLUJO POST-MIDJOURNEY

```
PASO 1: Generar ambas variantes en Midjourney → comparar
        ↓ Upscale la mejor versión (U1-U4)

PASO 2: Exportar a Canva / Figma
        ↓ Colocar el sello generado como elemento base

PASO 3: Añadir tipografía si se quiere un lockup completo (STYLE BIBLE)
        ├── "DETECTIVES" — Playfair Display Bold, cream #f2ede8
        ├── Línea separadora — rojo #8b1a1a, 2px
        └── "CASOS DE MISTERIO" — Oswald ExtraBold uppercase, rojo #8b1a1a

PASO 4: Generar variantes del logo completo
        ├── Cuadrado: sello solo (avatar / favicon / watermark)
        ├── Horizontal: sello + wordmark lado a lado (header web)
        └── Vertical: sello + texto apilado (portadas de caso)

PASO 5: Exportar
        ├── PNG transparente — para superposición en documentos e imágenes
        └── PNG sobre teal #0d2b38 — para uso directo en redes
```

---

## TIPS DE GENERACIÓN

- Empezar con la Variante A — menos elementos, más margen de acierto en Midjourney
- Si el ojo no queda centrado o bien proporcioned, añadir `--chaos 5` para más variedad
- Para reproducir el resultado exacto guardar el seed: `/imagine ... --seed [número del resultado]`
- El sello puede usarse directamente sobre imágenes del caso como watermark rojo semitransparente
