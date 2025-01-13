La función `COALESCE` se utiliza en consultas SQL para devolver el primer valor no nulo de una lista de expresiones.

## Ejemplo de uso
---

Supongamos que queremos seleccionar los nombres de los empleados y, en caso de que el campo de apellido esté vacío, queremos mostrar el valor "Apellido Desconocido". Podemos usar la función `COALESCE` de la siguiente manera:

```sql
SELECT nombre, COALESCE(apellido, 'Apellido Desconocido') AS apellido
FROM empleados;
```

