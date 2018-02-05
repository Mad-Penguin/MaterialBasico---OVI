Antes de ver la estructura de datos llamada *cola de prioridad*, vamos a ver algunos conceptos para la adecuada del funcionamiento de la misma:

# Concepto de árbol

Un árbol es una estructura de datos compuesta de nodos y aristas que es acíclica. Un árbol que no tiene ningún nodo se llama árbol vacío o nulo. Un árbol que no está vacío consta de un nodo raíz y potencialmente muchos niveles de nodos adicionales que forman una jerarquía. Las características principales de un árbol es que si tiene $N$ nodos, entonces tendrá $N-1$ aristas y que hay al menos un camino entre cada par de nodos.

![Árbol](arbol.png)

# Terminología utilizada en árboles

* Nodo: Es una estructura que puede contener un valor o condición, es la unidad fundamental de la que están formados los grafos.

* Aristas: Es una relación entre nodos

* Raíz: El nodo superior de un árbol.

* Hijo: Un nodo conectado directamente con otro cuando se aleja de la raíz.

* Padre: Un nodo conectado directamente con otro cuando se acerca a la raíz.

* Hoja: Un nodo sin hijos.

* Grado de un nodo: Es el número de hijos que tiene

* Profundidad: La profundidad de un nodo es el número de aristas desde la raíz del árbol hasta un nodo.

* Altura de un árbol: Es la profundidad del nodo más profundo.

* Árbol binario: Tipo de árbol en donde cada nodo puede tener a lo más dos nodos hijos.

# Concepto de montículo

Un montículo o heap es una estructura de datos del tipo árbol con información perteneciente a un conjunto ordenado. Los montículos máximos tienen la característica de que cada nodo padre tiene un valor mayor que el de cualquiera de sus nodos hijos, mientras que en los montículos mínimos, el valor del nodo padre es siempre menor al de sus nodos hijos. En un montículo de prioridad, el mayor elemento (o el menor, dependiendo de la relación de orden escogida) está siempre en el nodo raíz. Por ejemplo:

En la STL existe una estructura de datos llamada cola de prioridad o priority_queue ya implementada, que en realidad es un heap binario de máximos, es decir, que permite extraer los valores insertados en orden decreciente. Una cola de prioridad es una estructura donde se guardan datos de modo que el mayor de ellos pueda ser consultado o eliminado. En cierto modo, es como una cola o una pila donde los elementos no se ordenan según el orden en el que se han insertado, sino según su valor.

# Funcionamiento de un heap binario de máximos

Una cola de prioridad se implementa mediante un heap binario de máximos el cual sus funciones básicas en el árbol son:

* Añadir un elemento al heap

* Devolver cual es el elemento máximo

* Eliminar el elemento máximo

Si el heap tiene N elementos, entonces el heap tiene una altura de log2(N). En la raíz del heap se debe encontrar el máximo elemento y se cumple que cada nodo padre tiene un valor mayor que el de cualquiera de sus nodos hijos. Al insertar un elemento se realiza el siguiente proceso: el valor se agrega como un nodo en el siguiente espacio disponible en el heap y subirá mientras él sea mayor a su padre hasta el momento o si llega a ser la raíz.

![Insertar1](insertar1.png)

![Insertar2](insertar2.png)

![Insertar3](insertar3.png)

![Insertar4](insertar4.png)

![Eliminar1](eliminar1.png)

![Eliminar2](eliminar2.png)

![Eliminar3](eliminar3.png)

![Eliminar4](eliminar4.png)

# Uso de stl::priority_queue

Para que tu programa use colas de prioridad, es necesario añadir #include &lt;queue&gt; y using namespace std; (este último para no tener que poner $stl::$ cada vez que usemos las coas de prioridad) al principio de tu código. Todos los elementos de una cola de prioridad son del mismo tipo, y éste se debe especificar en el momento de crearlo: $priority_queue < T > N$ es una cola de prioridad cuyos elementos son de tipo $T$ y su nombre es $N$. 

#Problema de ejemplo

# [Buscando una estrella][1]

Podemos observar que si múltiplicamos por -1 cada elemento a insertar en la priority_queue ahora el heap es de mínimos. 

* Código:

# Tarea

* List Game

* Adivina

* Lavando platos 

[1]: https://omegaup.com/arena/problem/Buscando-una-estrella#problems
