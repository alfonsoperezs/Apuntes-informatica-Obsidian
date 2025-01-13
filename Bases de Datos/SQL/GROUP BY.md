La cláusula `GROUP BY` se utiliza en consultas SQL para agrupar filas que tienen el mismo valor en una o más columnas y aplicar funciones de agregación a cada grupo.

## Sintaxis
---

```sql
SELECT columna1, columna2, func_agregacion(columna3)
FROM tabla
GROUP BY columna1, columna2;
```

## Restricciones
---

- Al usar `GROUP BY`, en el [[SELECT]] solo puede haber las columnas que se incluyen y funciones.