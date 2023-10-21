El comando `git commit` se utiliza para confirmar los cambios que has agregado previamente al área de preparación. Podemos pensar este comando como hacerle una fotografía a nuestro proyecto en un momento determinado.

La manera más habitual de usar este comando es `git commit -m "descripción del commit"`. Destacar que se debe incluir una descripción del commit.

## Cómo usar

Suponemos que hemos empezado nuestro proyecto, por lo tanto hemos creado un fichero y hemos escrito cosas en él. A continuación queremos guardar nuestros cambios.

![[add_status.png]]

Acabamos de hacer `git add` y ahora queremos guardar los cambios. Ejecutamos el comando `git commit -m` y ya estarán confirmados los cambios.

![[Screenshot_20231022_005221.png]]

Fijarse en el número `6f4b444`. Ese número se le denomina hash y es un identificador único del commit. Esto representa que el commit que acabamos de hacer es único e irrepetible.

[[Git add]] [[Git status]]