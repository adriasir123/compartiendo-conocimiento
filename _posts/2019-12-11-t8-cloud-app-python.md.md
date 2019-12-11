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
>
## Mostramos la web
![](https://i.imgur.com/x5DsdvA.png)
## Accediendo a la parte de administración








# Paso 2: personalización de la web
## Cambiar nombre de la página

## Cambiar tema

## Añadir artículo + imagen













# Paso 3: guardado en Github





# Paso 4: despliegue en producción




<!--stackedit_data:
eyJoaXN0b3J5IjpbMTg5MzUyNjg2OCwtMTQyNzQ2NywtODU1Mj
E3NTM4LC0xNjY1Njg1NzcsNjk5MzE0NTU3LC05NDEyMTI3Njcs
MTY4NjQ4NzMwNSwxMTIxOTY4MTIsLTc1NDE3Njg5MywtNzM4Mj
E2Mjk2LC0xNjQ3MTI0Njk1LC02MDI1NzE5ODEsLTE5OTEwMjM1
MzUsLTIwNjQ5MTc0MzQsNzYzODE2NTQwLDE3NjQ2MTE3MzgsLT
MwODM5MzczOSwtMTcyODA0NzgzMCwyMTE0MjExNjE5LDE5MTEw
MTg1NDFdfQ==
-->