## Usuario Real (Real User)

- **Descripción**: El "usuario real" se refiere al usuario que ha iniciado o lanzado un proceso en un sistema Unix o Linux. Es el usuario que ejecuta el proceso inicialmente.
- **Identificación**: El usuario real se identifica mediante su nombre de usuario y se verifica durante el inicio de sesión.
- **Importancia**: El usuario real es importante porque determina quién tiene permisos para ejecutar el proceso y qué recursos puede acceder.
## Usuario Efectivo (Effective User)

- **Descripción**: El "usuario efectivo" se refiere al usuario bajo cuyas credenciales o permisos se está ejecutando actualmente un proceso, incluso si el proceso fue iniciado por otro usuario.
- **Identificación**: El usuario efectivo se identifica mediante la información contenida en el proceso, que puede cambiar durante la ejecución del programa.
- **Importancia**: El usuario efectivo es importante porque determina qué acciones y recursos puede utilizar el proceso en nombre de un usuario específico, independientemente del usuario real que inició el proceso.

En resumen, el usuario real y el usuario efectivo son dos identidades cruciales en la ejecución de procesos en sistemas Unix/Linux. El usuario real representa quién inicia el proceso, mientras que el usuario efectivo determina bajo cuyos permisos se ejecuta el proceso en un momento dado.