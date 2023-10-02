El "sticky bit" (bit pegajoso) es un atributo especial de permisos utilizado en sistemas Unix y Linux para controlar el comportamiento de eliminación de archivos en directorios compartidos. Cuando se establece el sticky bit en un directorio, afecta quién tiene permiso para borrar archivos en ese directorio. El sticky bit se representa como un "t" minúscula en la columna de permisos de un directorio.

Cuando un directorio tiene el sticky bit activado:
- **Root**: El usuario root siempre puede eliminar cualquier archivo en el directorio, independientemente de los permisos del archivo o del directorio.
- **Propietario del Directorio**: El propietario del directorio (el usuario que creó el directorio) puede eliminar cualquier archivo en el directorio, incluso si no tiene permisos de escritura en el archivo.
- **Propietario de la Entrada a Borrar**: Solo el propietario del archivo que se intenta borrar puede eliminarlo, incluso si otros usuarios tienen permisos de escritura en el directorio. Esto significa que, en un directorio con sticky bit activado, los usuarios no pueden borrar archivos de otros usuarios, a menos que sean el propietario del archivo.

El sticky bit es comúnmente utilizado en directorios temporales, como "/tmp", para evitar que los usuarios borren archivos de otros usuarios y para garantizar la privacidad y seguridad de los datos temporales.