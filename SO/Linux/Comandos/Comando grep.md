El comando `grep` se utiliza para buscar patrones de texto en archivos o en la salida de otros comandos.

Sintaxis: `grep [opciones] patrón [archivo(s)]`

- ## Opciones
	- `-i`: Realizar una búsqueda insensible a mayúsculas y minúsculas.
	- `-r` o `-R`: Buscar de forma recursiva en directorios y subdirectorios.
	- `-l`: Mostrar solo los nombres de los archivos que contienen coincidencias en lugar de las líneas de texto reales.
	- `-v`: Invertir la búsqueda para mostrar las líneas que no coinciden con el patrón.
	- `-c`: Mostrar el número de líneas que coinciden con el patrón en lugar de las líneas reales.

## Ejemplos de uso

Supongamos que queremos encontrar en un directorio un subdiretorio con un nombre específico. En este caso vamos situarnos en el directorio `/home`. Al ejecutar el comando `ls -l` podemos observar lo siguiente:

![[grep 1.png]]

Supongamos que deseamos encontrar el directorio `Documents`. Para ello, si metemos la salida del comando `ls -l` a `grep Documents` [¹] podemos filtrar de entre todos los directorios el que buscamos.

![[grep 2.png]]

Otro ejemplo sería localizar en un archivo una palabra/frase. En este caso tenemos un archivo con el siguiente contenido:

![[Screenshot_20231003_163632.png]]

Supongamos que queremos encontrar la palabra "apuntes". Para ello si ejecutamos el comando `grep "apuntes" archivo1.txt` nos remarcará esa palabra.

![[Screenshot_20231003_163709.png]]

[¹] [[Tuberías]]


