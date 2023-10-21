El comando `git status` es utilizado para mostrar el estado actual de tu repositorio de Git.

## Ejemplo de uso

Vamos suponer el directorio `hellogit` donde se acaba de inicializar el repositorio. Dicho directorio contiene un archivo de texto llamado `archivo1.txt`. Al ejecutar el comando `git status` podemos observar:

![[Screenshot_20231022_002032.png]]

En primer lugar nos indica que dicha rama no ha tenido ningún commit hasta este momento (el lógico ya que acaba de ser creado). En segundo lugar vemos un listado de ficheros que están en el propio directorio, pero que no están guardados en el repositorio.

![[add_status.png]]

Tras haber hecho `git add`, volvemos a ejecutar el comando y se ve como ahora nos indica que se han guardado los cambios del repositorio (en este caso, se ha añadido un nuevo fichero).

[[Git add]]