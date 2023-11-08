## Complejidad

Mejor caso: O(nlogn)
Caso medio: O(nlogn)
Peor caso: O(n²)
## Pseudocódigo

![[qs1.png]]
![[qs2.png]]

**Observaciones:**
	- Es preferible deshacer el último cambio que incluir un test dentro del bucle.
	- Evitar llamada a funciones

## Explicación

En primer lugar, se halla la mediana de 3.

![[Screenshot_20231108_155321.png]]

Seguidamente, se coloca el menor numero en v[i], el segundo menor en el pivote y el último en v[j].

![[Screenshot_20231108_155349.png]]

A continuación, se intercambia el pivote con v[j - 1].

![[Screenshot_20231108_155400.png]]

Se empieza un doble recorrido incrementando k hasta que llegue a un número mayor que el pivote y decrementando m hasta llegar a un número menor que el pivote.

![[Screenshot_20231108_161412.png]]
![[Screenshot_20231108_162551.png]]

El procedimiento es el mismo en todo el vector hasta que que m <= k. Destacar que hacemos un paso de más con el fin de no incluir un test dentro del bucle, por tanto, hay que deshacer el último intercambio.

![[Screenshot_20231108_162744.png]]
![[Screenshot_20231108_163003.png]]

Por último se coloca el pivote en la posición k.

![[Screenshot_20231108_163115.png]]

Finalizado este paso, se harían las sucesivas llamadas recursivas a la parte izquierda del vector, sin incluir el vector.

![[Screenshot_20231108_163411.png]]
![[Screenshot_20231108_163548.png]]

Una vez llegado al umbral, se detiene la recursión.

![[Screenshot_20231108_163559.png]]

Se hace el mismo proceso con la parte derecha del vector, sin incluir el pivote.

![[Screenshot_20231108_163625.png]]

Finalizado este paso, se realiza una ordenación por inserción del vector resultante. 

![[Screenshot_20231108_163644.png]]

[[Ordenación por Inserción]]