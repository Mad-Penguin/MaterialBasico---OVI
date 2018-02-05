# Introducción

El algoritmo de búsqueda en amplitud es un método para visitar todos los elementos de un espacio de búsqueda, exactamente una vez y en un orden tal que, el primer elemento visitado es la raíz, luego se visitan todos los elementos a un "paso" de la raíz, luego todos los elementos a "dos" pasos de la raíz, etc.


# Problema de ejemplo y explicación del algoritmo

Tienes una calculadora de **4** dígitos decimales que sólo puede realizar **2** operaciones: multiplicar por **A** y dividir entre **B**. Si el resultado de multiplicar un número por **A** es un número de más de **4** dígitos la calculadora da como resultado **1**. Si el resultado de dividir entre **B** no es un número entero, entonces la calculadora trunca el resultado entregando únicamente la parte entera. Por ejemplo, si A=2A=2 y B=3B=3 entonces 20×A=4020×A=40 y 20/B=620/B=6 mientras que 6,000×A=16,000×A=1 y 6,000/B=2,0006,000/B=2,000. La calculadora siempre comienza con el número 11 y almacena el último resultado obtenido para utilizarlo en la siguiente operación. Escribe un programa que dados AA y BB encuentre el número mínimo de pasos que se tienen que realizar con la calculadora para obtener un número NN comenzando en el 11 y utilizando únicamente las dos operaciones válidas.

# Algoritmo
