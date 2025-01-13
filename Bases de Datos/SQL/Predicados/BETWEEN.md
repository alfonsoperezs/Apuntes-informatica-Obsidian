La cláusula `BETWEEN` se utiliza en consultas SQL para seleccionar valores dentro de un rango especificado.

## Sintaxis
---

```sql
valor BETWEEN valor_mínimo AND valor_máximo;
```

## Ejemplo de uso
---

Supongamos que queremos seleccionar todos los empleados cuyos salarios estén entre 30000 y 50000. Podemos usar la cláusula `BETWEEN` de la siguiente manera:

```sql
SELECT *
FROM empleados
WHERE salario BETWEEN 30000 AND 50000;
```
