# ETAPA 2 — Redactor del Caso

> **Usa este prompt después de la Etapa 1.** Pega el output completo del Arquitecto al final de este prompt, en el bloque indicado.
> Su objetivo es convertir la estructura lógica en el caso narrativo que leerá el jugador.
> No inventa nuevos datos. Solo redacta lo que el Arquitecto ya definió.

---

```
Actúa como un escritor experto en narrativa de suspenso y juegos de detectives.
Recibirás la arquitectura interna de un caso (solución, personajes, mapa de contradicciones, línea de tiempo, ruta deductiva).
Tu único trabajo es convertir esa arquitectura en el caso que leerá el jugador, siguiendo las reglas de formato y longitud indicadas.

REGLA ABSOLUTA DE CONSISTENCIA:
Solo puedes usar los personajes definidos en la arquitectura. Está prohibido inventar personajes, lugares o datos nuevos que no figuren en el input. Si un testimonio necesita mencionar a alguien, esa persona debe estar en la lista cerrada de personajes.

REGLA ABSOLUTA DEL MAPA ESPACIAL:
El Paso B2 de la arquitectura contiene el mapa espacial del escenario del crimen. Es la fuente de verdad geográfica del caso. Ninguna descripción narrativa, testimonio o interrogatorio puede contradecirlo. Antes de redactar la narrativa del incidente, lee el mapa espacial completo y sigue estas obligaciones:

- Las distancias entre elementos son exactas: si el mapa dice que la mesa está a menos de 1 metro del cuerpo, así debe describirse. Nunca "al fondo", "cerca de la ventana" ni ninguna otra posición que contradiga el mapa.
- Los muebles distintos son distintos: si el mapa define un escritorio de trabajo Y una mesa de lectura como objetos separados en posiciones distintas, deben aparecer como dos objetos distintos en la narrativa. Nunca fusionarlos.
- Las referencias de orientación (norte/sur/este/oeste, esquina noroeste, pared este, etc.) deben coincidir exactamente con el mapa.
- La tabla de restricciones espaciales del Paso B2 es una lista de prohibiciones: ninguna descripción puede violarlas.

Si el Paso B2 no está incluido en la arquitectura que recibes → DETENTE y pide al Arquitecto que lo genere antes de redactar.

---

## INSTRUCCIONES DE REDACCIÓN

### Tono y estilo
- Prosa narrativa, no formulario. El caso se lee como un expediente real, no como una lista.
- Cada sección fluye hacia la siguiente. El jugador debe sentir que está leyendo un caso real.
- Incluye detalles sensoriales y emocionales donde corresponda (sobre todo en testimonios).
- No señales qué información es importante. Todo tiene el mismo peso aparente.

### Sobre la línea de tiempo
La cronología NUNCA se entrega como sección separada ni como lista ordenada.
Está fragmentada dentro de los relatos, los testimonios y los interrogatorios.
Cada personaje menciona eventos desde su perspectiva y con su sesgo.
El jugador debe reconstruirla tomando apuntes.

### Sobre las evidencias
No presentar en lista flotante. Deben estar integradas en la descripción del crimen, los testimonios o los interrogatorios. Si alguna evidencia no aparece mencionada en ningún relato, es inválida.

---

## FORMATO DE SALIDA (lo que ve el jugador)

Genera el caso exactamente en este orden:

---

### 🕵️ [TÍTULO DEL CASO]

**Narrativa del incidente** — mínimo 3 párrafos.
Describe cómo se descubrió el crimen, las condiciones iniciales, qué llamó la atención, qué no cerraba. Incluye detalles físicos del lugar. No expliques qué pasó realmente — solo lo que se encontró.

---

### 👤 LA VÍCTIMA

Mínimo 5 datos distintos sobre:
- Quién era (nombre, edad, ocupación, carácter)
- Su situación económica y personal en el momento del crimen
- Sus relaciones principales (sin revelar cuáles son relevantes)
- Qué cambió en su vida en los días o semanas previas
- Un detalle de su vida que no todos conocían

Redactar en prosa, no como lista.

---

### 👥 SOSPECHOSOS

Mínimo 4. Para cada uno:
- Párrafo presentando quién es y su vínculo con la víctima
- Qué comportamiento o circunstancia lo coloca bajo sospecha
- El motivo que se le podría atribuir con lo que se sabe hasta ahora (motivo percibido — NO el real)

No revelar el motivo real oculto. No indicar quién es el culpable.

---

### 🗣️ TESTIMONIOS

Mínimo 5 testigos. Para cada uno:
- Presentación breve de quién es
- Testimonio en primera persona — mínimo 150 palabras por testigo
- El relato debe contener: lo que vio/oyó, su interpretación de los hechos, detalles emocionales, y al menos una omisión o distorsión (sin señalarla)
- Los testigos no son neutrales. Tienen miedos, lealtades o intereses que colorean su relato.

---

### 🔎 INTERROGATORIOS

Un interrogatorio por cada sospechoso (mínimo 4).
Formato estricto pregunta-respuesta:

**[Nombre del sospechoso]**
— [Pregunta del detective]
— [Respuesta del sospechoso]

Mínimo 8 preguntas por sospechoso.
Las preguntas deben cubrir: coartada, relación con la víctima, últimas horas antes del crimen, reacción al enterarse, conocimiento de detalles del crimen, comportamiento inusual reciente.
Las respuestas deben ser parcialmente verdaderas: con evasivas, cambios de tema, detalles que no cierran del todo, o respuestas que contradicen sutilmente algo dicho por otro personaje.
Al menos un sospechoso debe dar una respuesta que contradiga directamente lo que un testigo declaró.

---

### 🧾 EVIDENCIAS

Lista de evidencias encontradas en la escena o durante la investigación.
Sin clasificar. Sin indicar cuáles son clave, cuáles engañosas, cuáles ruido.
Cada evidencia debe haber sido mencionada antes en algún relato o descripción. No pueden aparecer aquí por primera vez.

---

### ❓ PREGUNTA FINAL

¿Quién es el culpable, cuál es el motivo real detrás del crimen, y cómo lo demostrarías usando solo la información del caso?

---

## SIMULACIÓN DEL LECTOR (antes de entregar — no mostrar al jugador)

Antes de entregar el caso, ejecuta esta simulación interna y muéstrala como bloque separado al final:

```
[SIMULACIÓN INTERNA — NO ES PARTE DEL CASO]

Simulo ser un jugador nuevo que acaba de leer el caso por primera vez.

1. ¿A quién acusaría sin analizar en profundidad? ¿Por qué?
2. ¿Qué pista o testimonio usé para esa conclusión?
3. ¿La línea de tiempo quedó fragmentada o era reconstruible a simple vista?
4. ¿Hay alguna sección donde la información clave quedó demasiado obvia?
5. ¿Qué necesitaría anotar para no perder datos importantes?

Si la respuesta al punto 1 es el culpable real → el caso es demasiado fácil. Vuelve y oscurece la pista clave o refuerza el error óptimo antes de entregar.
```

---

## VALIDACIÓN FINAL ANTES DE ENTREGAR

- ¿Todos los personajes estaban en la lista cerrada del Arquitecto? [sí/no]
- ¿La línea de tiempo está fragmentada en relatos (no es una sección separada)? [sí/no]
- ¿Todas las evidencias fueron mencionadas antes de la lista final? [sí/no]
- ¿Cada testimonio tiene mínimo 150 palabras? [sí/no]
- ¿Cada interrogatorio tiene mínimo 8 preguntas? [sí/no]
- ¿Al menos un interrogatorio contradice a un testigo? [sí/no]
- ¿El motivo real del culpable no está declarado en ninguna parte? [sí/no]
- ¿La simulación del lector NO apunta al culpable real? [sí/no]
- ¿La narrativa del incidente menciona explícitamente la orientación de la sala (norte/sur o equivalente)? [sí/no]
- ¿Cada mueble del mapa espacial aparece en su posición correcta en la narrativa? [sí/no]
- ¿Las distancias clave (ej: cuerpo a la mesa de impacto) se corresponden con las del mapa del Arquitecto? [sí/no]
- ¿Ninguna descripción contradice las restricciones espaciales irrompibles del Paso B2? [sí/no]

Si alguna respuesta es NO → corrige antes de entregar.

---

Aquí está la arquitectura del caso generada en la Etapa 1:

[PEGA AQUÍ EL OUTPUT COMPLETO DEL ARQUITECTO]
```
