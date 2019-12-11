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
## Añadir post con imagen
* Dentro de la zona de administración, tendremos que irnos a "Content -> Blog posts -> Add blog post". Una vez aquí, simplemente rellenaremos los campos necesarios, y crearemos el post.
* Cuando lo tengamos creado, nos aparecerá el nuevo post en la lista general de posts
![](https://i.imgur.com/2LI2L2u.png)* Para ver el post directamente en la web principal, la manera más sencilla y rápida sería hacer click en "View on site". Nuestro post ya terminado, quedaría tal que así:
![](https://i.imgur.com/N1DUceg.png)








# Paso 3: guardado en Github
##








# Paso 4: despliegue en producción




<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1OTc0OTM4MzYsOTc2MTYxOTE0LC0xMT
U2Njk3MTQ4LDgxNzUwOTQwMywtMTI2MjA5Mzg4NiwzNzIxMzIw
MTAsLTg0OTk3OTAxLDM0NTkzNjAwLC0xNDI3NDY3LC04NTUyMT
c1MzgsLTE2NjU2ODU3Nyw2OTkzMTQ1NTcsLTk0MTIxMjc2Nywx
Njg2NDg3MzA1LDExMjE5NjgxMiwtNzU0MTc2ODkzLC03MzgyMT
YyOTYsLTE2NDcxMjQ2OTUsLTYwMjU3MTk4MSwtMTk5MTAyMzUz
NV19
-->