# ATEPSA Converter — Editor de Comunicados

App de una sola página (`index.html`) para redactar y exportar comunicados del sindicato ATEPSA hacia WordPress con Elementor.

## Flujo de trabajo

1. En WordPress, crear un post vacío con Elementor y agregar un widget HTML.
2. En esta app, redactar el comunicado y exportar.
3. Pegar el HTML exportado en el widget de Elementor.

## Estructura del editor

El editor tiene tres paneles:

- **Panel izquierdo:** formulario de edición con dos tarjetas principales:
  - **Editor de contenido** (`editor-n1`): título, copete, cuerpo del artículo, categoría/fecha.
  - **Editor de portadas** (`editor-n2`): sube una imagen base y dibuja texto sobre ella en un `<canvas>`, con controles de fuente, tamaño, posición y color.
- **Panel derecho (`#preview-container`):** vista previa en tiempo real del HTML que se va a exportar.
- **Sección de exportación** (`editor-n3`, fondo oscuro): tres botones de acción.

## Formatos de exportación

### Post (botón "Post" → `exportArticle()`)
HTML estándar para pegar en Elementor. Incluye título, copete, imagen de portada y cuerpo del artículo con formato.

### Medidas Gremiales (botón "Medidas" → `exportMedidas()`)
Formato especial con línea de tiempo integrada para publicar acciones/medidas gremiales. Tiene estructura distinta al post normal.

### Exportar Portada (botón "Exportar Portada")
Descarga la imagen del canvas como PNG para usarla como imagen destacada en WordPress.

### Conversión Post → Medidas (botón con flechas → `openPostToMedidasModal()`)
Modal que convierte el contenido de un post ya exportado al formato Medidas.

## Stack técnico

- HTML/CSS/JS puro, sin frameworks ni bundler.
- Un solo archivo: `index.html` (~2800 líneas).
- Font Awesome 6.5 desde CDN.
- Canvas API para la portada.
- Sin dependencias externas ni node_modules.

## Despliegue

Hosteado en GitHub Pages: https://danielcastronuevo.github.io/atepsa-converter/

Para actualizar: editar `index.html` y hacer push a `main`. GitHub Pages sirve directo desde `main`.

## Consideraciones para mobile

La app fue originalmente diseñada para desktop. Tiene layout flex horizontal. Al editar desde el celular considerar que la vista previa puede ser pequeña — la funcionalidad de exportar (copiar al portapapeles) sigue funcionando.
