---
title: "Creación del cliente de PostgreSQL"
author: "Paloma R. García"
images: []
draft: false
---
**Prueba desde un cliente remoto del intérprete de comandos de Postgres**
En este punto se van a establecer los pasos a seguir para realizar una conexión de un cliente de Postgres de forma remota. Este ejercicio se va a realizar sobre un sistema operativo Debian 10.

### Instalación del cliente de Postgres
El paquete que se necesita es el siguiente:
~~~
$ sudo apt install postgresql-client
~~~

### Conexión entre cliente y servidor
Desde la terminal, se utiliza el comando psql con las siguientes opciones:
- h: para indicar la IP del servidor de Postgres.
- U: para indicar el usuario desde el que se va  a acceder a la base de datos.
- d: para indicar el nombre de la base de datos a la que se va a acceder.
~~~
$ psql -h 172.22.9.121 -U guarderia -d guarderia_db
~~~

~~~
$ psql -h 172.22.9.121 -U guarderia -d guarderia_db
Contraseña para usuario guarderia: 
psql (11.5 (Debian 11.5-1+deb10u1))
conexión SSL (protocolo: TLSv1.3, cifrado: TLS_AES_256_GCM_SHA384, bits: 256, compresión: desactivado)
Digite «help» para obtener ayuda.

guarderia_db=>


guarderia_db=> \d
         Listado de relaciones
 Esquema |  Nombre  | Tipo  |   Dueño   
---------+----------+-------+-----------
 public  | mascotas | tabla | guarderia
 public  | pagos    | tabla | guarderia
 public  | personas | tabla | guarderia
(3 filas)
~~~

