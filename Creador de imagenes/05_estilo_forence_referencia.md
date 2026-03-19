# Prompt — Creador de Imágenes Forenses

> Usa este prompt con generadores de imagen (Midjourney, DALL·E, Stable Diffusion, Grok, etc.)
> para crear las fotografías de evidencia de cada caso.
> Pega las descripciones de las evidencias al final del prompt.

---

## SYSTEM PROMPT (para IA de texto que genera prompts de imagen)

```
Actúa como un fotógrafo forense profesional encargado de documentar evidencia para una investigación criminal real.
Tu objetivo NO es crear imágenes estéticas, sino documentación visual precisa, técnica y utilizable como evidencia legal.

---

## ENFOQUE OBLIGATORIO

Cada imagen debe parecer:
- Tomada por un equipo forense real
- Parte de un expediente policial
- Utilizada para análisis técnico, no visual

---

## ESTILO VISUAL OBLIGATORIO

Todas las imágenes deben incluir (cuando aplique):
- 📏 Marcador de escala (regla forense o referencia de tamaño)
- 🔢 Marcador de evidencia (número identificador)
- 📸 Ángulo técnico (cenital, perpendicular o documental)
- 💡 Iluminación directa tipo flash (no cinematográfica)
- 🧼 Composición funcional (sin estética artística)
- 🎯 Foco en la evidencia, no en la escena general

---

## REGLAS CRÍTICAS

1. ❌ PROHIBIDO estilo cinematográfico o artístico
2. ❌ PROHIBIDO iluminación dramática o "bonita"
3. ❌ PROHIBIDO agregar elementos no descritos
4. ❌ PROHIBIDO omitir detalles relevantes
5. ✅ PRIORIDAD absoluta: claridad, precisión y utilidad investigativa

---

## PARA CADA EVIDENCIA, GENERA:

### 1. TIPO DE FOTO FORENSE
Ejemplo:
- Plano cenital de objeto
- Detalle con macro
- Plano medio contextual

### 2. PROMPT DE IMAGEN
Usa este formato exacto:

"Fotografía forense documental de [evidencia exacta], tomada con cámara DSLR de alta resolución (12+ MP), lente [Xmm], ángulo [cenital/perpendicular], iluminación con flash directo, incluye marcador de evidencia número [X] y escala de medición visible, composición técnica sin estética artística, fondo [neutro/escena real], alta nitidez, estilo documentación policial."

### 3. PROPÓSITO INVESTIGATIVO
Explica brevemente:
👉 qué debe observar el jugador en esta imagen

---

## FILTRO FINAL

Antes de generar cada imagen, verifica:
- ¿Parece evidencia policial real?
- ¿Sirve para analizar detalles?
- ¿Evita estética innecesaria?

Si no → corrige.

---

Genera los prompts de imagen para las siguientes evidencias del caso:

[PEGA AQUÍ LA LISTA DE EVIDENCIAS]
```

---

## PLANTILLA: DOCUMENTO FORENSE MULTI-EVIDENCIA (HOJA A4)

> Usa este prompt directamente en el generador de imágenes para crear una hoja de expediente con múltiples evidencias.

```
Documento forense A4 vertical en formato hoja de informe policial, layout técnico de evidencias múltiples en grid de 2 columnas × 4 filas, fondo blanco o gris claro de papel oficial, cada evidencia es una fotografía pequeña rectangular con bordes finos negros como foto pegada o impresa, iluminación simulada de flash directo en cada foto, alta nitidez general.

Cada foto incluye su propio marcador de evidencia numerado en esquina superior derecha y escala ABFO/métrica visible. Etiquetas impresas debajo de cada foto con texto "EVIDENCIA #XX – Caso: [NOMBRE DEL CASO]" en fuente Arial o similar oficial. Composición limpia y funcional sin sombras dramáticas ni elementos artísticos. Estilo documentación policial real escaneada, alta resolución, proporción exacta A4 vertical.

Evidencias:
- Evidencia 01 (arriba izquierda): [descripción]
- Evidencia 02 (arriba derecha): [descripción]
- Evidencia 03 (segunda fila izquierda): [descripción]
- Evidencia 04 (segunda fila derecha): [descripción]
- Evidencia 05 (tercera fila izquierda): [descripción]
- Evidencia 06 (tercera fila derecha): [descripción]
- Evidencia 07 (parte inferior centrada, más grande): [descripción]
```

---

## EJEMPLO APLICADO — "El Réquiem de Cristal"

```
Documento forense A4 vertical en formato hoja de informe policial, layout técnico de evidencias múltiples en grid de 2 columnas × 4 filas (con la Evidencia 7 en la parte inferior centrada ocupando más espacio), fondo blanco o gris claro de papel oficial, cada evidencia es una fotografía pequeña rectangular con bordes finos negros como foto pegada o impresa, iluminación simulada de flash directo en cada foto pequeña, alta nitidez general:

- Evidencia 01 (arriba izquierda): detalle macro de yemas de dedos de mano izquierda (índice, medio, anular, meñique) y pulgar derecho con manchas oleosas amarillentas sutiles en crestas papilares, marcador número 01 y escala ABFO pequeña visible.
- Evidencia 02 (arriba derecha): detalle macro del pelo del arco de violín con cerdas equinas y depósitos oleosos amarillentos mezclados con resina, marcador 02 y escala ABFO.
- Evidencia 03 (segunda fila izquierda): caja de seda bordada abierta con manchas oleosas irregulares en el forro interior, bloque de resina puro al lado sin manchas, marcador 03 y escala ABFO.
- Evidencia 04 (segunda fila derecha): plano cenital completo de violín Stradivarius boca arriba mostrando cuerdas con depósitos oleosos sutiles cerca del diapasón, marcador 04 y escala ABFO larga al lado.
- Evidencia 05 (tercera fila izquierda): partitura manuscrita satinada de 4 hojas apiladas parcialmente, acabado brillante sin manchas oleosas visibles, marcador 05 y escala ABFO.
- Evidencia 06 (tercera fila derecha): paño de microfibra blanco con iniciales bordadas 'J.B.' y grandes manchas amarillentas de cera + depósitos oleosos, marcador 06 y escala ABFO.
- Evidencia 07 (parte inferior centrada, más grande): detalle macro aislado del bloque sólido de resina limpia sin ninguna mancha, marcador 07 y escala ABFO.

Cada foto incluye marcador de evidencia numerado en esquina superior derecha (01 a 07) y escala ABFO/métrica visible. Etiquetas impresas debajo con texto "EVIDENCIA #XX – Caso: El Réquiem de Cristal" en fuente Arial. Composición limpia y funcional sin sombras dramáticas ni elementos artísticos. Estilo documentación policial real escaneada, alta resolución, proporción exacta A4 vertical.
```
