# ETAPA 2.5 — Jugador Independiente

> **Usa este prompt después de la Etapa 2.** Pega únicamente el caso narrativo final (output del Redactor) al final de este prompt.
> Su objetivo es intentar resolver el caso genuinamente, como si fuera un jugador real.
> NO recibe la arquitectura interna. NO sabe quién es el culpable. Solo ve lo mismo que verá el jugador.

---

```
Actúa como un jugador inteligente que acaba de recibir un caso de detective para resolver. No tienes información previa sobre el caso — solo lo que está en el texto que vas a leer.

Tu objetivo es intentar resolverlo con honestidad intelectual. No asumas nada que no esté escrito. No busques la respuesta "correcta" — busca la respuesta más coherente con la evidencia disponible.

---

## INSTRUCCIONES DE ANÁLISIS

Trabaja en este orden exacto. No saltes pasos.

### PASO 1: PRIMERA LECTURA

Lee el caso completo de corrido, como cualquier jugador. No tomes notas todavía.

Al terminar, sin releer, responde:
- ¿A quién sospecharías ahora mismo, instintivamente?
- ¿Por qué? (una sola razón, la más fuerte)

Esta es tu hipótesis 0. Puede estar equivocada — es solo el punto de partida.

---

### PASO 2: MAPA DE PERSONAJES

Construye una tabla con todos los personajes del caso:

| Nombre | Rol | Vínculo con la víctima | Motivo aparente | ¿Tiene coartada? | Comportamiento sospechoso |
|--------|-----|----------------------|----------------|-----------------|--------------------------|
| [nombre] | [sospechoso/testigo] | [relación] | [lo que se puede inferir] | [sí/no/parcial] | [qué llama la atención] |

---

### PASO 3: MAPA DE EVIDENCIAS

Lista todas las evidencias mencionadas en el caso:

| Evidencia | Dónde aparece (sección) | A quién vincula o podría vincular | ¿Cómo se interpreta? |
|-----------|------------------------|----------------------------------|----------------------|
| [evidencia] | [testimonios/interrogatorio/narrativa] | [personaje] | [qué dice sobre el crimen] |

---

### PASO 4: LÍNEA DE TIEMPO RECONSTRUIDA

Intenta reconstruir la secuencia de eventos a partir de lo que dicen los distintos personajes.

Formato:
```
[hora aproximada] — [evento] — [fuente: quién lo dice o cómo se sabe]
⚠️ CONTRADICCIÓN: [si dos fuentes dicen cosas distintas sobre este evento]
```

Identifica al menos 2 contradicciones entre personajes distintos. Si no encontrás ninguna, indica "No encontré contradicciones detectables" — eso es información relevante sobre la dificultad del caso.

---

### PASO 5: DESCARTE DE SOSPECHOSOS

Para cada sospechoso, evalúa si puede descartarse y por qué:

| Sospechoso | ¿Se puede descartar? | Razón (evidencia o argumento concreto) |
|------------|---------------------|----------------------------------------|
| [nombre] | sí/no/parcialmente | [qué dato lo elimina o lo mantiene en juego] |

---

### PASO 6: CONSTRUCCIÓN DE HIPÓTESIS

Con todo lo anterior, construye tus 2 mejores hipótesis:

**HIPÓTESIS A (la más fuerte):**
- Culpable propuesto
- Método
- Motivación (inferida de los datos, no declarada)
- Evidencias que la sostienen
- Testimonios que la respaldan
- ¿Algún dato contradice esta hipótesis?

**HIPÓTESIS B (la segunda más creíble):**
- Culpable propuesto
- Por qué es plausible
- Por qué es menos sólida que la A

---

### PASO 7: VEREDICTO DE DIFICULTAD

Evalúa honestamente la dificultad del caso:

- ¿Cuántas veces necesitaste releer para construir tu hipótesis A?
- ¿La pista clave estaba demasiado expuesta o bien disimulada?
- ¿El caso generó dudas reales o la respuesta se imponía desde el inicio?
- ¿Tu hipótesis 0 (primera instintiva) era la correcta? ¿O cambió al analizar?

Clasifica el caso en una de estas categorías:

- 🟢 **FÁCIL** — La hipótesis 0 era correcta y no cambió con el análisis. El culpable era obvio desde una lectura superficial.
- 🟡 **CALIBRADO** — La hipótesis 0 era incorrecta o incompleta. Fue necesario analizar y cruzar fuentes para llegar al culpable. El debate entre jugadores sería genuino.
- 🔴 **DIFÍCIL** — Ninguna hipótesis se impone claramente. Se puede construir un argumento coherente para al menos 2 sospechosos distintos con peso similar. Requiere análisis profundo.
- ⚫ **IRRESOLUBLE** — No hay suficiente información para llegar a una conclusión defendible. La solución no puede deducirse con lo disponible.

---

### PASO 8: REPORTE FINAL

Entrega el reporte en este formato exacto (los comandos de orquestación lo leerán para decidir el routing):

```
[REPORTE DEL JUGADOR]

VEREDICTO: [FÁCIL / CALIBRADO / DIFÍCIL / IRRESOLUBLE]

HIPÓTESIS PRINCIPAL: [nombre del sospechoso acusado]
CONFIANZA: [alta / media / baja]

RESUMEN:
[2-3 oraciones explicando por qué llegaste a esa conclusión y qué tan seguro estás]

PISTAS MÁS VISIBLES (las que se ven de inmediato):
- [pista 1]
- [pista 2]

PISTAS QUE PASÉ POR ALTO EN LA PRIMERA LECTURA:
- [pista 1 o "ninguna"]

CONTRADICCIONES DETECTADAS:
- [contradicción entre personaje X y personaje Y sobre evento Z]

SI EL VEREDICTO ES FÁCIL — indicar exactamente qué sección o pista lo delata demasiado:
[sección específica o "N/A"]

SI EL VEREDICTO ES IRRESOLUBLE — indicar qué información faltó para poder concluir:
[qué dato necesitaría para resolverlo o "N/A"]
```

---

Aquí está el caso a resolver:

[PEGA AQUÍ EL CASO COMPLETO — SOLO LA NARRATIVA, SIN LA ARQUITECTURA INTERNA]
```
