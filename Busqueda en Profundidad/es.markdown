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

![DFS](DFS.gif)

# Diferencia entre Amplitud y Profundidad

Es de ahí donde surge la naturaleza ***recursiva*** de la DFS: al momento de explorar el espacio de búsqueda por medio de profundidad, se explora un estado y los hijos de éste, antes de explorar los estados hermanos y sus subsecuentes hijos; tomar estados hermanos en lugar del que se explora actualmente y visitar sus hijos queda pendiente mediante la **recursión**, la cual es llevada a cabo mediante diferentes instancias de una misma función, o mediante una estructura ***Stack*** de la STL. La recursión se encargará de que, una vez que se termine un camino y el estado actual no puede generar hijos y/o los que genera fueron visitados con anterioridad, aquellos estados hermanos y los caminos que nazcan de éstos sean visitados y se sigan nuevas vías. Ésto se traduce como *visitar todas las posibilidades en el espacio de búsqueda*. 

A diferencia de una *búsqueda en amplitud (Breadth First Search ó BFS)*, donde se exploran todos los estados hermanos derivados de un mismo padre y, posteriormente, los hijos y descendencia de dichos estados, en una búsqueda en profundidad se visitan todos los hijos del estado actual y después los estados hermanos y su diferencia.

A continuación, se puede apreciar la comparación entre el funcionamiento de una BFS contra una DFS.

![BFSvsDFS](BFSvsDFS.gif)
 


