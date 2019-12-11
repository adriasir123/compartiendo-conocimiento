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
## Mostramos la web
![](https://i.imgur.com/x5DsdvA.png)



# Paso 2: personalización de la web
## Cambiar nombre de la página

## Cambiar tema

## Añadir artículo + imagen













# Paso 3: guardado en Github





# Paso 4: despliegue en producción




<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2NjU2ODU3Nyw2OTkzMTQ1NTcsLTk0MT
IxMjc2NywxNjg2NDg3MzA1LDExMjE5NjgxMiwtNzU0MTc2ODkz
LC03MzgyMTYyOTYsLTE2NDcxMjQ2OTUsLTYwMjU3MTk4MSwtMT
k5MTAyMzUzNSwtMjA2NDkxNzQzNCw3NjM4MTY1NDAsMTc2NDYx
MTczOCwtMzA4MzkzNzM5LC0xNzI4MDQ3ODMwLDIxMTQyMTE2MT
ksMTkxMTAxODU0MV19
-->