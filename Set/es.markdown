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

 - $begin()$

 - $end()$

 - $empty()$

 - $size()$

 - $insert()$

 - $erase()$

 - $clear()$

 - $lower$_$bound()$

 - $upper$_$bound()$

Recuerda que para ocupar cualquiera de estas funciones se hace de la siguiente manera:

<pre>
nombreDelSet.funcion()
</pre>

Donde $funcion()$ es cualquier función que otorga esta estructura.

Para ver mas a detalle estas y mas funciones ve a este link recomendado: [Set - C Plus Plus][1] (se encuentran en la parte inferior de la página y puedes dar clic sobre cualquiera para obtener mas información). 


  [1]: http://www.cplusplus.com/reference/set/set/