La cláusula `IN` se utiliza en consultas SQL para comparar un valor con una lista de posibles valores y devolver filas que coincidan con al menos uno de esos valores.

## Sintaxis
---

```sql
columna IN (valor1, valor2, ...);
```

## Ejemplo de uso
---

Supongamos que queremos seleccionar todos los empleados cuyo departamento sea "Ventas" o "Marketing". Podemos usar la cláusula `IN` de la siguiente manera:

```sql
SELECT *
FROM empleados
WHERE departamento IN ('Ventas', 'Marketing');
```
