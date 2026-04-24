# Generar Imágenes — Orquestador Etapa 5

**Uso:** `/generar-imagenes {slug}` (ej: `/generar-imagenes codex`)

El argumento es el slug del caso: $ARGUMENTS

---

## Instrucciones de ejecución

Sigue estos pasos en orden. No los omitas ni combines.

### Paso 0 — Validación

1. El slug es: **$ARGUMENTS**

2. Verifica que existan los archivos de entrada:
   - `casos/{slug}/caso_final.md` (narrativa aprobada)
   - Arquitectura de la última iteración aprobada: busca el `arquitectura.md` del `iter_NN/` con número más alto dentro de `casos/{slug}/`.

   Si falta `caso_final.md` → informa: "⚠️ No existe `casos/{slug}/caso_final.md`. Ejecuta `/crear-caso` o `/corregir-caso` antes de generar imágenes." — TERMINAR.

   Si existe `caso_final.md` pero no hay ningún `iter_NN/arquitectura.md` → informa: "⚠️ No se encontró la arquitectura del caso. El generador necesita el mapa espacial (PASO B2)." — TERMINAR.

3. Crea el directorio de salida si no existe:
   ```bash
   mkdir -p casos/{slug}/imagenes
   ```

4. Lee el archivo `05_generador_imagenes.md` y extrae el bloque de código (entre las primeras ``` y las últimas ```) — ese es el system prompt del agente.

---

### Paso 1 — Ejecutar el agente visual

Usa el Agent tool (subagent_type: general-purpose) con:

- **System prompt:** contenido extraído de `05_generador_imagenes.md`
- **User message:**
  ```
  SLUG: {slug}

  ARQUITECTURA DEL CASO:
  {contenido completo de iter_NN/arquitectura.md — la última iteración aprobada}

  NARRATIVA FINAL DEL CASO:
  {contenido completo de caso_final.md}
  ```

⚠️ El agente DEBE usar la herramienta Write para crear los tres archivos. No le pidas los prompts en el chat — solo el resumen final.

---

### Paso 2 — Verificación de salida

Al terminar el agente, comprueba que existan los tres archivos:

- `casos/{slug}/imagenes/personajes.md`
- `casos/{slug}/imagenes/escenas.md`
- `casos/{slug}/imagenes/evidencias.md`

Si falta alguno → informa al usuario con el resumen que devolvió el agente y el archivo faltante. No reintentes automáticamente.

---

### Paso 3 — Reporte al usuario

Informa:

```
✅ Prompts de imagen generados para el caso: {slug}

Archivos creados:
- casos/{slug}/imagenes/personajes.md  ({N} prompts)
- casos/{slug}/imagenes/escenas.md     ({N} prompts)
- casos/{slug}/imagenes/evidencias.md  ({N} prompts)

Próximo paso: copiar cada prompt a Midjourney v6.1.
```

Los conteos de prompts los lees contando las secciones `####` en cada archivo generado.

---

### Estructura esperada

```
casos/{slug}/
├── caso_final.md
├── iter_NN/
│   ├── arquitectura.md
│   ├── narrativa.md
│   ├── jugador.md
│   └── evaluacion.md
└── imagenes/              ← creado por este comando
    ├── personajes.md
    ├── escenas.md
    └── evidencias.md
```
