Ejercicio 1
-----------

En primer lugar creo el espacio de nombre:
  
    sudo unshare -m /bin/bash
    
Y a continuación monto la imágen:
    
    mount -o loop prueba.iso /mnt/disk
    
Ejercicio 2
-----------

Para mostrar los puentes utilizo:

    brctl show
    
Como no he creado ninguno, no sale nada.

A continuacíon escribro los pasos para crear uno:

    brctl addbr puente-prueba         //Con esto lo creo
    brctl addif puente-prueba eth0    //Le asigno la interfaz eth0
    
Y esta es la salida de brctl show:

![captura1](https://dl.dropbox.com/s/okgr35czvi3ipv9/Captura%20de%20pantalla%20de%202013-11-04%2000%3A07%3A04.png)

Ejercicio 3
-----------

a) Creo un sistema con la orden explicada en los apuntes de clase:

    sudo debootstrap --arch=i386 quantal /home/jaulas/quantal/ http://archive.ubuntu.com/ubuntu

En este caso utilizo infraestructura de 32 bits.

b) Parecido al apartado anterior:

    sudo rinse --arch=i386 --distribution fedora-core-6 --directory /home/jaulas/fedora
    
Ejercicio 4
-----------

Como en el ejercicio anterior:

    sudo debootstrap --arch=i386 wheezy /home/jaulas/debian http://ftp.debian.org/debian/

y como ejemplo instalo python

    apt-get install python
    
![captura2](https://dl.dropbox.com/s/dyxu8lgnhufjl7h/Captura%20de%20pantalla%20de%202013-11-04%2013%3A04%3A43.png)
    
