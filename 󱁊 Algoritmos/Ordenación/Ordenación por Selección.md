## Complejidad

Mejor caso: O(n²)
Caso medio: O(n²)
Peor caso: O(n²)
## Pseudocódigo

![[seleccion.png]]
## Explicación

El algoritmo de ordenación por selección consiste en recorrer las n-1 posiciones del vector, y en cada iteracción, buscar en el rango [i+1,n] el menor elemento de la lista e intercambiarlo con i.

Supongamos el siguiente vector desordenado:

![[insercion2.jpg]]

En la primera iteracción, la posición i sería la primera posición. Buscaríamos en el rango [i+1,n], en este caso [5,3,1,8]. Escogeríamos el menor número de esos (el 1) y lo compararíamos con el número de la posición i. Como 1 < 6, entonces se intercambian las posiciones, quedando tal que así:

![[seleccion2.jpg]]

En la segunda iteracción, i sería la segunda posición. Se escoge el mínimo de [3,6,8], que sería el 3. Como 3 < 5, se intercambian las posiciones.

![[seleccion3.jpg]]

Podemos afirmar que al final de cada iteracción, el rango [1,i] está ordenado. Se da la casualidad de que [i+1,n] también lo está, pero no tiene por qué. Si continuasemos la ejecución en este caso, se haría exactamente como ahora, con la excepción de que el mínimo sería mayor que el i-ésimo número.

Detallar que se hace con todos los números del vector excepto con el último, ya que al llegar ahí, todo el vector estaría ordenado.