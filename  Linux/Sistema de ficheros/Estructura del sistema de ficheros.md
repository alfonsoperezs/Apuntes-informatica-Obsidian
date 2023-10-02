- ## Directorios Principales
	- **/**: La barra diagonal / sola representa la raíz del árbol del sistema de archivos.
	- **/bin**: Abreviatura de "binarios" y contiene utilidades fundamentales como ls, cp, rm, bash, que son generalmente necesarias para todos los usuarios.
	- **/sbin**: Contiene binarios relacionados con utilidades de administración, como fsck, mkfs y mount.
	- **/boot**: Contiene todos los archivos necesarios para el proceso de arranque exitoso.
	- **/dev**: Abreviatura de "dispositivos". Contiene representaciones de archivos de dispositivos periféricos y seudo-dispositivos.
	- **/etc**: Contiene archivos de configuración y bases de datos del sistema. Originalmente también contenía "utilidades de mantenimiento peligrosas" como init, pero generalmente se han trasladado a /sbin u otros lugares.
	- **/home**: Contiene los directorios de inicio de los usuarios.
	- **/lib**: Contiene bibliotecas del sistema y algunos archivos críticos como módulos del kernel o controladores de dispositivos.
	- **/media**: Punto de montaje predeterminado para dispositivos extraíbles como memorias USB, reproductores de medios, etc.
	- **/mnt**: Abreviatura de "montaje". Contiene puntos de montaje del sistema de archivos. Se utilizan, por ejemplo, si el sistema utiliza múltiples discos duros o particiones de disco duro. También se utiliza a menudo para sistemas de archivos remotos (de red), unidades de CD-ROM/DVD, etc.
	- **/proc**: Sistema de archivos virtual procfs que muestra información sobre procesos como archivos.
	- **/root**: El directorio de inicio del superusuario "root", es decir, el administrador del sistema. El directorio de inicio de esta cuenta suele estar en el sistema de archivos inicial y, por lo tanto, no está en /home (que puede ser un punto de montaje para otro sistema de archivos) en caso de que sea necesario realizar mantenimiento específico cuando otros sistemas de archivos no estén disponibles. Esto podría ocurrir, por ejemplo, si un disco duro sufre fallas físicas y no puede montarse correctamente.
	- **/tmp**: Un lugar para archivos temporales. Muchos sistemas limpian este directorio al inicio; podría tener tmpfs montado encima de él, en cuyo caso su contenido no sobrevive a un reinicio, o podría ser eliminado explícitamente por un script de inicio en el momento del arranque.
- ## Directorios de Usuario

	- **/usr**: Originalmente, el directorio que contenía los directorios de inicio de los usuarios, su uso ha cambiado. Ahora almacena programas ejecutables, bibliotecas y recursos compartidos que no son críticos para el sistema, como el Sistema de Ventanas X, KDE, Perl, etc. Sin embargo, en algunos sistemas Unix, algunas cuentas de usuario todavía pueden tener un directorio de inicio que es un subdirectorio directo de /usr, como el valor predeterminado en Minix. (en sistemas modernos, estas cuentas de usuario a menudo están relacionadas con el uso del servidor o del sistema y no se utilizan directamente por una persona).
	- **/usr/bin**: Este directorio almacena todos los programas binarios distribuidos con el sistema operativo que no residen en /bin, /sbin o (raramente) /etc.
	- **/usr/include**: Almacena las cabeceras de desarrollo utilizadas en todo el sistema. Los archivos de cabecera son principalmente utilizados por la directiva #include en el lenguaje de programación C/C++.
	- **/usr/lib**: Almacena las bibliotecas requeridas y archivos de datos para programas almacenados en /usr u otros lugares.

- ## Directorios de Datos Variables

	- **/var**: Una abreviatura de "variable". Un lugar para archivos que pueden cambiar a menudo, especialmente en tamaño, como el correo electrónico enviado a los usuarios en el sistema o archivos de bloqueo de identificadores de proceso (PID).
	- **/var/log**: Contiene archivos de registro del sistema.
	- **/var/mail**: El lugar donde se almacenan todos los correos electrónicos entrantes. Los usuarios (que no sean root) solo pueden acceder a su propio correo. A menudo, este directorio es un enlace simbólico a /var/spool/mail.
	- **/var/spool**: Directorio de cola. Contiene trabajos de impresión, colas de correo y otras tareas en cola.
	- **/var/tmp**: Un lugar para archivos temporales que deben preservarse entre reinicios del sistema.