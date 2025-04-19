## Caso 1

Tenemos este fichero con este contenido en la rama `main.

```bash
alfonsoperezs@peixepc:/tmp/gittest$ ls
a.txt
alfonsoperezs@peixepc:/tmp/gittest$ cat a.txt
hola
alfonsoperezs@peixepc:/tmp/gittest$ git add .
alfonsoperezs@peixepc:/tmp/gittest$ git commit -m "commit main"
[main (root-commit) 77bd532] commit main
 1 file changed, 1 insertion(+)
 create mode 100644 a.txt
```

Creamos y nos vamos a la rama `dev`. En ella añadimos una nueva línea adicional a la que teníamos.
```bash
alfonsoperezs@peixepc:/tmp/gittest$ git checkout -b dev
Switched to a new branch 'dev'
alfonsoperezs@peixepc:/tmp/gittest$ nano a.txt
alfonsoperezs@peixepc:/tmp/gittest$ cat a.txt
hola
mundo
alfonsoperezs@peixepc:/tmp/gittest$ git add .
alfonsoperezs@peixepc:/tmp/gittest$ git commit -m "cambios"
[dev 582651f] cambios
 1 file changed, 1 insertion(+)
```

Volvemos a la rama `main`, mergeamos los cambios hechos en la rama `dev` y sin problemas.

```bash
alfonsoperezs@peixepc:/tmp/gittest$ git checkout main
Switched to branch 'main'
alfonsoperezs@peixepc:/tmp/gittest$ cat a.txt
hola
alfonsoperezs@peixepc:/tmp/gittest$ git merge dev
Updating 77bd532..582651f
Fast-forward
 a.txt | 1 +
 1 file changed, 1 insertion(+)
alfonsoperezs@peixepc:/tmp/gittest$ cat a.txt
hola
mundo
```

## Caso 2

Tenemos el siguiente contenido en la rama `main`.

```bash
alfonsoperezs@peixepc:/tmp/gittest$ cat a.txt
1
2
3
4
5
6
7
```

En la rama `dev`, hacemos el siguiente cambio en la línea 3.

```bash
alfonsoperezs@peixepc:/tmp/gittest$ cat a.txt
1
2
D
4
5
6
7
```

Al volver a la rama `main`, vemos que alguien ha hecho un cambio en la línea 6.

```bash
alfonsoperezs@peixepc:/tmp/gittest$ cat a.txt
1
2
3
4
5
M
7
```

Como no se ha modificado la misma rama, podremos mergear sin problemas.

> [!tip]
> Pensar git como algo **incremental**.  

```bash
alfonsoperezs@peixepc:/tmp/gittest$ git merge dev
Auto-merging a.txt
Merge made by the 'ort' strategy.
 a.txt | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
alfonsoperezs@peixepc:/tmp/gittest$ cat a.txt
1
2
D
4
5
M
7
```

## Caso 3

Tenemos el siguiente contenido en la rama `main`.

```bash
alfonsoperezs@peixepc:/tmp/gittest$ cat a.txt
1
2
3
4
```

En la rama `dev`, hacemos el siguiente cambio en la línea 2.

```bash
alfonsoperezs@peixepc:/tmp/gittest$ git checkout -b dev
Switched to a new branch 'dev'
alfonsoperezs@peixepc:/tmp/gittest$ nano a.txt
alfonsoperezs@peixepc:/tmp/gittest$ cat a.txt
1
D
3
4
```

Al volver a la rama `main`, vemos que alguien ha hecho un cambio en la línea 2, justo donde nosotros hicimos un cambio. Tras mergear, nos indica que ha habido un conflicto.

```bash
alfonsoperezs@peixepc:/tmp/gittest$ cat a.txt
1
M
3
4
alfonsoperezs@peixepc:/tmp/gittest$ git merge dev
Auto-merging a.txt
CONFLICT (content): Merge conflict in a.txt
Automatic merge failed; fix conflicts and then commit the result.
```

Para ello vamos a nuestro editor de texto y nos saldrá arriba lo que ya había en la rama `main` y abajo lo que queremos mergear de la rama `dev`. A continuación, borraremos lo que no queremos (borramos también los comentarios de HEAD, dev, etc...).

```
1
<<<<<<< HEAD
M
=======
D
>>>>>>> dev
3
4
```

Tras seleccionar lo que queremos, nos quedó así en el editor.

```
1
D
3
4
```

Por último, debemos hacer un commit de la resolución del conflicto y veremos como se reflejan los cambios.

```bash
alfonsoperezs@peixepc:/tmp/gittest$ git commit -am "arreglado conflicto"
[main e25e3af] arreglado conflicto
alfonsoperezs@peixepc:/tmp/gittest$ cat a.txt
1
D
3
4
```