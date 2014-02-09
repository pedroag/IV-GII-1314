Ejercicio 1
===========

### Instalar los paquetes necesarios para usar KVM. Se pueden seguir estas instrucciones. Ya lo hicimos en el primer tema, pero volver a comprobar si nuestro sistema está preparado para ejecutarlo o hay que conformarse con la paravirtualización.

Ejecuto el comando:

    kvm-ok

Y la salida es:

    INFO: /dev/kvm exists
    KVM acceleration can be used
    
Por lo tanto, está instalado.

Ejercicio 2
===========

### 1.Crear varias máquinas virtuales con algún sistema operativo libre, Linux o BSD. Si se quieren distribuciones que ocupen poco espacio con el objetivo principalmente de hacer pruebas se puede usar CoreOS (que sirve como soporte para Docker) GALPon Minino, hecha en Galicia para el mundo, Damn Small Linux, SliTaz (que cabe en 35 megas) y ttylinux (basado en línea de órdenes solo).

En primer lugar activo el modulo KVM del kernel:

    sudo modprobe kvm-intel

A continuación siguo los siguientes pasos para cada SO:

Creo el disco duro virtual:

    qemu-img create -f qcow2 ddvirual.qcow2 500M
    
Arranco la imágen de slitaz:

    qemu-system-x86_64 -hda ./ddvirual.qcow2 -cdrom ./slitaz-4.0.iso
    
Seguimos los pasos de configuración y ya lo tenemos:

![captura1](https://dl.dropbox.com/s/hwmfhh23m7rs73k/slitaz.png)


### 2. Hacer un ejercicio equivalente usando otro hipervisor como Xen, VirtualBox o Parallels.

Esto ya los hice en la [practica 3] (https://github.com/pedroag/Practica3IV/blob/master/README.md)

Ejercicio 4
===========

### Crear una máquina virtual Linux con 512 megas de RAM y entorno gráfico LXDE a la que se pueda acceder mediante VNC y ssh.

En el debian instalado anteriormente le instalo el entorno gráfico lxde:
    
    apt-get install lxde
    
Además le instalo el cliente vnc vinagre:

    sudo apt-get install vinagre

Ejercicio 5
===========

### Crear una máquina virtual ubuntu e instalar en ella un servidor nginx para poder acceder mediante web.


    
