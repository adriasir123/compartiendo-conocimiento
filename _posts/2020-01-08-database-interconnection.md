---
title: "Práctica 4 BD: Interconexión de Servidores de Bases de Datos"
---

# Enunciado 

**Los servidores enlazados siempre tendrán que estar instalados en máquinas diferentes**

En ésta práctica veremos varias formas de crear un enlace entre distintos servidores de bases de datos

Tipos de enlace a crear:

* 2 servidores de bases de datos ORACLE
      
* 2 servidores de bases de datos PostgreSQL
      
* 1 servidor ORACLE y 1 PostgreSQL/MySQL empleando Heterogeneous Services
      
En todos ellos, es necesario explicar la configuración necesaria para ambos extremos y demostrar su funcionamiento



# Registro de acciones previas en las máquinas
## Oracle1



## Oracle2



## PostgreSQL1

```
sudo apt-get install postgresql-11
sudo adduser postgres1_user
CREATE USER postgres1_user WITH PASSWORD '1234';
CREATE DATABASE postgres1_db OWNER postgres1_user;
```

Tabla insertada
```
CREATE TABLE table1(
   id serial PRIMARY KEY,
   name VARCHAR (50),
   desc VARCHAR (50)
);
```

Datos insertados
```
INSERT INTO table1 VALUES (1, 'Bird', 'Has wings');
```



/etc/postgresql/11/main/postgresql.conf
(cambiar las listen_addresses a asterisco)

​ /etc/postgresql/11/main/pg_hba.conf
(añadir la siguiente línea)
```
host all all 0.0.0.0/0 md5
/etc/init.d/postgresql restart
```
Al final se reinicia postgre





## PostgreSQL2

```
sudo apt-get install postgresql-11
sudo adduser postgres2_user
CREATE USER postgres2_user WITH PASSWORD '1234';
CREATE DATABASE postgres2_db OWNER postgres2_user;
```

Tabla insertada
```
CREATE TABLE table2(
   id serial PRIMARY KEY,
   name VARCHAR (50),
   desc VARCHAR (50)
);
```

Datos insertados
```
INSERT INTO table2 VALUES (1, 'Dog', 'Has legs');
```



/etc/postgresql/11/main/postgresql.conf
(cambiar las listen_addresses a asterisco)

​ /etc/postgresql/11/main/pg_hba.conf
(añadir la siguiente línea)
```
host all all 0.0.0.0/0 md5
/etc/init.d/postgresql restart
```
Al final se reinicia postgre







# Enlace ORACLE - ORACLE
















# Enlace PostgreSQL - PostgreSQL













# Enlace ORACLE - PostgreSQL

