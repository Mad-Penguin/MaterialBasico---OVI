# Introducción

Los arreglos son la respuesta a la pregunta "¿cómo puedo almacenar fácilmente una gran cantidad de datos?".
Un arreglo es, esencialmente, una variable con un solo nombre que puede almacenar múltiples valores, pero cada valor es indexado por un número.
Puede pensar en un arreglo como una lista numerada donde puede acceder a los elementos por dicho número.

# Consideraciones de sintaxis para arreglos

# Declarar Arreglos

Para declarar un arreglo, debe especificar dos cosas (además del nombre): el tipo y el tamaño.

<pre>
int my_array [10];
</pre>

Esto declara un arreglo con diez elementos enteros. Tenga en cuenta que el tamaño va entre los corchetes y los corchetes van después del nombre de la variable.

# Acceder a los elementos de un arreglo

Para acceder a los elementos de un arreglo, utilizamos corchetes, pero esta vez, en lugar del tamaño, proporciona el índice del elemento al que desea acceder (cuidando no escribir una posición que no exista):

<pre>my_array [4];</pre>

Podemos visualizarlo de la siguiente manera:

![vista](arrayscheme.jpg)

my_array se refiere al arreglo como un todo, mientras que my_array [0] se refiere al primer elemento y my_array [4] al quinto. La indexación de arreglos comienza en 0. Con índice, me refiero al número que conecta para obtener un valor particular de un arreglo. Probablemente no sea esto a lo que estás acostumbrado, a menos que tus padres (o quien te enseñó a contar) fueran programadores de computadoras.

Una vez que haya elegido un elemento particular en la matriz, lo tratará como cualquier otra variable. Puede modificar un elemento de la matriz de la siguiente manera:

<pre>
int my_array [4]; // declaro el arreglo
my_array [2] = 2; // establece el tercer elemento del arreglo en 2
</pre>

# Arreglos de más de una dimensión

Los arreglos también se pueden usar para representar datos multidimensionales, como un tablero de ajedrez o damas (o, si prefieres algo un poco más simple, un tablero de “gato” ). La información multidimensional solo significa que tiene más de un índice para eso.

Para declarar una arreglo de dos dimensiones o matriz , proporciona cada una de las dimensiones:

int gato [3] [3];

Visualizándolo de la siguiente manera

![matriz](matriz.jpg)

Dado que una matriz es rectangular, hay dos índices que debe usar para acceder a ella: uno para la fila y otro para la columna. En el diagrama, he puesto los índices exactos que necesitaría usar para acceder a cada elemento. Todo lo que necesita son dos valores, uno que va en el primer corchete y otro que va en él segundo.
Puedes hacer una matriz tridimensional, aunque probablemente no necesites hacerlo. De hecho, podrías hacer una matriz de cuatro o cinco dimensiones o más.

Tener una matriz en forma de cuadrícula significa que puede organizar mejor los datos; si tiene un tablero de “GATO”, puede establecer el valor de cada elemento de la matriz para que coincida con la posición actual del tablero. También puede usar una matriz para representar un laberinto o el diseño de un nivel en un juego de rol.

# Implementación de arreglos y matrices con ciclos.

Las matrices y ciclos funcionan extremadamente bien juntos; se puede acceder a una matriz inicializando una variable a 0 e incrementando esa variable hasta que esa variable sea tan grande como la longitud de la matriz, un patrón que se ajusta exactamente al modelo de un ciclo for.

Aquí hay un pequeño programa que demuestra el uso de ciclos for para crear tablas de multiplicar y almacenar los resultados en una matriz de dos dimensiones.

<pre>
  #include <iostream>
  using namespace std;
  int main ()
  {
      int array[ 8 ][ 8 ]; // Declara un arreglo de dos dimensiones
      for ( int i = 0; i < 8; i++ )
      {
          for ( int j = 0; j < 8; j++ )
          {
            array[ i ][ j ] = i * j; // Asigna un valor a cada elemento
          }
      }
      cout << "Tabla de multiplicar";
      for ( int i = 0; i < 8; i++ )
      {
        for ( int j = 0; j < 8; j++ )
        {
          cout << "[ "<< i <<" ][ "<< j <<" ] = ";
          cout << array[ i ][ j ] <<" "; cout << "\n";
        }
      }
    }
</pre>
