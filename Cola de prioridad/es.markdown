Antes de ver la estructura de datos llamada *cola de prioridad*, vamos a ver algunos conceptos para la adecuada comprensión del funcionamiento de la misma:

# Concepto de árbol

Un árbol es una estructura de datos compuesta de nodos y aristas que es acíclica. Un árbol que no tiene ningún nodo se llama árbol vacío o nulo. Un árbol que no está vacío consta de un nodo raíz y potencialmente muchos niveles de nodos adicionales que forman una jerarquía. Las características principales de un árbol es que si tiene $N$ nodos, entonces tendrá $N-1$ aristas y que hay al menos un camino entre cada par de nodos.

<center>![Árbol](arbol.png)</center>

# Terminología utilizada en árboles

* Nodo: Es una estructura que puede contener un valor o condición, es la unidad fundamental de la que están formados los grafos.

* Aristas: Es una relación entre nodos.

* Raíz: El nodo superior de un árbol.

* Hijo: Un nodo conectado directamente con otro cuando se aleja de la raíz.

* Padre: Un nodo conectado directamente con otro cuando se acerca a la raíz.

* Hoja: Un nodo sin hijos.

* Grado de un nodo: Es el número de hijos que tiene

* Profundidad: La profundidad de un nodo es el número de aristas desde la raíz del árbol hasta un nodo.

* Altura de un árbol: Es la profundidad del nodo más profundo.

* Árbol binario: Tipo de árbol en donde cada nodo puede tener a lo más dos nodos hijos.

# Concepto de montículo

Un montículo o heap es una estructura de datos del tipo árbol con información perteneciente a un conjunto ordenado. Los montículos máximos tienen la característica de que cada nodo padre tiene un valor mayor que el de cualquiera de sus nodos hijos, mientras que en los montículos mínimos, el valor del nodo padre es siempre menor al de sus nodos hijos. En un montículo de prioridad, el mayor elemento (o el menor, dependiendo de la relación de orden escogida) está siempre en el nodo raíz.

En la STL existe una estructura de datos llamada cola de prioridad o priority_queue ya implementada, que en realidad es un heap binario de máximos, es decir, que permite extraer los valores insertados en orden decreciente. Una cola de prioridad es una estructura donde se guardan datos de modo que el mayor de ellos pueda ser consultado o eliminado. En cierto modo, es como una cola o una pila donde los elementos no se ordenan según el orden en el que se han insertado, sino según su valor.

# Funcionamiento de un heap binario de máximos

Una cola de prioridad se implementa mediante un heap binario de máximos el cual sus funciones básicas en el árbol son:

* Añadir un elemento al heap

* Devolver cuál es el elemento máximo

* Eliminar el elemento máximo

Si el heap tiene N elementos, entonces el heap tiene una altura de log2(N). En la raíz del heap se debe encontrar el máximo elemento y se cumple que cada nodo padre tiene un valor mayor que el de cualquiera de sus nodos hijos. Al insertar un elemento se realiza el siguiente proceso: el valor se agrega como un nodo en el siguiente espacio disponible en el heap y subirá mientras él sea mayor a su padre hasta el momento o si llega a ser la raíz. Esta operación dura log2(N) por recorrer a lo más la altura del heap. Por ejemplo:

Heap inicial:

<center>![Insertar1](insertar1.png)</center>

Inserción del 34:

<center>![Insertar2](insertar2.png)</center>

<center>![Insertar3](insertar3.png)</center>

<center>![Insertar4](insertar4.png)</center>

Para eliminar el elemento máximo, es decir la raíz del heap, y mantener el orden de los nodos se sigue el siguiente proceso: reemplace el valor en la raíz con el valor del último nodo del heap, quita esa hoja del heap y ahora navegue por el heap, intercambiando valores para restaurar la propiedad de la orden: cada vez, si el valor en el nodo actual es menor que uno de sus hijos, cambie su valor con el hijo más grande (eso asegura que el nuevo valor padre es más grande que sus dos hijos). Esta operación dura log2(N) por recorrer a lo más la altura del heap. Por ejemplo:

Heap inicial:

<center>![Eliminar1](eliminar1.png)</center>

Eliminar:

<center>![Eliminar2](eliminar2.png)</center>

<center>![Eliminar3](eliminar3.png)</center>

<center>![Eliminar4](eliminar4.png)</center>

# Uso de stl::priority_queue

Para que tu programa use colas de prioridad, es necesario añadir #include &lt;queue&gt; y using namespace std; (este último para no tener que poner $stl::$ cada vez que usemos las colas de prioridad) al principio de tu código. Todos los elementos de una cola de prioridad son del mismo tipo, y éste se debe especificar en el momento de crearlo: priority&#95;queue < T > N es una cola de prioridad cuyos elementos son de tipo $T$ y su nombre es $N$. 

Las funciones de la priority_queue son:

* $empty()$ devuelve true si la cola de prioridad está vacía.

* $size()$ devuelve el número de elementos en la cola de prioridad.

* $top()$ devuelve el máximo valor en la cola de prioridad.

* $push(x)$ inserta el valor $x$ en la cola de prioridad.

* $pop()$ elimina el máximo valor en la cola de prioridad. Primero hay que checar si hay elementos en la cola de prioridad para usar adecuadamente esta función.

Es importante que los tipos de datos que usemos en la cola de prioridad sean comparables (casi todos los datos en C++ son comparables, al menos que sea un struct definido por nosotros mismos sin un operador de comparación).

#Problema de ejemplo

# [Buscando una estrella][1]

Podemos observar que si múltiplicamos por -1 cada elemento a insertar en la priority_queue ahora el heap es de mínimos. Ahora las operaciones se pueden ver de la siguiente manera

* $S$: Si hay al menos 3 datos, sacar tres datos de la cola de prioridad (serán las tres valores mínimos insertados), multiplicar por -1 cada uno (valor original), imprimirlos, multiplicarlos por -1 para insertarlos nuevamente en la cola de prioridad. En caso de no tener al menos 3 elementos imprimir "NO HAY SUFICIENTES PUNTAJES".

* $R$: Leer $x$, multiplicarlo por -1 e insertarlo a la cola de prioridad.

* $B$: Si hay elementos en la cola de prioridad, eliminar con pop().

Al final, si la cola de prioridad está vacía, imprimir "NO HUBO GANADOR", en caso contrario sacar de la cola de prioridad todos los valores, quedarte con el último eliminado e imprimir "EL PUNTAJE MAS ALTO FUE "+ ese número por -1 (valor original).

* Código:

<pre>
#include&lt;queue&gt;
#include&lt;stdio.h&gt;
#define ll long long int
using namespace std;
priority_queue &lt; ll &gt; pq;
ll N, x, y, z;
char ins;
int main()
{
    scanf("%lld", &N);
    while(N--)
    {
        scanf(" %c", &ins);
        if(ins=='S')
        {
            if(pq.size()<3)
            {
                printf("NO HAY SUFICIENTES PUNTAJES\n");
            }
            else
            {
                x=pq.top();
                pq.pop();
                y=pq.top();
                pq.pop();
                z=pq.top();
                pq.pop();
                x*=-1;
                y*=-1;
                z*=-1;
                printf("%lld %lld %lld\n", x, y, z);
                x*=-1;
                y*=-1;
                z*=-1;
                pq.push(x);
                pq.push(y);
                pq.push(z);
            }
        }
        else if(ins=='R')
        {
            scanf("%lld", &x);
            x*=-1;
            pq.push(x);
        }
        else
        {
            if(!pq.empty())
                pq.pop();
        }
    }
    if(pq.empty())
    {
        printf("NO HUBO GANADOR\n");
        return 0;
    }
    else
    {
        while(!pq.empty())
            x=pq.top(), pq.pop();
        printf("EL PUNTAJE MAS ALTO FUE %lld", x*-1);
        return 0;
    }
    return 0;
}
</pre>

# Tarea

* List Game

* Adivina

* Lavando platos 

[1]: https://omegaup.com/arena/problem/Buscando-una-estrella#problems
