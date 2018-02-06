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
