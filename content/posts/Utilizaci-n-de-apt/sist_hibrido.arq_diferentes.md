---
title: "Sistemas híbridos"
date: 2018-12-17T22:21:42+01:00
publishDate: 2018-12-19T22:21:42+01:00
author: "Paloma R. García"
images: []
draft: false
---
En el claud hacemos un sistema híblido y un sistema con varias arquitecturas. Debian con 64/Sid con i386. Después le damos la vuelta.

Para añadir una arquitectura adicional se usa el comando:
~~~
dpkg --add-architecture i386
~~~

Para ver la arquitectura de la máquina:
~~~
dpkg --print-architecture
~~~

Para ver las arquitecturas adicionales de una máquina:
~~~
dpkg --print-foreign-architecture
~~~



