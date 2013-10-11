Actividades de clase de IV
==========================

Ejercicio 6
-----------

Los pasos a seguir para modificar el archvio Readme.md y volver a subirlo han sido los siguientes:

* En primer lugar hago una copia del repositorio en el disco local:  git clone https://github.com/IV-GII/GII-2013.git
* A continuación edito el Readme.md: gedit Readme.md
* Lo añado al repositorio: git add Readme.md
* Hago un commit de lo que he hecho: git commit -m "descripcion"
* Y lo subo: git push origin master

Ejercicio 7
-----------

Los pasos han sido los siguientes:

* Los creo: cgcreate -g memory,cpuacct:navegador y cgcreate -g memory,cpuacct:protext
* Asignos procesos: cgexec -g memory,cpuacct:protext gedit y cgexec -g memory,cpuacct:navegador firefox

Resultados:

| Navegador | Protext
--- | --- | ---
cpuact.usage | 9176719008 | 1866035090
cpuact.stat | user 706 system 170 | user 153 system 24
cpuacct.usage_percpu | 4157895961 5018823047  | 1055893816 813090137 
