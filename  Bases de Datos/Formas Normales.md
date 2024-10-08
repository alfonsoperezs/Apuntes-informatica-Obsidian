# 1º Forma Normal
---

Una base de datos está en 1º FN si cada columna contiene valores atómicos.

# 2º Forma Normal
---

Un esquema de relación está en la Segunda Forma Normal (2FN) si está en 1FN y además todos los atributos **no primos** son totalmente dependientes de cada clave candidata del esquema, no permitiéndose dependencias parciales.

Otras características que debe cumplir:
- Si la clave principal es un solo atributo, no hay problemas de dependencias parciales.
- Si la clave principal consta de múltiples atributos, cada otro atributo debe depender de la clave completa, no de solo una parte de ella.
	![[Pasted image 20240403180702.png]]

# 3º Forma Normal
---

Una base de datos está en 3º FN si está en 2º FN y además se cumple que no debe haber dependencias transitivas, es decir, ningún atributo **NO CLAVE** debe depender de otro atributo **NO CLAVE**.

# Forma Normal Boyce Codd
---

Una base de datos está en FNBC si está en 3º FN y además se cumple que ningún atributo primo depende parcialmente de la clave candidata.