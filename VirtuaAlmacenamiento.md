Ejercicio 1
===========

### ¿Cómo tienes instalado tu disco duro? ¿Usas particiones? ¿Volúmenes lógicos?

![captura1](https://dl.dropbox.com/s/iau319oubdwq15r/discoduro.png)

Ejercicio 2
===========

### Usar FUSE para acceder a recursos remotos como si fueran ficheros locales. Por ejemplo, sshfs para acceder a ficheros de una máquina virtual invitada o de la invitada al anfitrión.

Instalo sshfs tanto en el anfitrión como en la máquina virtual:

    sudo apt-get install sshfs
    
A continuación añado el usuario de la máquina virtual al grupo fuse:

    usermod -a -G fuse pedro
    
Ahora miro la ip de la máquina virtual para conectarme:

    ifconfig
    
La ip es 10.0.2.15 creamos carpetas en ambos lados y procedemos a la conexión

    sudo sshfs pedro@10.0.2.15:/home/pedro/carpeta /home/pedro/carpeta_anf

Tras poner el password del usuario, ya tenemos los archivos de carpeta en carpeta_anf.

Ejercicio 3
===========

### Crear imágenes con estos formatos (y otros que se encuentren tales como VMDK) y manipularlas a base de montarlas o con cualquier otra utilidad que se encuentre.

Utilizo los siguientes lineas de comando:

* Imgen raw: dd of=raw.img bs=1k seek=10240 count=0
* Imagen qcow2: qemu-img create -f qcow2 qcow2.qcow2 10M
* Imagen vmdk: qemu-img create -f vmdk vmdk.vmdk 10M

A continuación para poder montarlos primero los tranformo en un archivo loop, luego los formateo y a continuación los monto:

    sudo losetup -v -f vmdk.vmdk
    sudo mkfs.ext4 /dev/loop2
    sudo mount /dev/loop2 /mnt/imagenes

Todo esto es similar en las tres imágenes, exceptuando el número que acompaña al loop. Aquí se pueden ver las imágenes montadas:

![captura2](https://dl.dropbox.com/s/mqf23435yk0paoy/montadas.png)

Ejercicio 4
===========

### Crear uno o varios sistema de ficheros en bucle usando un formato que no sea habitual (xfs o btrfs) y comparar las prestaciones de entrada/salida entre sí y entre ellos y el sistema de ficheros en el que se encuentra, para comprobar el overhead que se añade mediante este sistema

Creo los dos archivos que vamos a utilizar:

    qemu-img create -f raw xfs.img 500M
    qemu-img create -f raw btrfs.img 500M

Y hago con ambos los pasos del ejercicio anterior:

    sudo losetup -v -f xfs.img
    sudo losetup -v -f btrfs.img
    sudo mkfs.xfs /dev/loop3
    sudo mkfs.btrfs /dev/loop4
    
Y los monto:
    
    sudo mount /dev/loop3 /mnt/imagenes
    sudo mount /dev/loop4 /mnt/imagenes

Ahora para comprobar el tiempo, creamos un archivo de 400MB:

    dd if=/dev/urandom of=archivo bs=100 count=4000000

Y comprobamos el tiempo copiando el archivo en ambos sistemas:
    
    sudo time cp archivo /mnt/imagenes/xfs
    sudo time cp archivo /mnt/imagenes/brtfs
  
![captura3](https://dl.dropbox.com/s/3jqgkrvfkyy5aud/transferencia.png)

Como se puede ver es más rápido en xfs que brtfs.

Ejercicio 5
===========

### Instalar ceph en tu sistema operativo.

Utilizo lo sugiente:

    sudo apt-get install ceph-mds
    
Ejercicio 6
===========

### Crear un dispositivo ceph usando BTRFS o XFS

Creamos los directorios donde se almacena la información ceph:

    mkdir -p /srv/ceph/{osd,mon,mds}

Y este es mi archivo de configuración:

    [global]
    auth cluster required = none
    auth service required = none
    auth client required = none
    auth supported = none
    log file = /var/log/ceph/$name.log
    pid file = /var/run/ceph/$name.pid
    [mon]
    mon data = /srv/ceph/mon/$name
    [mon.gpc]
    host = pedro-Lenovo-IdeaPad-U410
    mon addr = 127.0.0.1:6789
    [mds]
    [mds.gpc]
    host = pedro-Lenovo-IdeaPad-U410
    [osd]
    osd data = /srv/ceph/osd/$name
    osd journal = /srv/ceph/osd/$name/journal
    osd journal size = 1000
    [osd.0]
    host = pedro-Lenovo-IdeaPad-U410
    xfs devs = /dev/loop5
    
Creo el directorio a mano como dice el ejemplo:

     sudo mkdir /srv/ceph/osd/osd.0
     
Y creo el sistema de ficheros de objetos:

    sudo /sbin/mkcephfs -a -c /etc/ceph/ceph.conf
    
Comprobamos que funciona ceph:

![captura5](https://dl.dropbox.com/s/ro1u867638yt5vg/funcionaceph.png)

Al montar el sistema:

    sudo mount -t ceph pedro-Lenovo-IdeaPad-U410:/ /mnt/imagenes/ceph
    
Da el siguiente error:

![captura6](https://dl.dropbox.com/s/dnc55nj2zglpbjx/errorceph.png)

He visto que también lo tuviste tu: [Enlace](http://stackoverflow.com/questions/20553445/mounting-ceph-fails-with-mount-error-5-input-output-error?answertab=active#tab-top)

Ejercicio 7
===========

### Almacenar objetos y ver la forma de almacenar directorios completos usando ceph y rados.

    
