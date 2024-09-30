# Fichero interfaces
---
En el fichero /etc/network/interfaces es donde configuramos la red de nuestros servidores. 

```bash
cat /etc/network/interfaces
```

![[images/etc-interfaces.png]]

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

# Distribución de mi máquina
---
```bash
lsb_release -a
```
# Targets
---
Los targets son un conjunto de servicios y características activas por defecto en el sistema.

## Ver target por defecto

```bash
systemctl get-default
```

```
graphical.target
```

## Targets activos en el sistema

```bash
systemctl list-units --type=target
```

```

  UNIT                   LOAD   ACTIVE SUB    DESCRIPTION
  basic.target           loaded active active Basic System
  cryptsetup.target      loaded active active Local Encrypted Volumes
  getty.target           loaded active active Login Prompts
  graphical.target       loaded active active Graphical Interface
  integritysetup.target  loaded active active Local Integrity Protected Volumes
  local-fs-pre.target    loaded active active Preparation for Local File Systems
  local-fs.target        loaded active active Local File Systems
  multi-user.target      loaded active active Multi-User System
  network-online.target  loaded active active Network is Online
  network.target         loaded active active Network
  nss-user-lookup.target loaded active active User and Group Name Lookups
  paths.target           loaded active active Path Units
  remote-fs.target       loaded active active Remote File Systems
  slices.target          loaded active active Slice Units
  sockets.target         loaded active active Socket Units
  sysinit.target         loaded active active System Initialization
  time-set.target        loaded active active System Time Set
  timers.target          loaded active active Timer Units
  veritysetup.target     loaded active active Local Verity Protected Volumes

LOAD   = Reflects whether the unit definition was properly loaded.
ACTIVE = The high-level unit activation state, i.e. generalization of SUB.
SUB    = The low-level unit activation state, values depend on unit type.
19 loaded units listed. Pass --all to see loaded but inactive units, too.
To show all installed unit files use 'systemctl list-unit-files'.

```

## Targets disponibles en el sistema

```bash
systemctl list-unit-files --type=target
```

```
UNIT FILE                     STATE    PRESET
basic.target                  static   -
blockdev@.target              static   -
bluetooth.target              static   -
boot-complete.target          static   -
cryptsetup-pre.target         static   -
cryptsetup.target             static   -
ctrl-alt-del.target           alias    -
default.target                alias    -
emergency.target              static   -
exit.target                   disabled disabled
factory-reset.target          static   -
final.target                  static   -
first-boot-complete.target    static   -
getty-pre.target              static   -
getty.target                  static   -
graphical.target              static   -
halt.target                   disabled disabled
hibernate.target              static   -
hybrid-sleep.target           static   -
initrd-fs.target              static   -
...
```

# Services
---
Un servicio es un programa que se ejecuta en segundo plano, fuera del control interactivo de los usuarios del sistema, ya que carecen de una interfaz.

## Listar services

```bash
systemctl list-unit-files --type=service
```

```
UNIT FILE                                  STATE           PRESET
accounts-daemon.service                    enabled         enabled
alsa-restore.service                       static          -
alsa-state.service                         static          -
alsa-utils.service                         masked          enabled
anacron.service                            enabled         enabled
apparmor.service                           enabled         enabled
apt-daily-upgrade.service                  static          -
apt-daily.service                          static          -
autovt@.service                            alias           -
avahi-daemon.service                       enabled         enabled
bluetooth.service                          enabled         enabled
bolt.service                               static          -
colord.service                             static          -
configure-printer@.service                 static          -
console-getty.service                      disabled        disabled
console-setup.service                      enabled         enabled
container-getty@.service                   static          -
cron.service                               enabled         enabled
cryptdisks-early.service                   masked          enabled
cryptdisks.service                         masked          enabled
cups-browsed.service                       enabled         enabled
cups.service                               enabled         enabled
dbus-fi.w1.wpa_supplicant1.service         alias           -
dbus-org.bluez.service                     alias           -
...

188 unit files listed.
```

## Ver si los servicios fallan

```bash
systemctl list-unit-files --type=service --state=failed
```

# Unidades
---
## Ver tipos de unidades

```bash
systemctl list-units -t help
```

```
Available unit types:
service
mount
swap
socket
target
device
automount
timer
path
slice
scope
```

# Tiempos de botado
---
## Tiempo de botado de kernel y userspace

```bash
systemd-analyze
```

```
Startup finished in 2min 49.054s (kernel) + 9min 33.536s (userspace) = 12min 22.590s
multi-user.target reached after 9min 33.499s in userspace.
```

## Tiempo de botado de cada servicio

```bash
systemd-analyze blame
```

# Systemd-timesyncd
---
`systemd-timesyncd` es un demonio que se ha añadido para sincronizar el reloj del sistema a través de la red con una fuente de tiempo precisa.

Comprobamos que el servicio está activo:

```
systemd-timesyncd.service                  enabled         enabled
```

Accedemos a su fichero de configuración:

```bash
cat /etc/systemd/timesyncd.conf
```

```
#  This file is part of systemd.
#
#  systemd is free software; you can redistribute it and/or modify it under the
#  terms of the GNU Lesser General Public License as published by the Free
#  Software Foundation; either version 2.1 of the License, or (at your option)
#  any later version.
#
# Entries in this file show the compile time defaults. Local configuration
# should be created by either modifying this file, or by creating "drop-ins" in
# the timesyncd.conf.d/ subdirectory. The latter is generally recommended.
# Defaults can be restored by simply deleting this file and all drop-ins.
#
# See timesyncd.conf(5) for details.

[Time]
#NTP=
#FallbackNTP=0.debian.pool.ntp.org 1.debian.pool.ntp.org 2.debian.pool.ntp.org 3.debian.pool.ntp.org
#RootDistanceMaxSec=5
#PollIntervalMinSec=32
#PollIntervalMaxSec=2048
#ConnectionRetrySec=30
#SaveIntervalSec=60
```

# Interfaz lógico
---
Una **interfaz lógica** es una forma virtual de configurar una red que se basa en una interfaz física. Permite asignar múltiples direcciones IP a una sola tarjeta de red.
## Configurar un nuevo interfaz lógico

> [!WARNING] 
> Se necesitan permisos de superusuario

Crearlo.
```
ifconfig ens34:0 10.11.52.1/24
```

Activarlo.
```
 ifconfig ens34:0 up
```

Comprobar que está activado.
```
ifconfig
```

![[Pasted image 20240929131048.png]]
Apagarlo (si se desea).
```
ifconfig ens34:0 down
```
# Tablas de enrutamiento
---
## Ver rutas definidas en el sistema

```bash
netstat -rn
```

- `-r`: Muestra la tabla de enrutamiento
- `-n`: No resuelve nombres, solo muestra IPs.

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         10.11.48.1      0.0.0.0         UG        0 0          0 ens33
10.11.48.0      0.0.0.0         255.255.254.0   U         0 0          0 ens33
10.11.50.0      0.0.0.0         255.255.254.0   U         0 0          0 ens34
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 ens33
```

## Agregar y borrar rutas

> [!WARNING] 
> Se necesitan permisos de superusuario

```
route add -net <IP> netmask <mask> gw <gateway> dev <iface>
```

Queremos añadir a la tabla de enrutamiento la ruta a `10.11.51.0` por el iface `ens34`.

```
route -p add -net 10.11.51.0 netmask 255.255.255.0 dev ens34
```

- `-p`: Ruta persistente tras reiniciar el sistema.
- `-net`: El destino es una red.
- `netmask`: Especifica la máscara de red
- `dev` : Interfaz
- `gw` : Gateway

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         10.11.48.1      0.0.0.0         UG        0 0          0 ens33
10.11.48.0      0.0.0.0         255.255.254.0   U         0 0          0 ens33
10.11.50.0      0.0.0.0         255.255.254.0   U         0 0          0 ens34
10.11.51.0      0.0.0.0         255.255.255.0   U         0 0          0 ens34
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 ens33
```

Ahora vamos a borrar la ruta que acabamos de poner:

```
route del -net 10.11.51.0 netmask 255.255.255.0 dev ens34
```

# Identificar servicios no necesarios
---
## Enmascarar servicios

Enmascarando se bloquea completamente el servicio, evitando cualquier inicio hasta que se desenmascare.

```
systemctl mask <service>
```
## Desactivar servicios

Desactivando se permite que el servicio siga existiendo y se pueda iniciar manualmente.

```
systemctl disable <service>
```
## Servicios no necesarios

- `bluetooth.service`: Servicio de Bluetooth.
- `avahi-daemon.service`: Avahi permite detectar automáticamente los recursos de una red local y conectarse a ella. En términos generales se ocupa de asignar automáticamente una dirección IP incluso sin presencia de un servidor DHCP, hacer la función de DNS y crear una lista de los servicios a fin de acceder a ellos fácilmente.
- `modemmanager.service`: Es un servicio de systemd necesario para conexiones 2G/3G/4G.