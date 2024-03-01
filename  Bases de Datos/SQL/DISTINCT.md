La cláusula `DISTINCT` se utiliza en consultas SQL para eliminar filas duplicadas de los resultados de la consulta, devolviendo solo valores únicos.

## Sintaxis
---

```sql
SELECT DISTINCT columna1, columna2
FROM tabla;
```

## Ejemplo de uso

---

Supongamos que tenemos una tabla llamada `empleados` con las columnas `nombre`, `apellido` y `departamento`. Si queremos obtener una lista de todos los departamentos únicos en los que trabajan los empleados, usaríamos la siguiente consulta:

```sql
SELECT DISTINCT departamento
FROM empleados;
```


