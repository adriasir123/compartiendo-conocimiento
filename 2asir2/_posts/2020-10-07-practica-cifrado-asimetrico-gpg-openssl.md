---
title: "Práctica: Cifrado asimétrico con gpg y openssl"
---

# **Tarea 1**: Generación de claves 

## 1. Genera un par de claves (pública y privada). ¿En que directorio se guardan las claves de un usuario?

```
gpg --gen-key
```
```
gpg (GnuPG) 2.2.12; Copyright (C) 2018 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

gpg: directory '/home/vagrant/.gnupg' created
gpg: keybox '/home/vagrant/.gnupg/pubring.kbx' created
Note: Use "gpg --full-generate-key" for a full featured key generation dialog.

GnuPG needs to construct a user ID to identify your key.

Real name: Adrián Jaramillo Rodríguez
Email address: adristudy@gmail.com
You are using the 'utf-8' character set.
You selected this USER-ID:
    "Adrián Jaramillo Rodríguez <adristudy@gmail.com>"

Change (N)ame, (E)mail, or (O)kay/(Q)uit? o
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
gpg: /home/vagrant/.gnupg/trustdb.gpg: trustdb created
gpg: key 7E0C48CBBC17F36F marked as ultimately trusted
gpg: directory '/home/vagrant/.gnupg/openpgp-revocs.d' created
gpg: revocation certificate stored as '/home/vagrant/.gnupg/openpgp-revocs.d/C34C081A07CA71291F82BFD67E0C48CBBC17F36F.rev'
public and secret key created and signed.

pub   rsa3072 2020-10-08 [SC] [expires: 2022-10-08]
      C34C081A07CA71291F82BFD67E0C48CBBC17F36F
uid                      Adrián Jaramillo Rodríguez <adristudy@gmail.com>
sub   rsa3072 2020-10-08 [E] [expires: 2022-10-08]
```

decir en qué directorio se guardan las claves



























# **Tarea 2**: Importar / exportar clave pública 
 




# **Tarea 3**: Cifrado asimétrico con claves públicas 





# **Tarea 4**: Exportar clave a un servidor público de claves PGP




# **Tarea 5**: Cifrado asimétrico con openssl 






