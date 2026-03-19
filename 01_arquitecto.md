# ETAPA 1 — Arquitecto del Caso

> **Usa este prompt primero.** Su único objetivo es diseñar la estructura lógica del caso antes de escribir una sola línea narrativa.
> El output de este prompt se pega completo al inicio del prompt de la Etapa 2 (Redactor).
> No genera nada que vea el jugador. Solo construye el esqueleto interno.

---

```
Actúa como un arquitecto de juegos de detectives. Tu único trabajo en este momento es diseñar la lógica interna del caso. NO vas a escribir narrativa, ni diálogos, ni el caso para el jugador. Solo vas a construir la estructura que garantiza que el caso sea lógicamente sólido antes de redactarlo.

Trabaja paso a paso en el orden exacto indicado. No saltes pasos. No combines pasos.

---

## PASO A: PENSAR ANTES DE DECIDIR

Antes de elegir al culpable, genera internamente 3 posibles soluciones distintas:
- Solución 1: [culpable, método, motivación]
- Solución 2: [culpable, método, motivación]
- Solución 3: [culpable, método, motivación]

Luego elige la que cumpla estas condiciones:
- Motivación menos obvia
- Más posibilidades de generar error óptimo convincente
- Más rica en contradicciones detectables entre testimonios

Escribe cuál elegiste y por qué descartaste las otras dos.

---

## PASO B: DEFINIR LA SOLUCIÓN INTERNA

Con la solución elegida, define con precisión:

**CULPABLE:**
- Nombre
- Qué hizo exactamente (acción concreta)
- Cómo lo hizo (método paso a paso)
- Por qué lo hizo (motivación real — debe ser profunda, no obvia, emergente de la historia)
- Qué evidencia física lo delata (pista clave)
- Qué sabe que nadie más sabe

**CRIMEN:**
- Tipo exacto (asesinato / robo / desaparición / fraude / otro)
- Cuándo ocurrió (fecha y hora exacta)
- Dónde ocurrió exactamente
- Qué dejó como rastro involuntario el culpable

---

## PASO B2: MAPA ESPACIAL DEL ESCENARIO DEL CRIMEN

> Este paso es OBLIGATORIO. Su output es la fuente de verdad para el Redactor (Etapa 2) y el Generador de Imágenes (Etapa 4). Ninguno de los dos puede contradecirlo.

### 1. Planta del lugar (diagrama ASCII)

Dibuja la planta del espacio físico donde ocurrió el crimen con orientación cardinal. Coloca todos los elementos en su posición real.

```
NORTE  ┌─────────────────────────────────────────┐
       │  [qué hay en la pared norte]            │
       │                                          │
OESTE  │  [elementos del lado oeste]             │ ESTE
       │                                          │
       │         [elementos del centro]           │
       │         CUERPO ← posición exacta         │
       │         EVIDENCIAS ← cada una            │
       │                                          │
SUR    └─────────────────────────────────────────┘
              [acceso / puerta / entrada]
```

Incluir obligatoriamente:
- Todos los accesos (puertas, ventanas, pasillos)
- Todos los muebles relevantes con nombre y posición
- Posición del cuerpo respecto a cada elemento
- Posición de cada evidencia física

### 2. Inventario de elementos con posición y distancia al cuerpo

| Elemento | Tipo | Zona/pared | Distancia al cuerpo | Visible desde la entrada |
|---------|------|-----------|---------------------|--------------------------|
| [nombre] | [mueble / acceso / ventana / evidencia] | [norte/sur/este/oeste/centro] | [X metros aprox.] | [sí/no] |

⚠️ REGLA CRÍTICA DE MUEBLES: Si el lugar tiene un escritorio de trabajo Y una mesa de lectura/reunión, o cualquier par de muebles del mismo tipo, son objetos distintos. Cada uno debe tener fila propia en esta tabla con posición y distancia al cuerpo por separado. Confundirlos en la redacción o en los prompts de imagen invalida la escena del crimen.

### 3. Tabla de perspectivas de imagen

Define exactamente qué debe verse desde cada ángulo de cámara. El Generador de Imágenes usará esta tabla como instrucción vinculante.

| Imagen | Posición cámara | Dirección mirada | Elemento al fondo | Elemento detrás de cámara (NO visible) |
|--------|----------------|-----------------|-------------------|----------------------------------------|
| Plano general | [posición] | [norte/sur/este/oeste] | [qué se ve al fondo] | [qué queda detrás] |
| Vista contextual | [posición 2] | [dirección 2] | [qué se ve al fondo] | [qué queda detrás] |
| Detalle | [posición macro] | [ángulo] | — | — |

⚠️ REGLA DE ÁNGULOS OPUESTOS: Si dos imágenes se toman desde posiciones contrarias del mismo espacio, sus fondos deben ser contrarios. Ejemplo: si desde la entrada se ve la ventana al fondo, desde la ventana se ve la entrada al fondo. Nunca dos imágenes desde posiciones opuestas pueden mostrar el mismo elemento al fondo.

### 4. Restricciones espaciales irrompibles

Lista las reglas que ningún relato narrativo ni prompt de imagen puede violar:

- [Ej: La ventana está en la pared norte. Es visible solo en imágenes tomadas mirando al norte. En imágenes mirando al sur, la ventana no existe en el encuadre.]
- [Ej: La mesa de impacto está a menos de 1 metro del cuerpo. Siempre aparece junto al cuerpo. Nunca al fondo ni lejos.]
- [Ej: La puerta de acceso está en la pared sur. Es visible solo en imágenes mirando al sur.]
- [Añadir las que correspondan al caso]

---

## PASO C: DEFINIR TODOS LOS PERSONAJES

Lista TODOS los personajes que aparecerán en el caso. Una vez definida esta lista, ningún testimonio puede mencionar a alguien que no esté aquí. No se permiten personajes nuevos en la redacción.

**VÍCTIMA:**
- Nombre completo, edad, ocupación
- Situación económica y personal
- Secreto relevante (mínimo 1 que afecte la trama)
- Quién ganó con su muerte/robo/desaparición
- Quién perdió algo con ella

**SOSPECHOSOS (mínimo 4):**
Para cada uno:
- Nombre, edad, ocupación
- Vínculo con la víctima
- Motivo percibido (lo que el jugador verá inicialmente — debe ser plausible pero no el real)
- Motivo real oculto (lo que realmente lo vincula al caso, incluso si es inocente — puede ser un secreto sin relación al crimen)
- ¿Es culpable o inocente?
- Si es inocente: ¿qué oculta y por qué?

Los motivos no pueden ser obvios ni declarados. Deben emerger de conectar datos. Ningún sospechoso puede tener un motivo que se entienda en una sola lectura.

**TESTIGOS (mínimo 5):**
Para cada uno:
- Nombre, vínculo con la víctima o el lugar
- Qué vio, oyó o sabe realmente
- Qué omite y por qué
- Si miente en algo: qué y por qué
- Qué información útil está escondida en su relato

---

## PASO D: MAPA DE CONTRADICCIONES

Antes de definir los testimonios, construye esta tabla para cada personaje:

| Personaje | Afirmación en su relato | Verdad real | Tipo de distorsión | Detectable cruzando con... |
|-----------|------------------------|-------------|-------------------|---------------------------|
| [nombre]  | [qué dice]             | [qué pasó]  | mentira activa / omisión / confusión / miedo | [otro personaje o evidencia] |

Completa la tabla para los 4 sospechosos y los 5 testigos.
Debe haber al menos:
- 3 mentiras activas (dicen algo falso intencionalmente)
- 3 omisiones deliberadas (callan algo importante)
- 2 confusiones reales (se equivocan sin mala intención — esto también puede despistar al jugador)

---

## PASO E: LÍNEA DE TIEMPO INTERNA

Define la secuencia real y completa de eventos (solo uso interno):

[HORA] — [Evento] — [Quién sabe esto] — [Quién lo menciona en su relato]

Cada evento debe estar cubierto por al menos un personaje en su relato.
Ningún personaje tiene el cuadro completo.
Al menos 3 eventos deben ser contradictorios entre dos personajes (uno de los dos miente o se equivoca).

---

## PASO F: RUTA DEDUCTIVA COMPLETA

Escribe la cadena lógica exacta que lleva al jugador desde las pistas hasta el culpable. Cada eslabón debe estar sustentado por evidencia o testimonio presente en el caso:

```
Paso 1: [Evidencia/Testimonio X] revela que [dato A]
Paso 2: [Dato A] contradice lo que [Sospechoso Y] dijo sobre [tema B]
Paso 3: Si [Sospechoso Y] mentía sobre [B], entonces [conclusión C]
Paso 4: [Evidencia Z] vincula [método del crimen] únicamente con [culpable]
Paso 5: Descarte de [Sospechoso N] porque [dato D] lo elimina
...
Conclusión: solo [culpable] satisface todos los pasos sin contradicción
```

Verifica que cada paso sea deducible. Si algún paso requiere asumir algo no dicho → vuelve y corrige la estructura.

---

## PASO G: INFORMACIÓN A DEDUCIR

Lista los 3 datos mínimos que el jugador debe inferir (no leer directamente):

1. [Relación o vínculo que no se declara explícitamente]
2. [Móvil que se construye conectando datos dispersos]
3. [Contradicción horaria o geográfica que desmiente una coartada]

Indica exactamente en qué parte del caso estará la evidencia para cada deducción.

---

## PASO H: ERROR ÓPTIMO

Define la teoría incorrecta más convincente:
- Sospechoso que se acusaría por error
- Qué evidencias del caso sostienen esa teoría incorrecta
- Por qué es refutable con lógica precisa
- Qué paso de la ruta deductiva desmonta esa teoría

---

## PASO I: VALIDACIÓN INTERNA

Responde sí o no a cada pregunta. Si alguna es NO → vuelve y corrige antes de continuar:

- ¿La solución tiene un único culpable posible? [sí/no]
- ¿Cada paso de la ruta deductiva está sustentado por evidencia o testimonio? [sí/no]
- ¿Toda la información necesaria está en el caso (aunque dispersa)? [sí/no]
- ¿Puedo descartar a cada sospechoso inocente con lógica? [sí/no]
- ¿El motivo del culpable requiere deducción (no es obvio)? [sí/no]
- ¿El mapa de contradicciones tiene al menos 3 mentiras activas y 3 omisiones? [sí/no]
- ¿Hay mínimo 4 sospechosos y 5 testigos definidos? [sí/no]
- ¿La lista de personajes está cerrada (no aparecerá nadie nuevo en la redacción)? [sí/no]
- ¿El error óptimo es convincente y refutable? [sí/no]
- ¿El mapa espacial (Paso B2) tiene diagrama ASCII con orientación cardinal? [sí/no]
- ¿La tabla de elementos distingue cada mueble/objeto con posición y distancia al cuerpo? [sí/no]
- ¿La tabla de perspectivas define qué aparece al fondo y qué NO desde cada ángulo de cámara? [sí/no]
- ¿Las restricciones espaciales irrompibles están listadas explícitamente? [sí/no]

Si alguna respuesta es NO → vuelve y completa el paso correspondiente antes de continuar.

---

Entrega el output completo de todos los pasos (A a I, incluyendo B2). Este output es el insumo para la Etapa 2.
```
