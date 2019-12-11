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
Para ello, tendremos que acceder a una URL parecida a la siguiente `
```
http://192.168.1.104:8000/admin/
```




# Paso 2: personalización de la web
## Cambiar nombre de la página

## Cambiar tema

## Añadir artículo + imagen













# Paso 3: guardado en Github





# Paso 4: despliegue en producción




<!--stackedit_data:
eyJoaXN0b3J5IjpbODU0NDgwMjU1LDM0NTkzNjAwLC0xNDI3ND
Y3LC04NTUyMTc1MzgsLTE2NjU2ODU3Nyw2OTkzMTQ1NTcsLTk0
MTIxMjc2NywxNjg2NDg3MzA1LDExMjE5NjgxMiwtNzU0MTc2OD
kzLC03MzgyMTYyOTYsLTE2NDcxMjQ2OTUsLTYwMjU3MTk4MSwt
MTk5MTAyMzUzNSwtMjA2NDkxNzQzNCw3NjM4MTY1NDAsMTc2ND
YxMTczOCwtMzA4MzkzNzM5LC0xNzI4MDQ3ODMwLDIxMTQyMTE2
MTldfQ==
-->