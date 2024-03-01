La cláusula `JOIN` se utiliza en consultas SQL para combinar filas de dos o más tablas basándose en una condición relacionada entre ellas.

## Sintaxis
---

```sql
SELECT columna1, columna2
FROM tabla1 JOIN tabla2 ON tabla1.columna = tabla2.columna;
```

## Precauciones
---

1. JOIN EXTERIOR:
	- Condición de `WHERE` puede eliminar el efecto del `JOIN EXTERIOR`
2. JOIN + 2 TABLAS:
	- Efecto multiplicativo al hacer `count`. Para solucionarlo se debe usar `distinct`.
	- Elementos que pueden desaparecer al no encontrar pareja en la 3 o siguientes tablas. Se necesita usar join exterior (o arrastrarlo) o usar parentesis para solucionarlo.




