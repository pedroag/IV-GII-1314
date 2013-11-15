Ejercicio 1
-----------

Ejecuto el comando:

    sudo apt-get install lxc
    

Ejercicio 2
-----------

La interfaz puente que se ha creado la veo con:

     brctl show
     
Y la salida es:

![captura1](https://dl.dropbox.com/s/bevwg3vjjm14lpv/interfaces-puente.png)

Esto se crean automaticamente para que el contenedor al conectarse a estos puentes, lo hagan como si estuvieran conectados
al router.

Ejercicio 3
-----------

a)

Lo creo con:

    sudo lxc-create -t debian -n cont-debian

![captura2](https://dl.dropbox.com/s/6zj4rckzer01p4c/contenedor-debian.png)

Lo ejecuto con:

    lxc-start -n cont-debian
    
Ya dentro me logueo como root:

![captura3](https://dl.dropbox.com/s/ermtxzv1mwg6w3y/cont-debian-ejecuta.png)

b)

Lo instalo de la misma manera que el anterior:

    sudo lxc-create -t fedora -n cont-fedora

Pero me da un error y me pide que instale yum y curl. Lo instalo:

    sudo apt-get install curl yum
    
El error se resuelve, pero me salen errores nuevos y no consigo instalarlo

Ejercicio 4
-----------

a)

Primero tengo que ser super usuario:

    sudo su

Y a continuación instalo lxc Web Panel:

    wget http://lxc-webpanel.github.io/tools/install.sh -O - | bash
    

    



