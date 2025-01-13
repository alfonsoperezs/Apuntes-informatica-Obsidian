El comando `fsck` (que significa "file system check" o "file system consistency check") se utiliza en sistemas operativos basados en Unix, como Linux, para verificar y reparar sistema de ficheros [¹] dañados o con problemas de consistencia. Este comando se utiliza típicamente cuando un sistema de archivos muestra signos de corrupción o errores que pueden afectar la integridad de los datos almacenados en él. 

Sintaxis : `fsck [opciones] dispositivo`

- ## Opciones: 
	- `-a`: Automáticamente intenta reparar cualquier problema encontrado sin pedir confirmación del usuario.
	- `-y`: Responde "sí" a todas las preguntas automáticamente, lo que es útil para la automatización.
	- `-c`: Realiza una comprobación completa del sistema de archivos, incluso si parece estar en buen estado.
	- `-r`: Intenta reparar los problemas que encuentra.
	- `-n`: Simula una comprobación de sistema de archivos sin realizar ninguna corrección.


[¹] [[Sistema de ficheros]]