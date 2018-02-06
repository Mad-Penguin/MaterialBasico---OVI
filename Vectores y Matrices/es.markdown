# Introduccion

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

<pre>my_array [3];</pre>

Podemos visualizarlo de la siguiente manera:

![vista](arrayscheme.jpg)
