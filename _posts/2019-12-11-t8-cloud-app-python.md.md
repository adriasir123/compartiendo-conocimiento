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

```



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
eyJoaXN0b3J5IjpbNDk5NTk0MTUxLDExMjE5NjgxMiwtNzU0MT
c2ODkzLC03MzgyMTYyOTYsLTE2NDcxMjQ2OTUsLTYwMjU3MTk4
MSwtMTk5MTAyMzUzNSwtMjA2NDkxNzQzNCw3NjM4MTY1NDAsMT
c2NDYxMTczOCwtMzA4MzkzNzM5LC0xNzI4MDQ3ODMwLDIxMTQy
MTE2MTksMTkxMTAxODU0MV19
-->