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

Ejercicio 9
-----------

Ejecuto  egrep '^flags.*(vmx|svm)' /proc/cpuinfo y me aparece la siguiente lista: 

flags	| fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit hw_pstate lbrv svm_lock nrip_save
--- | ---

Por lo tanto, si tengo instalada esta teconlogía.

Mi modelo es:  AMD Turion(tm) X2 Dual-Core Mobile RM-70

