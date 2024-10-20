# Aplicacion-Estadisticas-de-Baloncesto
## Descripción de la aplicación:
Para utilizar esta aplicación se necesita un fichero .csv con los datos de los jugadores de baloncesto. Esta es la estructura que debe tener ese fichero:

Nombre, Triples intentados, Triples anotados, Tiros libres intentados, Tiros libres anotados, Tiros de dos intentados, Tiros de dos anotados, Tapones, Robos, Rebotes, Minutos, Prorrogas

Jugador1, 10, 5, 8, 6, 15, 10, 2, 3, 4, 30, 1

Con ese fichero la aplicación es capaz de realizar dos tareas:
1. Mostras las estadísticas de un solo jugador, el que el usuario quiera.
2. Comparar las estadísticas entre dos jugadores que el usuario quiera.
   
## Clases:
1. **class Tiros:**
   
   a. Inputs:
   
       - **kwargs --> con ello se creara un diccionario donde: keys-->tipos de tiros: triples, de dos y libres, values-->lista: [tiros intentados, tiros anotados]
       - try/except para asegurar de que los tipos de tiro en el input sean válidos.
   
   b. Métodos:
   
       - tirosdecampo --> para calcular los datos de los tiros de campo, que son los triples más los tiros de dos, devuelve una lista: [tiros de campo intentados, tiros de campo anotados]
       - puntos --> devuelve los puntos anotados (los triples valen 3, los tiros de dos 2 y los libres 1)
       - calcular_porcentajes --> calcula los porcentajes de acierto en el tiro
       - porcentajes --> utiliza el método calcular_porcentajes y devuelve un diccionario con los porcentajes para cada tipo de tiro
       - mostrar_tiros_intentados --> devuelve un diccionario con los tiros intentados
       - mostrar_tiros_anotados --> devuelve un diccionario con los tiros anotados

2. **class Defensa:**

   a. Inputs:

       - **kwargs con los que se creará un diccionario de los datos defensivos: tapones, robos y rebotes
       - try/except para asegurar de que los keys en el input sean válidos y los valores >= 0.

   b. Métodos:
   
       - mostrar_defensa --> devuelve un diccionario con los datos correctos

3. **class Estadisticas:**

   Heredara las clases Tiros y Defensa

   a. Inputs:
   
       - nombre: nombre del jugador a analizar
       - minutos: número de minutos que ha jugado el jugador a analizar
       - partido: número total de minutos que ha tenido el partido
       - **kwargs: los necesarios para utilizar en las clases Tiros y Defensa

   b. Métodos:
   
       - validar_minutos --> se utilizara en el setter de los minutos para asegurar que es un valor >=0 y menor que los minutos totales del partido
       - porminuto --> calcula las estadisticas por minuto jugado
       - proyeccion --> calcula las estadisticas que hubiese conseguido el jugador si hubiese jugado el partido completo
       - mostrarporminuto --> devuelve un diccionario con todos los datos por minuto jugado (utilizara el metodo porminuto)
       - mostrarproyeccion --> devuelve un diccionario con la proyeccion hecha utilizando el metodo proyeccion
       - mostrar --> devuelve un diccionario con todas las estadisticas posibles: puntos anotados, tiros intentados y anotados, datos defensivos, porcentajes, todas las estadisticas por minuto, y la proyeccion

4. **class Comparar:**

   Heredara la clase Estadisticas

   a. Inputs:
   
       - jugador1 --> estadisticas de un jugador
       - jugador2 --> estadisticas de otro jugador

   b. Métodos:
   
       - anotacion --> calcula los puntos anotados para cada jugador usando la funcion puntos de la clase Estadisticas y devuelve un string donde indica cual de los dos a anotado más puntos o si han anotado la misma cantidad de puntos
       - efectividad --> compara el porcentaje de cada jugador para cada tipo de tiro, devuelve un diccionario donde: keys --> los tipos de tiro, values --> un string donde se indica que jugador es más efectivo o si son igual de efectivos en ese tipo de tiros
       - comparar_defensa --> compara los datos defensivos entre los dos jugadores y devuelve un diccionario donde los keys son esos datos y sus values un string explicando el resultado de la comparación

5. **class Inicilizador:**

Una clase para que se utilizará para conseguir una instancia del jugador que quiera el usuario, para ello heredara la clase Estadisticas

   a. Input: 
   
       - dataframe con los datos del fichero que el usuario ha proporcionado previamente
       
   b. Métodos:
   
       - Getter y setter para el dataframe --> exceptions para asegurar de que el dataframe no esta vacio y que es un pandas
       
       - inicializar_jugador --> pregunta al usuario que introduzca el nombre del jugador que quiere analizar, y crea una instancia con las estadisticas de ese jugador
       - Exceptiones: (si no se cumplen la aplicación le volvera a pedir al usuario que introduzca otro nombre)
       
               - para asegurar de que el jugador introduzido por el usuario se encuentra entre los datos
               - para asegurar que los tiros intentados son mayor o igual que los anotados (para cada tipo de tiro)
               
       - efectividad --> compara el porcentaje de cada jugador para cada tipo de tiro, devuelve un diccionario donde: keys --> los tipos de tiro, values --> un string donde se indica que jugador es más efectivo o si son igual de efectivos en ese tipo de tiros

       - comparar_defensa --> compara los datos defensivos entre los dos jugadores y devuelve un diccionario donde los keys son esos datos y sus values un string explicando el resultado de la comparación

## Como funciona la aplicación
Para inicializar la aplicación:

1. Se pide al usuario que introduzca el fichero que contiene los datos de los jugadores que quiere analizar --> se crea un dataframe con los datos del fichero
2. Exceptions:
   
       a. Para asegurar de que el fichero contiene todas las columnas necesarias
       b. Para asegurar de que el fichero (su ruta) que ha introduzido es correcta
       c. Para asegurar de el fichero existe
       d. Para asegurar de que no este vacio
   
4. Utiliza la clase Inicializador con el dataframe del fichero
5. La aplicacion dara tres opciones:
   
       1 --> para ver las estadisticas de un jugador
       2 --> comparar las estadisticas entre dos jugadores
       3 --> terminar
  
7. Excepctiones:
   
       a. para asegurar de que el usuario introduce una de esas tres opciones
       b. en el caso de la comparación, asegurar de que el usuario esta introduciendo dos nombres distintos


 
