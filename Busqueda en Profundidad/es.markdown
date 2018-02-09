# Introducción

La **búsqueda en profundidad** es una de las técnicas fundamentales dentro de las ciencias computacionales. También conocida como *Depth First Search (DFS)* es un tipo de búsqueda recursiva, cuyo funcionamiento se basa en el ***backtracking***.

A grandes rasgos, la finalidad de una DFS es que, dado un espacio de búsqueda, explore todas las posibilidades que se puedan generar dentro de éste. Lo anterior permite encontrar un *estado óptimo* con respecto a cierto criterio, o llegar a un estado en particular, registrando información en el proceso, como la cantidad de estados para llegar al objetivo desde el estado inicial.

# Funcionamiento de la Búsqueda en Profundidad 

Para comprender el funcionamiento del *backtracking*, se necesitan comprender tres conceptos. Dos de éstos son *estado padre* y *estado hijo*. Un *estado padre* es aquel a partir del cual se pueden llegar a otros estados, derivados de éste; aquellos "nuevos" estados se conocen como *estados hijos*. De lo anterior, se puede extraer que dos estados son *hermanos* si ambos son hijos del mismo estado padre, es decir, se encuentran en el mismo "nivel" en la búsqueda.

Para ejemplificar de mejor manera lo anterior, utilicemos el siguiente esquema que representa el espacio de búsqueda, el cual, a su vez, puede ser visto como un árbol, dónde los estados se muestran como nodos:

![relationship](relationship.png)

En éste caso, el estado A es *padre* de los estados B, C y D, por lo que se puede decir que B, C y D son *hijos* de A; a su vez, dichos tres estados son *hermanos* entre sí.

Una vez comprendidos los conceptos anteriores, se define como *backtracking* a la técnica, donde, desde un estado inicial, se avanza hacia yendo a todos los estados hijos, posteriormente a los hijos de éstos, y así consecutivamente. Se continúa yendo por cada estado hacia su hijo, uno a la vez, de modo que cada estado solo se visite en una única ocasión dentro de la ruta que se sigue.

Al momento de avanzar en el espacio de búsqueda, se exploran todos los hijos de un estado en concreto antes de explorar los estados del mismo nivel. De ésta forma, se sigue un camino en concreto, que, una vez explorado, se modifica para que explore otros estados dentro del mismo espacio de búsqueda.

Es importante recalcar que el principio de no pasar por un estado ya visitado en el camino que se recorre proviene del hecho de que la profundidad, como se aclaró anteriormente, busca explorar todas las posibilidades dentro del espacio de búsqueda. Ésto lleva a que, en ciertos casos, un estado genere un hijo que se había explorado con anterioridad. El problema en ésto reside en que dicho punto ya visitado generará los mismos estados hijos que generó la primera vez que se exploró, y éstos a su vez tendran la misma descendencia y así consecutivamente, lo cual tiende a una **ejecución cíclica**, y por ende, el algoritmo nunca terminará. 

![DFS](DFS.gif)

# Recursión en la Profundidad


Es de ahí donde surge la naturaleza ***recursiva*** de la DFS: al momento de explorar el espacio de búsqueda por medio de profundidad, se explora un estado y los hijos de éste, antes de explorar los estados hermanos y sus subsecuentes hijos; tomar estados hermanos en lugar del que se explora actualmente y visitar sus hijos queda pendiente mediante la **recursión**, la cual es llevada a cabo mediante diferentes instancias de una misma función, o mediante una estructura ***Stack*** de la STL. 

# Diferencia entre Amplitud y Profundidad

La recursión se encargará de que, una vez que se termine un camino y el estado actual no puede generar hijos y/o los que genera fueron visitados con anterioridad, aquellos estados hermanos y los caminos que nazcan de éstos sean visitados y se sigan nuevas vías. Ésto se traduce como *visitar todas las posibilidades en el espacio de búsqueda*. 

A diferencia de una *búsqueda en amplitud (Breadth First Search ó BFS)*, donde se exploran todos los estados hermanos derivados de un mismo padre y, posteriormente, los hijos y descendencia de dichos estados, en una búsqueda en profundidad se visitan todos los hijos del estado actual y después los estados hermanos y su diferencia.

A continuación, se puede apreciar la comparación entre el funcionamiento de una BFS contra una DFS.

![BFSvsDFS](BFSvsDFS.gif)

# Problemas de Ejemplo

Tomemos como primer ejemplo el primer problema:

	*Sea $S$ un conjunto de $N$ letras del alfabeto inglés. Indicar todas las posibles permutaciones, ordenadas en orden lexicográfico, usando las $N$ letras de $S$.*
 
Entiéndase por *permutación* a cada forma de reordenar un conjunto de elementos de tal manera que, aunque sigan siendo los mismos, los elementos se encuentren en un distinto orden. En una permutación, **el orden de los elementos importa**, ya que cada permutación son los mismos elementos de un conjunto, pero en un orden distinto. 

![permutation](permutation.png)

Para resolver éste problema se puede utilizar búsqueda en profundidad. Las $N$ letras de $S$ pueden ser almacenadas en alguna estructura (arreglo, vector). Como se pide que las permutaciones sean impresas en orden lexicográfico, la forma más sencilla de resolver éste inconveniente es ordenar los $N$ elementos desde un inicio.

Una vez hecho ésto, se debe realizar la búsqueda. Podemos ver cada permutación como un tablero con $N$ espacios en línea, donde en cada uno de esos espacios se coloca uno de los $N$ elementos de $S$. La diferencia entre permutación y permutación es que el orden de los elementos es distinto.

Para comenzar la búsqueda, se necesitará un parámetro: algo que nos indique en que posición del tablero, es decir, de la permutación se encuentra la búsqueda. También será necesario marcar que elementos se han tomado en la permutación, utilizando un arreglo de booleanos o algún otro método. 

Con éstas herramientas, la idea es simple: por cada posición en la que vayamos, se buscarán entre las $N$ letras del conjunto $S$ a la primera que no haya sido ocupada (es decir, la que no esté marcada), ya que esa será el menor elemento disponible lexicográficamente, ya que $S$ fue ordenado. Una vez que se tome un elemento, se avanza en la búsqueda, haciendo un nuevo llamado a la función recursiva, cuyo parámetro aumentará en uno para indicar que se avanza en posición.

Se hace lo mismo por cada posición: recorrer las $N$ letras hasta encontrar la primera desmarcarla, tomar ese elemento y marcarlo, para que otra posición más adelante no intente usarlo. Una vez que las N posiciones estén asignadas a algún elemento de S, la búsqueda se detiene, imprime los elementos en el orden que estén asignados y comienza el backtracking. 

En el backtracking (es decir, el regreso recursivo de la función) se desmarca el elemento tomado anteriormente, indicando que ya no se va a usar, y se continua recorriendo el conjunto ordenado $S$ para tomar el siguiente elemento menor lexicográficamente que esté disponible. Se toma y se hace lo que ya fue explicado anteriormente. Todo el proceso anterior se repetirá con todas las letras de $S$, ya que se buscan todas las permutaciones posibles.

A continuación se presenta un código de ejemplo:

<pre>
#include<stdio.h> ///entrada y salida de datos
#include<algorithm> ///algoritmo de ordenación
using namespace std;
int n;
char conjuntoS[10]; ///conjunto S
char perm[10]; ///arreglo donde se almacenan las permutaciones de S
bool marks[10]; ///arreglo para marcar elementos
void permutations(int pos)
{
    if(pos==n) ///si la posición es igual a N, imprimir y cortar
    {
        for(int i=0;i<n;i++)
            printf("%c",perm[i]);
        printf("\n");
        return;
    }

    for(int i=0;i<n;i++) ///recorrer los N elementos de S para buscar que asignar
    {
        if(!marks[i]) ///si no está marcado el elemento i, asignar
        {
            marks[i]=true; ///marcar
            perm[pos]=conjuntoS[i]; ///asignar a la posicion pos el elemento i
            permutations(pos+1); ///avanzar uno en la busqueda
            marks[i]=false; ///desmarcar para poder volver a utlizar elemento i
        }
    }
}

int main()
{
    scanf("%d",&n); ///leer cuantos elementos tiene S
    for(int i=0;i<n;i++)
        scanf(" %c",&conjuntoS[i]); ///leer los elementos de S

    sort(conjuntoS,conjuntoS+n); ///ordenar S
    printf("\n");

    permutations(0); ///mandar a llamar la búsqueda desde la posición 0

    return 0;
}
</pre>

