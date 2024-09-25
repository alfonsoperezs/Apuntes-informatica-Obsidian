# Fichero interfaces
---
En el fichero /etc/network/interfaces es donde configuramos la red de nuestros servidores. 

```bash
cat /etc/network/interfaces
```

![](images/etc-interfaces.png)

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
initrd-root-device.target     static   -
initrd-root-fs.target         static   -
initrd-switch-root.target     static   -
initrd-usr-fs.target          static   -
initrd.target                 static   -
integritysetup-pre.target     static   -
integritysetup.target         static   -
kexec.target                  disabled disabled
local-fs-pre.target           static   -
local-fs.target               static   -
multi-user.target             static   -
network-online.target         static   -
network-pre.target            static   -
network.target                static   -
nss-lookup.target             static   -
nss-user-lookup.target        static   -
```

# Services
---
Un servicio es un programa que se ejecuta en segundo plano, fuera del control interactivo de los usuarios del sistema, ya que carecen de una interfaz.

## Listar services

```bash
systemctl list-unit-files --type=target
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

