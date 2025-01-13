La cláusula `HAVING` se utiliza en consultas SQL junto con la cláusula [[GROUP BY]] para filtrar grupos de filas devueltos por la consulta basándose en condiciones específicas.

## Restricciones
---

- Puede incluir constantes, funciones y condiciones con columnas incluidas en el `GROUP BY`.

## Ejemplo de uso
---

Supongamos que queremos encontrar los departamentos con ventas totales superiores a 10000. Podemos usar la cláusula `HAVING` de la siguiente manera:

```sql
SELECT departamento, SUM(total_ventas) AS total_ventas_por_departamento
FROM ventas
GROUP BY departamento
HAVING SUM(total_ventas) > 10000;
```

