---
title: "Gestión de almacenamiento"
author: "Paloma R. García"
images: []
draft: false
---

Al diseñar una política de almacenamiento de la información hay que tener en cuenta el rendimiento, disponibilidad y accesibilidad.


### Almacenamientos secundarios:
- Sist magnéticos
- Sist ópticos
- Sist de almacenamiento sólido


### En la nube:
Estos tipos están creciendo. Ventajas: actualización a tiempo real, acceso en cualquier lugar y bajos costes. Inconvenientes: seguridad y dependencia.


### Almacenamiento redundante, RAID:
Conjunto de discos entre los que se distribuyen o se replican datos. 
Ventajas:

- Mayor integridad
- Mayor tolerancia a fallos
- Mayor rendimiento
- Mayor capacidad

### Tipos de RAID:
- Por software. 
- Por hardware. El software solo distingue un solo disco y es el hardware el que controla.
- Híbrido.

**RAID 0 – Striping o división**
El raid reparte los datos en varios discos duros, sin redundancia de datos. Aumenta la velocidad. Este tipo de RAID es bueno para aumentar la capacidad de los discos y el rendimiento, ya que se suman los discos usados y se utilizan como si fueran 1. 


**RAID 1 – Mirroring o espejo**
Se escribe la misma información en dos discos, o en tres si se tiene 3 discos, etc. La tolerancia a fallos es n-1, según el número de discos que tengas.
Si falla el sistema sigue en marcha empleando los otros discos. 

**RAID 5 – Mirroring + paridad distribuida**
	Paridad: los datos de paridad se utilizan para conseguir redundancia de datos utilizando las operacones XOR, de esta forma, mediante esta operación, se pueden obtener los datos porque uno de los discos no guarda los datos reales, sino los datos “calculados”.

La información de los usuarios se guarda por bloques en distintos discos y gracias a la información de paridad se puede reestablecer la pérdida. La paridad del disco 1 y 2 se guarda en el disco 3 y así sucesivamente. 

>Disco de reserva: un disco que se añade al RAID, que no funciona pero que si uno falla, este toma su lugar. 

Con mdadm a partir de dispositivos de bloques vamos a poder construir RAIDs. 


