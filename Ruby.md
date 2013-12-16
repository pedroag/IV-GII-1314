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
        

Ejercicio 4
-----------

Muestro la fecha de modificación de la URL:

        #!/usr/bin/ruby

        require 'net/http'

        url = ARGV[0]
        puts "URL: " << url << "\n"

        datos = Net::HTTP.get_response  url, '/'

        puts "Fecha de modificacion: #{datos['date'].to_s}\n"
        

Ejercico 5
----------
