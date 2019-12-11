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
En el fichero `local_settings.py` 


## Ejecutamos el server web local
```
python manage.py runserver 0.0.0.0:8000
```








# Paso 2: personalización de la web
## Cambiar nombre de la página

## Cambiar tema

## Añadir artículo + imagen






# Paso 3: guardado en Github





# Paso 4: despliegue en producción




<!--stackedit_data:
eyJoaXN0b3J5IjpbLTcyMzUzMDMxNiwxMTIxOTY4MTIsLTc1ND
E3Njg5MywtNzM4MjE2Mjk2LC0xNjQ3MTI0Njk1LC02MDI1NzE5
ODEsLTE5OTEwMjM1MzUsLTIwNjQ5MTc0MzQsNzYzODE2NTQwLD
E3NjQ2MTE3MzgsLTMwODM5MzczOSwtMTcyODA0NzgzMCwyMTE0
MjExNjE5LDE5MTEwMTg1NDFdfQ==
-->