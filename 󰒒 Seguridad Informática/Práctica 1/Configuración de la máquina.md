# Fichero interfaces
---
En el fichero /etc/network/interfaces es donde configuramos la red de nuestros servidores. 

Accedemos al fichero:

```bash
cat /etc/network/interfaces
```

![[Pasted image 20240923173934.png]]

Las interfaces que se deseen levantar durante el arranque de el sistema se deben indicar con `auto`.

# Fichero hosts
---
Es un archivo de texto que asocia direcciones IP con nombres de host.

```bash
cat /etc/hosts
```

![[Pasted image 20240923180356.png]]

(debian es el nombre de la máquina)

El formato es una IP (IPv4 o IPv6), seguida de espacios y el nombre asociado. El nombre debe comenzar con una letra y terminar con un carácter alfanumérico. Se permite el "-" y el ".".

Inicialmente nos encontramos con IPs de localhost y de multicast en el ámbito link-local (transmiten dentro del enlace o red local).

# Fichero nsswitch.conf
---
Fichero de configuración de las Bases de Datos del Sistema y del sistema de Conmutación de los Servicios de Nombres (Name Service Switch).

```bash
cat /etc/nsswitch.conf
```

![[Pasted image 20240923183218.png]]


