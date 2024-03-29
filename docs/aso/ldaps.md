# LDAPs

## 1. Enunciado

Configurar el servidor LDAP para que utilice tanto el protocolo `ldaps://` como `ldap://` con certificados x509.

Configurar los clientes LDAP para que usen `ldaps://` por defecto.

## 2. Server

### 2.1 Requisitos

```shell
sudo apt install libldap-common
```

### 2.2 Certificados

Genero la clave privada:

```shell
sudo su -
cd /etc/ssl/private
openssl genrsa -aes128 -out server.key 2048
```

Le quito la passphrase:

```shell
openssl rsa -in server.key -out server.key
```

Genero el csr:

```shell
root@server:/etc/ssl/private# openssl req -new -days 3650 -key server.key -out server.csr
Ignoring -days; not generating a certificate
You are about to be asked to enter information that will be incorporated
into your certificate request.
What you are about to enter is what is called a Distinguished Name or a DN.
There are quite a few fields but you can leave some blank
For some fields there will be a default value,
If you enter '.', the field will be left blank.
-----
Country Name (2 letter code) [AU]:ES
State or Province Name (full name) [Some-State]:Sevilla
Locality Name (eg, city) []:Dos Hermanas
Organization Name (eg, company) [Internet Widgits Pty Ltd]:IES Gonzalo Nazareno
Organizational Unit Name (eg, section) []:ASIR
Common Name (e.g. server FQDN or YOUR name) []:server.adrianj.gonzalonazareno.org
Email Address []:adrjaro@gmail.com

Please enter the following 'extra' attributes
to be sent with your certificate request
A challenge password []:
An optional company name []:
```

Genero el crt:

```shell
openssl x509 -in server.csr -out server.crt -req -signkey server.key -days 3650
```

Muestro los ficheros generados:

```shell
root@server:/etc/ssl/private# ls -la
total 20
drwx------ 2 root root 4096 Mar  9 07:51 .
drwxr-xr-x 4 root root 4096 Dec 19 20:26 ..
-rw-r--r-- 1 root root 1424 Mar  9 07:51 server.crt
-rw-r--r-- 1 root root 1106 Mar  9 07:50 server.csr
-rw------- 1 root root 1679 Mar  8 00:45 server.key
```

Copio los ficheros al directorio correspondiente:

```shell
cp /etc/ssl/private/server.key /etc/ssl/private/server.crt /etc/ssl/certs/ca-certificates.crt /etc/ldap/sasl2/
```

Modifico propietarios:

```shell
chown openldap:openldap /etc/ldap/sasl2/server.key /etc/ldap/sasl2/server.crt /etc/ldap/sasl2/ca-certificates.crt
```

### 2.3 Configuración certificados

```shell
cd
nano mod_ssl.ldif
```

```shell
dn: cn=config
changetype: modify
add: olcTLSCACertificateFile
olcTLSCACertificateFile: /etc/ldap/sasl2/ca-certificates.crt
-
replace: olcTLSCertificateFile
olcTLSCertificateFile: /etc/ldap/sasl2/server.crt
-
replace: olcTLSCertificateKeyFile
olcTLSCertificateKeyFile: /etc/ldap/sasl2/server.key
```

La aplico:

```shell
ldapmodify -Y EXTERNAL -H ldapi:/// -f mod_ssl.ldif
```

Compruebo que se ha aplicado:

```shell
slapcat -b cn=config
```

![certificadosaplicados](https://i.imgur.com/I5s3MNw.png)

Salgo de root:

```shell
exit
```

### 2.4 Configuración LDAP

Dejo la sección de TLS así:

```shell
sudo nano /etc/ldap/ldap.conf
```

```shell
# TLS certificates (needed for GnuTLS)
#TLS_CACERT	/etc/ssl/certs/ca-certificates.crt
TLS_REQCERT never
```

Reemplazo la siguiente línea:

```shell
sudo nano /etc/default/slapd
```

```shell
SLAPD_SERVICES="ldap:/// ldapi:/// ldaps:///"
```

Reinicio:

```shell
sudo systemctl restart slapd
```

### 2.5 Comprobaciones

Puerto de LDAPs abierto:

```shell
sudo ss -tulpn | grep 636
```

![ldapspuerto](https://i.imgur.com/WXkopWr.png)

Pruebo que una consulta mediante `ldaps://` y sin root funciona:

```shell
ldapsearch -x -b "dc=adrianj,dc=gonzalonazareno,dc=org" -H ldaps://
```

![ldapsconsulta](https://i.imgur.com/7uADl24.png)

## 3. Clientedebian

### 3.1 Requisitos

```shell
sudo apt install libldap-common
```

### 3.2 Configuración

Dejo `/etc/ldap/ldap.conf` así:

```shell
sudo nano /etc/ldap/ldap.conf
```

```shell
#
# LDAP Defaults
#

# See ldap.conf(5) for details
# This file should be world readable but not world writable.

BASE	dc=adrianj,dc=gonzalonazareno,dc=org
URI	ldaps://server.adrianj.gonzalonazareno.org:636

#SIZELIMIT	12
#TIMELIMIT	15
#DEREF	        never

# TLS certificates (needed for GnuTLS)
#TLS_CACERT	/etc/ssl/certs/ca-certificates.crt
TLS_REQCERT never
```

En `/etc/nslcd.conf` dejo la URI así:

```shell
sudo nano /etc/nslcd.conf
```

```shell
uri ldaps://server.adrianj.gonzalonazareno.org/
```

Y la sección de SSL así:

```shell
# SSL options
#ssl start_tls
tls_reqcert never
#tls_cacertfile /etc/ssl/certs/ca-certificates.crt
```

Reinicio:

```shell
sudo systemctl restart nslcd
```

### 3.3 Comprobaciones

Pruebo que una consulta mediante `ldaps://` y sin root funciona:

```shell
ldapsearch -x -b "dc=adrianj,dc=gonzalonazareno,dc=org" "objectclass=posixAccount"
```

![ldapsconsultacliente](https://i.imgur.com/C3uCbGI.png)

!!! info

    Recordemos que no he escrito `ldaps://` en la consulta porque ya no es necesario. Las consultas se autocompletan con la información de `/etc/ldap/ldap.conf`






