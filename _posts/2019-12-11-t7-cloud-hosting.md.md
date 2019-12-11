---
title: "Tarea 7 Cloud: Hosting"
---

# Paso 0: preparativos
## Instalar/configurar proftpd
* Añadir el repositorio EPEL
No lo hago, porque ya lo tengo
* Actualizamos los paquetes (por buenas prácticas)
```
sudo yum update
```
* Instalamos el servidor FTP
```
sudo yum install proftpd
```
* Añadimos las reglas de firewall para permitir la comunicación FTP
```
firewall-cmd --permanent --add-port=21/tcp
```
* Reiniciamos el servicio de firewalld
* 







# Paso 1: Creación del usuario







# Paso 2: VirtualHost + Document Root + Default Root






# Paso 3: Crear CNAME para VH







# Paso 4: Crear usuario BD y la BD
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTM5OTQ3OTM4NCwtMTgyNDc1NDY0MiwxNj
M3OTIwNDYxLC0xNDYzODMxOTksMTkyODk1MTM4MSwtMTUxNDQy
NjYyMCwtMTExNTQwODk2NV19
-->