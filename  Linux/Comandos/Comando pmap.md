Se utiliza para mostrar información detallada sobre el espacio de direcciones de memoria de un proceso en ejecución. Proporciona una vista detallada de cómo se está utilizando la memoria virtual en ese proceso.

Sintaxis: `pmap [PID]`

## Ejemplo de uso

Una vez conseguido el PID (en este caso es 5699), ejecutamos el comando `pmap 5699` y obtenemos lo siguiente:

![[Screenshot_20231005_111706.png]]

Vemos que obtenemos una tabla con cuatro columnas donde se puede ver:
	1. Las direcciones de memoria virtual utilizadas por el proceso.
	2. Cuanta memoria se le ha asignado a cada región.
	3. Los permisos de acceso [¹] para cada región de memoria.
	4. Etiquetas descriptivas para las regiones de memoria, donde se indica el tipo o uso de la región de memoria en el contexto del proceso.


[¹] [[Permisos]]