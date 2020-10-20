---
title: "Tarea: Creación de un sistema automatizado de instalación"
---

# Enunciado

Implementa un sistema de instalación con PXE/TFTP que realice una instalación completa de un sistema Debian Buster de forma totalmente desatendida, pasándole todos los parámetros necesarios por "preseeding"


# Planteamiento/Organización

1 VMs en red interna Vagrant

1 SERVER (imagen debian buster + fichero preseeding + server PXE + server DHCP + TFTP server)

2 CLIENT (booteo con PXE, pedirá una IP al DHCP, se instalará el sistema localmente a través del servidor) (MÁQUINA VACÍA VIRTUALBOX PARA QUE NO INSTALE NADA EN EL DISCO DURO)

(probar a poner por PXE el cliente en modo bridge, y que acceda al PXE del gonzalo nazareno) (no se ha podido porque no había imágenes booteables, no funciona el PXE de aquí)

https://wiki.debian.org/PXEBootInstall

# Desarrollo

## 1. Configuración del servidor DHCP (servidor)

```
sudo apt install isc-dhcp-server
```

En `/etc/default/isc-dhcp-server`
```
INTERFACESv4="eth1"
```
Decimos por qué interfaces servimos peticiones DHCP


En `/etc/dhcp/dhcpd.conf` (propia configuración)
```
default-lease-time 600;
max-lease-time 7200;

allow booting;
allow bootp;

# The next paragraph needs to be modified to fit your case
subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.3 192.168.0.10;
  option broadcast-address 192.168.0.255;
# the gateway address which can be different
# (access to the internet for instance)
#  option routers 192.168.1.1;
# indicate the dns you want to use
#  option domain-name-servers 192.168.1.3;
}

group {
  next-server 192.168.0.2;
  host tftpclient {
# tftp client hardware address
  hardware ethernet  08:00:27:3a:73:29;
  filename "pxelinux.0";
 }
}
```

Reiniciar servicio para que tenga en cuenta la configuración
```
sudo systemctl restart isc-dhcp-server
```
Comprobar que se está ejecutando
```
sudo systemctl status isc-dhcp-server
```

## 2. Configuración del servidor TFTP (servidor)

```
sudo apt install tftpd-hpa
```

> https://www.debian.org/releases/jessie/amd64/ch04s05.html.en
> Importante enlace para que funcione el booteo desde el cliente, por la configuración del DHCP básicamente

## 3. Proporcionar la imagen de instalación (servidor)

Nos posicionamos en el directorio de tftp
```
cd /srv/tftp/
```

Aquí, obtenemos la imagen de instalación por red
```
sudo wget http://ftp.nl.debian.org/debian/dists/buster/main/installer-amd64/current/images/netboot/netboot.tar.gz
```

Descomprimimos y borramos el comprimido original para mayor limpieza
```
sudo tar -xzf netboot.tar.gz
sudo rm netboot.tar.gz
```

Tenemos la siguiente estructura
```
drwxrwxr-x 3 root root 4096 Oct 16 09:01 .
drwxr-xr-x 3 root root 4096 Oct 16 08:30 ..
drwxrwxr-x 3 root root 4096 Sep 20 23:11 debian-installer
lrwxrwxrwx 1 root root   47 Sep 20 23:11 ldlinux.c32 -> debian-installer/amd64/boot-screens/ldlinux.c32
lrwxrwxrwx 1 root root   33 Sep 20 23:11 pxelinux.0 -> debian-installer/amd64/pxelinux.0
lrwxrwxrwx 1 root root   35 Sep 20 23:11 pxelinux.cfg -> debian-installer/amd64/pxelinux.cfg
-rw-rw-r-- 1 root root   63 Sep 20 23:11 version.info
```

Reiniciamos el servicio
```
sudo systemctl restart tftpd-hpa.service
```









(decir config de cliente)