## Pseudocódigo

![[shell.png]]
## Explicación

El algoritmo de ordenación Shell se ejecuta de la siguiente manera:

1. Se elige una secuencia de brechas (gaps) que se utilizan para dividir el conjunto de datos. La secuencia de brechas puede variar según la implementación, pero a menudo se utiliza la secuencia de brechas de Knuth: 1, 4, 13, 40, 121, 364, etc.
2. Comenzando con la brecha más grande, se divide el conjunto de datos en subconjuntos de elementos que están separados por la brecha.
3. En cada subconjunto, se aplica un algoritmo de inserción (como el que describí anteriormente) para ordenar esos elementos de manera local.
4. Luego, la brecha se reduce y se repite el proceso para subconjuntos más pequeños hasta que la brecha sea igual a 1.
5. Finalmente, se aplica un último paso de ordenación por inserción con brecha 1 para asegurarse de que la lista esté completamente ordenada.

La idea detrás de la ordenación Shell es que al ordenar primero con brechas más grandes, se mueven elementos más pequeños hacia sus posiciones finales más rápidamente. Luego, a medida que las brechas se reducen, los elementos más pequeños se agrupan juntos, lo que facilita su ordenación en las últimas etapas con brechas más pequeñas.

[[Ordenación por Inserción]]