
## Paso 1: Crear un Repositorio Git

1. Abre tu terminal o línea de comandos.
    
2. Navega al directorio deseado utilizando el comando `cd`. Por ejemplo:
    
    `cd /ruta/a/tu/archivo
    
3. Inicializa un nuevo repositorio Git en ese directorio utilizando el siguiente comando:
    
    `git init`
    

## Paso 2: Agregar y Confirmar Cambios

1. Navega al directorio dode se ubica el respositorio.
2. Agrega los archivos modificados al área de preparación para confirmarlos utilizando el comando:
    
    `git add .`
    
    El punto (.) agrega todos los archivos modificados en el directorio actual. Puedes especificar archivos individuales si lo deseas.
    
3. Confirma los cambios con un mensaje descriptivo utilizando el comando:
    
    `git commit -m "Mensaje descriptivo de los cambios"`
    

## Paso 3: Subir el Repositorio a un Servidor Remoto

1. Crea un repositorio en un servicio de alojamiento como por ejemplo GitHub.
2. Sigue las instrucciones proporcionadas por el servicio para agregar el repositorio remoto. Por lo general, esto implica agregar un control remoto con un comando como:
    
    `git remote add origin URL_DEL_REPOSITORIO`
    
    Asegúrate de reemplazar `URL_DEL_REPOSITORIO` con la URL real de tu repositorio remoto.
    
3. Sube tus cambios al repositorio remoto con el siguiente comando:
    
    `git push -u origin master`
    
    Esto enviará tus cambios al servidor y establecerá la rama "master" como la rama principal.