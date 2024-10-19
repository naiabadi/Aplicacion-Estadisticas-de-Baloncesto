# Aplicacion-Estadisticas-de-Baloncesto
"Clases:"
"1. Tiros:"
""" Inputs: **kwargs --> con ello se creara un diccionario donde
                                                                        keys-->tipos de tiros: triples, de dos y libres,
                                                                        values-->lista: [tiros intentados, tiros anotados]
                        try/except para asegurar de que los tipos de tiro en el input sean válidos.
                Métodos:
                        1. tirosdecampo --> para calcular los datos de los tiros de campo, que son los triples más los tiros de dos
                                            devuelve una lista: [tiros de campo intentados, tiros de campo anotados]
                        2. puntos --> devuelve los puntos anotados (los triples valen 3, los tiros de dos 2 y los libres 1)
                        3. calcular_porcentajes --> calcula los porcentajes de acierto en el tiro
                        4. porcentajes --> utiliza la función calcular_porcentajes y devuelve un diccionario con los porcentajes para cada tipo de tiro
                        5. mostrar_tiros_intentados --> devuelve un diccionario con los tiros intentados
                        6. mostrar_tiros_anotados --> devuelve un diccionario con los tiros anotados
                """
