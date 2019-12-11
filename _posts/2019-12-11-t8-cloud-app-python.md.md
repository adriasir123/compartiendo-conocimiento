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










# Paso 2: personalización de la web
## Cambiar nombre de la página

## Cambiar tema

## Añadir artículo + imagen






# Paso 3: guardado en Github





# Paso 4: despliegue en producción




<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2NDcxMjQ2OTUsLTYwMjU3MTk4MSwtMT
k5MTAyMzUzNSwtMjA2NDkxNzQzNCw3NjM4MTY1NDAsMTc2NDYx
MTczOCwtMzA4MzkzNzM5LC0xNzI4MDQ3ODMwLDIxMTQyMTE2MT
ksMTkxMTAxODU0MV19
-->