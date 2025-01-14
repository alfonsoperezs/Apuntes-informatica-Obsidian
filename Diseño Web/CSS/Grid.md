El **grid** de una página web es un sistema de diseño que utiliza una serie de filas y columnas para estructurar y alinear los elementos de la página. Se basa en el concepto de dividir el espacio en una cuadrícula, lo que facilita la organización de contenido de manera más controlada y coherente.

# Características
---
- **Filas y columnas**: La página se divide en una serie de filas (`grid-rows`) y columnas (`grid-columns`). Los elementos dentro de la cuadrícula se colocan en estos espacios.
- **Posicionamiento controlado**: Puedes especificar en qué fila y columna debe colocarse un elemento o hacer que se extienda a través de varias filas o columnas.
- **Responsividad**: El grid se adapta fácilmente a diferentes tamaños de pantalla, lo que facilita la creación de diseños que se ajusten a dispositivos móviles, tabletas y escritorios.

```css
.container {
  display: grid;
  grid-template-columns: repeat(3, 1fr); /* 3 columnas de igual tamaño */
  grid-template-rows: auto; /* las filas se ajustan al contenido */
  gap: 10px; /* espacio entre los elementos */
}
```
