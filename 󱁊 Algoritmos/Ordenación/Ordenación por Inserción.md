## Complejidad

- Mejor caso: O(n)
- Caso medio: O(n²)
- Peor caso: O(n²)

## Pseudocódigo

![[insercion.png]]

## Explicación 

El algoritmo de ordenación por inserción es un método de clasificación que funciona dividiendo la lista en dos partes: una parte ordenada y otra desordenada.

Supongamos el siguiente vector desordenado:

![[insercion2.jpg]]

Inicialmente partimos de que la parte ordenada es el primer elemento del vector (el 6). A continuación toma al segundo elemento del vector y lo compara con la parte ordenada (bucle mientras). Como 5 < 6, entonces se colocaría en primer lugar.

Partimos de que se han ordenado los tres primeros números, quedando el vector tal que así:

![[insercion3.jpg]]

El siguiente número a ordenar sería el 1. En esta iteracción, la parte ordenada sería [3,5,6]. Para ordenar empezaría comparando el 1 con el 6, pero el 6 es mayor que 1, por tanto continuaría. Seguidamente, compararía con el 5 y el 3. Como ambos son mayores que el 1 y ha llegado a la primera posición, se inserta en dicho lugar el 1.

![[insercion4.jpg]]

Durante la ejecución del bucle, se compara el número que se va a insertar con los números en la parte ordenada. Si el número a insertar es mayor que el número en comparación, ese número se desplaza una posición a la derecha. La inserción se realiza en el momento en que el número a comparar es más pequeño que el número a insertar o cuando se alcanza el principio del vector.