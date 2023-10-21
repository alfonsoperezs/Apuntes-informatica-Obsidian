El comando `git add` se utiliza para agregar cambios de archivos en tu directorio de trabajo al área de preparación. En otras palabras, este comando te permite seleccionar qué cambios deseas incluir en tu próximo commit.

- ## Modos de uso más comunes
	- Agregar archivos individuales: `git add <nombre_del_fichero>` 
	- Agregar todo el contenido: `git add .`
	- Agregar los cambios de un directorio: `git add RUTA_DEL_DIRECTORIO/

## Ejemplos de uso

![[Screenshot_20231022_002032.png]]

Tenemos este repositorio donde queremos añadir el fichero `archivo1.txt` para que se guarden los cambios. En este caso, añadir el fichero es equivalente a añadir todo el directorio, por tanto es indiferente usar `git add .` que `git add archivo1.txt`.

![[add_status.png]]
