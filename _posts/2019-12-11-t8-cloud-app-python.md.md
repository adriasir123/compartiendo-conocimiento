---
title: "Tarea 8 Cloud:  Instalación de app python (Mezzanine)"
---

# Paso 1: instalación en desarrollo con entorno virtual
## Instalar python...etc
Instalamos todos los paquetes necesarios
```
sudo apt install python3 python3-venv python3-virtualenv virtualenv
```
## Creamos el entorno virtual
```
python3 -m venv mezzanine-pyenv
```
## Lo activamos
```
source mezzanine-pyenv/bin/activate
```
## Instalando Mezzanine
```
pip install mezzanine
```
## Creamos el proyecto
```
mezzanine-project my_mezzanine
```
Nos movemos dentro de ese directorio
```
cd my_mezzanine
```
## Creamos la base de datos
```
python manage.py createdb
```
> Durante la creación nos pide un usuario y contraseña. En mi caso, ha sido "Usuario: vagrant" "Contraseña: 1234".
> Pero, ¿qué es esta cuenta que hemos configurado?
> Pues es simplemente la cuenta que se usa a la hora de acceder a la zona de administración de la página web. 
> Es importante que no confundamos esta cuenta como si fuese la cuenta que estuviéramos creando para autenticarnos contra la base de datos, porque sqlite no tiene el concepto de usuarios y contraseñas para el acceso (usa los permisos del sistema) 


## Permitimos la conexión a la app web
En el fichero `local_settings.py`, tenemos que modificar la siguiente línea
```
ALLOWED_HOSTS = ["localhost", "127.0.0.1", "::1"]
```
Para quede de la siguiente manera
```
ALLOWED_HOSTS = ["localhost", "127.0.0.1", "::1", "172.22.0.245"]
```
Lo que estamos haciendo con esto, es permitir el acceso a la aplicación python, a la máquina donde nos queremos conectar (en mi caso es una máquina virtual vagrant)

## Ejecutamos el servidor web
```
python manage.py runserver 0.0.0.0:8000
```
> En mi caso lo abro permitiendo las conexiones desde cualquier IP, porque mi entorno de desarrollo es una VM vagrant

## Mostramos la web
![](https://i.imgur.com/x5DsdvA.png)
## Accediendo a la parte de administración
Para ello, tendremos que acceder a una URL parecida a la siguiente  
(digo parecida, porque simplemente lo que cambiaría sería la IP)
```
http://192.168.1.104:8000/admin/
```
Una vez dentro, la parte de administración sería tal que así
![](https://i.imgur.com/3JGcIZa.png)





# Paso 2: personalización de la web

## Cambiar nombre de la página
Dentro de la zona de administración, tendremos que irnos a "Site -> Settings -> Site -> Site Title". Una vez aquí, podremos cambiar el nombre de la web al que queramos:
![](https://i.imgur.com/CussH1y.png)
Cuando guardemos, y volvamos a la web principal, veremos que el nombre de la web se cambió correctamente
![](https://i.imgur.com/xDdXVKc.png)
## Añadir artículo + imagen



## Cambiar tema





















# Paso 3: guardado en Github





# Paso 4: despliegue en producción




<!--stackedit_data:
eyJoaXN0b3J5IjpbMTYwODc3MDI0LC04NDk5NzkwMSwzNDU5Mz
YwMCwtMTQyNzQ2NywtODU1MjE3NTM4LC0xNjY1Njg1NzcsNjk5
MzE0NTU3LC05NDEyMTI3NjcsMTY4NjQ4NzMwNSwxMTIxOTY4MT
IsLTc1NDE3Njg5MywtNzM4MjE2Mjk2LC0xNjQ3MTI0Njk1LC02
MDI1NzE5ODEsLTE5OTEwMjM1MzUsLTIwNjQ5MTc0MzQsNzYzOD
E2NTQwLDE3NjQ2MTE3MzgsLTMwODM5MzczOSwtMTcyODA0Nzgz
MF19
-->