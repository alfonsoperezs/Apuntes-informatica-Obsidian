# em vs rem
---
- **`em`**: Es una unidad relativa al tamaño de fuente del elemento en el que se encuentra. Si el tamaño de la fuente de un elemento es 16px, entonces 1em será igual a 16px. Si aplicas un `font-size` de 2em a un elemento dentro de este, el tamaño de la fuente será 32px (2 * 16px). Ten en cuenta que si un elemento tiene un tamaño de fuente heredado de un contenedor, ese valor se ve afectado por la jerarquía.
- **`rem`**: Es una unidad relativa a la raíz del documento, es decir, siempre se refiere al tamaño de la fuente definido en el `<html>`. Si el tamaño de la fuente raíz (`<html>`) es 16px, entonces 1rem será igual a 16px, independientemente de los elementos secundarios o su jerarquía.
# vh vs vw
---
- **`vh` (viewport height)**: Representa un porcentaje de la altura de la ventana del navegador. 1vh es igual al 1% de la altura de la ventana visible.
    - Ejemplo: Si la altura de la ventana es 1000px, entonces 1vh sería 10px.
- **`vw` (viewport width)**: Representa un porcentaje del ancho de la ventana del navegador. 1vw es igual al 1% del ancho de la ventana visible.
    - Ejemplo: Si el ancho de la ventana es 1200px, entonces 1vw sería 12px

Podemos calcular dinámicamente el tamaño de por ejemplo el tamaño de fuente:

```css
html {
	font-size: calc(1em+1vw);
}
```