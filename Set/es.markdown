# Introducción

La estructura Set permite almacenar elementos con valores únicos (debido a que el valor de un elemento es también su forma de identificarlo) en un orden especifico.

Los valores de los elementos almacenados en el set no pueden ser modificados ya que se tratan como constantes, pero cualquier elemento puede ser insertado o eliminado de la estructura.

De manera interna, los elementos del set están siempre ordenados siguiendo un criterio especifico de ordenamiento, indicado por su algoritmo interno de comparación de objetos.

La estructura Set es generalmente implementada como un árbol binario de búsqueda.

# Propiedades

 - $Orden : $ Todo el tiempo los elementos están ordenados.

 - $Conjunto : $ El valor de un elemento es también la llave usada para identificarlo. 

 - $Llaves$ $unicas : $ Dos elementos en el set no puede compartir la misma llave.

 - $Memoria$ $dinamica : $ Esta estructura maneja dinámicamente sus necesidades de almacenamiento.

# Sintaxis de declaración 

Para poder utilizar la estructura set de la STL se necesita incluir su librería de la siguiente manera:

<pre>
#include &lt; set &gt;
using namespace std;
</pre>

Nota que estas dos líneas son necesarias para poder declarar un set.

Luego, para declarar una nueva estructura set:

<pre>
set &lt T &gt; nombreDelSet;
</pre>
 
Donde $T$ es el tipo de elementos que almacenara el set con nombre o identificador $nombreDelSet$.

# Funciones
   
Este es un listado de las funciones que con mayor frecuencia se ocupan en programación competitiva:

 - $begin():$

 - $end():$

 - $empty():$

 - $size():$

 - $insert():$

 - $erase():$

 - $clear():$

 - $lower$_$bound():$

 - $upper$_$bound():$

Recuerda que para ocupar cualquiera de estas funciones se hace de la siguiente manera:

<pre>
nombreDelSet.funcion()
</pre>

Donde $funcion()$ es cualquier función que otorga esta estructura.

Para ver mas a detalle estas y mas funciones ve a este link recomendado: [Set - C Plus Plus][1] (se encuentran en la parte inferior de la página y puedes dar clic sobre cualquiera para obtener mas información). 

# Acceso a los elementos

La estructura set maneja algo denominado por $forward$ $iterator$. Lo que hace esto es acceder secuencialmente a los elementos. Esta secuencia esta dada por el orden de los elementos.

*Sintaxis de declaración de un iterador para el set*

<pre>
set &lt T &gt :: iterator nombreDelIterador;
</pre>

El iterador $nombreDelIterador$ será capaz de acceder a elementos de cualquier set que almacene datos de tipo $T$.

Algo importante sobre este iterador es que si bien puede acceder a cualquier elemento, no es un elemento del set como tal, por lo que hay que tener cuidado sobre como manejarlo, pues es un apuntador (se explicará en futuros temas). Por esto para obtener el valor del elemento al que esta apuntando actualmente el iterador se le debe anteponer un asterisco. Con esto ya se puede almacenar en alguna otra variable (del mismo tipo de los elementos que apunta el iterador) el valor o utilizar este valor en cualquier forma según convenga.

*Ejemplo de iterador*

<pre>
set &lt T &gt ejemploSet;
set &lt T &gt :: iterator ejemploIterador;

for(ejemploIterador=ejemploSet.begin(); ejemploIterador!=ejemploSet.end(); ++ejemploIterador)
cout &lt&lt *ejemploIterador &lt&lt " ";
</pre>

Este código muestra los elementos que almacena $ejemploSet$ por medio de un recorrido gracias al iterador $ejemploIterador$. Nota que en el ```cout``` se utilizó el asterisco, pues se quiere conocer el valor almacenado.

  [1]: http://www.cplusplus.com/reference/set/set/