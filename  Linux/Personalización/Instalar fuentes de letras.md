1. Descargarse el .zip con las fuentes.
2. Descomprimir con el comando `unzip [fuente.zip]`.
3. Copiar la carpeta a la ruta `/usr/share/fonts/` para que esté disponible para todos los usuarios o a `~/.local/share/fonts/` para solo tu usuario. El comando a utilizar es `cp -r [carpeta] [ruta]`. Cabe mencionar que para copiar en la primera ruta, necesitas tener permisos de administrador.
4. Actualiza la caché de fuentes mediante el comando `fc-cache -f -v`.
