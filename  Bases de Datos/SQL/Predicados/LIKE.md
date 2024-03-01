La cláusula `LIKE` se utiliza en consultas SQL para realizar comparaciones de patrones en columnas de texto.

## Sintaxis
---

```sql
columna LIKE 'patrón';
```

## Patrones comunes
---

- `%`: Representa cero, uno o múltiples caracteres.
- `_`: Representa un único carácter.

## Ejemplo de uso
---

Supongamos que queremos seleccionar todos los empleados cuyos nombres empiecen con "J". Podemos usar la cláusula `LIKE` de la siguiente manera:

```sql
SELECT *
FROM empleados
WHERE nombre LIKE 'J%';
```