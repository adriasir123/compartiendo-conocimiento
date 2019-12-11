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
* Añadimos las reglas de firewall para permitir la comunicación
```
firewall-cmd --permanent --add-port=21/tcp
```








# Paso 1: Creación del usuario







# Paso 2: VirtualHost + Document Root + Default Root






# Paso 3: Crear CNAME para VH







# Paso 4: Crear usuario BD y la BD
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0NTYxOTk4NDcsLTE4MjQ3NTQ2NDIsMT
YzNzkyMDQ2MSwtMTQ2MzgzMTk5LDE5Mjg5NTEzODEsLTE1MTQ0
MjY2MjAsLTExMTU0MDg5NjVdfQ==
-->