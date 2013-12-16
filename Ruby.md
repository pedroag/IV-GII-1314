Ejercicio 1
-----------

El comando utilizado ha sido el siguiente:

    ruby --version

Ejercicio 2
-----------

Utilizo un simple for para recorrer los 10 primero números:

    #!/usr/bin/ruby

    for i in(0..9)
        puts i
    end
    
Ejercicio 3
-----------
Si se puede:

        #!/usr/bin/ruby

        arrays = { 
                :lugares => ['Paris','New York','Tokyo','Barcelona'],
                :Equipos => ['Real Madrid','Barcelona','Atletico de Madrid','Real Jaen'],
                :Jugadores => ['Raul','Zidane','Pedro Alcala']
        }
        puts arrays.inspect
        
