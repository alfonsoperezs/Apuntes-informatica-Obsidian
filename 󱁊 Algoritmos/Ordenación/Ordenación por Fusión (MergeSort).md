## Complejidad

Suponiendo puramente recursiva: O(nlogn)
## Pseudocódigo

![[fusion1.png]]
![[fusion2.png]]
## Explicación 

El algoritmo MergeSort, conocido por su enfoque recursivo, nos permite descomponer la tarea de ordenar un vector de números desordenados en pasos más pequeños. A medida que desentrañamos el funcionamiento de este algoritmo, es interesante observar cómo se asemeja al recorrido posorden de los árboles binarios. En este proceso, el árbol de recursividad se desarrolla siempre primero por la izquierda (subárbol izquierdo), a continuación por la derecha (subárbol derecho) y, finalmente, llegamos al vector original, que se convierte en la raíz de nuestro árbol.

Como primer paso, el vector principal se divide en dos mitades, que a su vez se dividirán en sucesivas mitades hasta llegar al caso base.

![[Screenshot_20231108_094546.png]]

Una vez que se ha dividido repetidamente el vector original en subvectores más pequeños y hemos alcanzado el caso base, el enfoque cambia hacia la ordenación. En este punto, se toma el primer subvector izquierdo y se procede a ordenarlo. Luego, el proceso se repite para el subvector derecho, donde se lleva a cabo una ordenación similar.

![[Screenshot_20231108_094655.png]]

Este proceso de ordenación de los subvectores izquierdo y derecho se repite recursivamente para cada nivel del árbol de recursividad hasta que finalmente, después de la combinación de todos los subvectores, obtengamos el vector original ordenado en su totalidad.

![[Screenshot_20231108_094716.png]]

![[Screenshot_20231108_094730.png]]

![[Screenshot_20231108_094744.png]]

![[Screenshot_20231108_094759.png]]

![[Screenshot_20231108_094810.png]]

Finalmente, tras tener ordenadas los dos subvectores del vector principal, se aplicará una última ordenación por fusión y así acabar el procedimiento.

![[Screenshot_20231108_094828.png]]

En este ejemplo, estamos aplicando un algoritmo de fusión con un umbral igual a 0. Cuando el tamaño del vector (n) sea mayor que este umbral, el algoritmo aplicará la ordenación por fusión. La ordenación por fusión implica dividir el vector en sublistas más pequeñas, ordenar cada sublista de manera independiente y, finalmente, fusionarlas para obtener la lista ordenada completa. Este enfoque es altamente eficiente para listas de gran tamaño, ya que la ordenación por fusión ofrece un rendimiento estable y se adapta de manera óptima a conjuntos de datos extensos.

Sin embargo, cuando el tamaño del vector sea igual o menor que el umbral (en este caso, umbral = 0), el algoritmo cambiará su estrategia y utilizará la ordenación por inserción en lugar de la fusión. La ordenación por inserción es más adecuada para listas pequeñas, ya que su proceso de ordenación es eficiente y sencillo de implementar en este contexto.

[[Ordenación por Inserción]]