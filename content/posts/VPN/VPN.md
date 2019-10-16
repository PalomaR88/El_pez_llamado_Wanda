---
title: "VPN"
author: "Paloma R. García"
images: []
draft: false
---
1. Genera una clave privada RSA 4096
Se crea una clave privada con openssl. Primero, como root, creamos una clave con el siguiente comando:
~~~
root@coatlicue:/home/paloma# openssl genrsa 4096 > /etc/ssl/private/coatlicue.palomaGarcia.key
~~~


2. Genera una solicitud de firma de certificado (fichero CSR) y súbelo a gestiona

Una vez creada la clave, hay que crear un fichero csr para que sea firmado por la CA Gonzalo Nazareno:

~~~
root@coatlicue:/home/paloma# openssl req -new -key /etc/ssl/private/coatlicue.palomaGarcia.key -out /root/coatlicue.palomaGarcia.csr
~~~

Teniendo ya el fichero, se envía a la entidad certificadora, dentro del menú utilidades de la aplicación gestiona.


3. Instala y configura apropiadamente el cliente openvpn y muestra los registros (logs) del sistema que demuestren que se ha establecido una conexión.

Se comienza instalando el paquete openvpn:
~~~
paloma@coatlicue:~$ sudo apt install openvpn
~~~

Se crea el fichero /etc/openvpn/openvpn.conf con la siguiente configuración:
~~~
dev tun
remote sputnik.gonzalonazareno.org
ifconfig 172.23.0.0 255.255.255.0
pull
proto tcp-client
tls-client
remote-cert-tls server
ca /etc/ssl/certs/gonzalonazareno.pem 
cert /etc/openvpn/coatlicue-palomaGarcia.crt
key /etc/ssl/private/coatlicue-palomaGarcia.key 
comp-lzo
keepalive 10 60
log /var/log/openvpn-sputnik.log
verb 1
~~~

Se reinicia openvpn y se comprueba si se ha creado el tunel:
~~~
paloma@coatlicue:~$ systemctl start openvpn.service
paloma@coatlicue:~$ ip r
default via 192.168.43.100 dev wlp1s0 proto dhcp metric 600 
169.254.0.0/16 dev wlp1s0 scope link metric 1000 
172.22.0.0/16 via 172.23.0.65 dev tun0 
172.23.0.1 via 172.23.0.65 dev tun0 
172.23.0.65 dev tun0 proto kernel scope link src 172.23.0.66 
192.168.43.0/24 dev wlp1s0 proto kernel scope link src 192.168.43.247 metric 600 
~~~

Es recomendable no dejar levantado el túnel VPN si no se está usando y levantarlo cuando sea necesario. Para ello:
~~~
systemctl disable openvpn.service
systemctl start openvpn.service
~~~

Por último, se recomienda actualizar el fichero /etc/hosts con la resolución estática de las máquinas.


4. Cuando hayas establecido la conexión VPN tendrás acceso a la red 172.22.0.0/16 a través de un túnel SSL. Compruébalo haciendo ping a 172.22.0.1
~~~
paloma@coatlicue:~$ ping jupiter
PING jupiter (172.22.222.1) 56(84) bytes of data.
64 bytes from jupiter (172.22.222.1): icmp_seq=1 ttl=62 time=227 ms
64 bytes from jupiter (172.22.222.1): icmp_seq=2 ttl=62 time=185 ms
64 bytes from jupiter (172.22.222.1): icmp_seq=3 ttl=62 time=207 ms
~~~

