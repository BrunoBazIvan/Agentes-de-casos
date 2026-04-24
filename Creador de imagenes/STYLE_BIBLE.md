# STYLE BIBLE — DETECTIVES
### Guía visual oficial del proyecto · Versión 1.0

> Este documento define el ADN visual de todos los casos, videos e imágenes del proyecto.
> Nada se produce sin seguir estas reglas. La consistencia es lo que convierte contenido en marca.

---

## 1. FILOSOFÍA VISUAL

El universo de Detectives es un mundo cartoon donde el crimen es real pero los personajes son exagerados. La tensión viene del contraste: un estilo visualmente cómico que narra historias genuinamente oscuras. Los personajes se ven casi ridículos — hasta que recuerdas que uno de ellos mató a alguien.

**Referentes visuales:**
- Gravity Falls (proporciones, expresividad, misterio)
- Hotel Transylvania (caricatura con peso emocional)
- Scooby-Doo: Mystery Incorporated (tono adulto en envase cartoon)
- The Bad Guys (línea limpia, cel-shading contemporáneo)

---

## 2. PALETA DE COLORES OFICIAL

### Colores de marca (UI, textos, sellos, títulos)

| Nombre | Hex | RGB | Uso |
|--------|-----|-----|-----|
| Teal Profundo | `#0d2b38` | 13, 43, 56 | Fondos principales, headers |
| Teal Medio | `#1e6b7a` | 30, 107, 122 | Fondo signature de personajes |
| Rojo Misterio | `#8b1a1a` | 139, 26, 26 | Sellos, alertas, "CASO ABIERTO" |
| Rojo Acento | `#cc2200` | 204, 34, 0 | Subrayados, énfasis, ojos villanos |
| Beige Papel | `#d4b896` | 212, 184, 150 | Fondos de documentos, fichas |
| Negro Tinta | `#0a0a0a` | 10, 10, 10 | Outlines siempre. Nunca gris. |
| Blanco Humo | `#f2ede8` | 242, 237, 232 | Textos sobre oscuro, ojos |

### Colores de personajes (aplicados en Midjourney)

| Nombre | Hex | Uso en personaje |
|--------|-----|-----------------|
| Piel Base | `#c4956a` | Tono de piel principal |
| Piel Sombra | `#8b5e3c` | Cel-shading en zonas de sombra |
| Piel Luz | `#e8c99a` | Highlight en frente, nariz, pómulos |
| Ropa Neutro 1 | `#a05060` | Mauve/rosa apagado (como referencia) |
| Ropa Neutro 2 | `#4a6741` | Verde oliva apagado |
| Ropa Neutro 3 | `#2d4a6e` | Azul pizarra oscuro |
| Cabello Oscuro | `#1a1008` | Negro con matiz cálido |

### Regla de color
> Nunca usar colores saturados al 100%. Siempre levemente desaturados y con temperatura cálida.
> El único color que puede ser brillante es el **rojo acento** (#cc2200) — es el grito visual del universo.

---

## 3. ESTILO DE PERSONAJES

### Proporciones (lo que SIEMPRE se exagera)

```
CABEZA:    Grande. Ocupa 1/3 del encuadre en retrato.
CARA:      Muy alargada verticalmente. Mentón prominente o hundido.
NARIZ:     Exagerada — puntiaguda, bulbosa, o ganchuda según personalidad.
OJOS:      Grandes. Expresivos. Pupila pequeña = inquietante.
OREJAS:    Visibles y ligeramente grandes.
CUELLO:    Largo y delgado.
CUERPO:    Pequeño en relación a la cabeza (solo visible en plano medio).
```

### Lo que NO se exagera
- Las manos (cuando aparecen, son normales — el detalle que las hace reales)
- La ropa (apagada, realista — contrasta con la cara expresiva)

### Expresiones por rol

| Rol | Expresión base | Detalle de ojos |
|-----|---------------|-----------------|
| Sospechoso principal | Tensa, sudorosa, sobreactuada | Pupila pequeña, mirada lateral |
| Sospechoso secundario | Nerviosa, evita el contacto | Ojos muy abiertos o muy entrecerrados |
| Víctima (flashback) | Seria, desconfiada | Ojos cansados, profundos |
| Testigo inocente | Sorprendida, ansiosa | Cejas muy arriba |
| Testigo cómplice | Demasiado calmada | Sonrisa que no llega a los ojos |

### Línea y trazo

- **Outline:** Negro puro (#0a0a0a), grosor variable (más grueso en bordes exteriores, más fino en detalles internos)
- **Cel-shading:** Dos zonas — luz y sombra. Sin gradientes suaves. Transición limpia.
- **Highlights:** Un destello blanco en los ojos y en la nariz. Solo esos dos puntos.
- **Textura:** Ligera textura granulada de papel en el fondo. Nunca en el personaje.

---

## 4. ESTILO DE ESCENAS Y AMBIENTES

Las escenas siguen el mismo universo cartoon. Nunca fotorrealistas.

### Reglas de escenas

- **Outlines:** Igual que los personajes — línea negra gruesa en TODO: muebles, paredes, objetos, arquitectura. Sin esto, la escena no pertenece al mismo universo.
- **Cel-shading:** Áreas de color plano con transición dura entre luz y sombra. Nunca gradientes suaves ni textura pictórica.
- **Perspectiva:** Ligeramente exagerada. Composición vertical (2:3) que enfatiza la altura del espacio.
- **Iluminación:** Una sola fuente cálida (lámpara, ventana) contra sombras frías en teal. Cono de luz cel-shadeado.
- **Formato:** SIEMPRE 2:3 vertical — igual que los personajes. Nunca 16:9 para escenas de video.
- **Keywords a EVITAR en Midjourney:** `point-and-click adventure game aesthetic`, `brushstroke texture`, `painterly`, `concept art` — todos empujan hacia estilo realista incompatible.

### Paleta de escenas

Escenas de interiores oscuros (sala de archivos, despachos):
- Dominante: Teal profundo + marrones oscuros
- Contraste: Un objeto iluminado en cálido (lámpara, ventana)
- Sombras: Azul-gris frío

Escenas de exteriores (calle, aparcamiento):
- Dominante: Azul noche o gris urbano
- Contraste: Farolas en amarillo cálido
- Húmedo/lluvioso siempre que sea posible

---

## 5. TIPOGRAFÍA (para videos y fichas)

| Uso | Estilo | Alternativa gratuita |
|-----|--------|---------------------|
| Títulos de caso | Serif pesada, estilo expediente | Playfair Display Bold |
| Texto de fichas | Monospace, estilo máquina de escribir | Courier Prime |
| Texto de alerta (CASO ABIERTO) | Sans-serif uppercase comprimida | Oswald ExtraBold |
| Subtítulos en video | Sans-serif limpia, blanco con sombra | Inter Medium |

### Reglas de texto en video
- Nunca texto sobre imagen sin fondo semitransparente o sombra
- Color de texto: siempre blanco (#f2ede8) o rojo (#cc2200). Nunca amarillo.
- Tamaño mínimo en móvil: lo que quepa cómodamente en 5 palabras por línea

---

## 6. REGLAS DE CONSISTENCIA ENTRE CASOS

Cada caso nuevo respeta:

1. **El mismo fondo de personajes:** Teal degradado (#1e6b7a → #0d2b38), siempre.
2. **El mismo grosor de outline:** Nunca cambiar aunque el estilo del caso sea diferente.
3. **La misma paleta de piel:** Los colores de piel son constantes. Lo que cambia es la forma de la cara.
4. **Los sellos en rojo misterio:** CASO ABIERTO, CONFIDENCIAL, EVIDENCIA — siempre en #8b1a1a.
5. **Nunca mezclar estilos:** Si un caso es cartoon, todo el caso es cartoon. No hay imágenes realistas intercaladas.

---

## 7. LO QUE SÍ Y LO QUE NO

| SÍ | NO |
|----|-----|
| Ojos grandes y expresivos | Ojos realistas o fotográficos |
| Sombras cel-shadeadas duras | Gradientes suaves tipo pintura digital |
| Fondo teal degradado | Fondos blancos o de color plano |
| Outline negro grueso | Personajes sin outline |
| Expresiones exageradas | Caras neutras o hiperrealistas |
| Ropa apagada y desaturada | Ropa brillante o llamativa |
| Un punto de luz en los ojos | Múltiples highlights en la cara |
| Textura granulada en el fondo | Fondos completamente lisos |
