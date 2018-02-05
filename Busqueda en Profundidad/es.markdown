# Introducción

La **búsqueda en profundidad** es una de las técnicas fundamentales dentro de las ciencias computacionales. También conocida como *Depth First Search (DFS)* es un tipo de búsqueda recursiva, cuyo funcionamiento se basa en el ***backtracking***. 

Para comprender el funcionamiento del *backtracking*, se necesitan comprender tres conceptos. Dos de dichos conceptos son *estado padre* y *estado hijo*. Un *estado padre* es aquel a partir del cual se pueden llegar a otros estados, derivados de éste; aquellos "nuevos" estados se conocen como *estados hijos*. De lo anterior, se puede extraer que dos estados son *hermanos* si ambos son hijos del mismo estado padre, es decir, se encuentran en el mismo "nivel" en la búsqueda.

Para ejemplificar de mejor manera lo anterior, utilicemos el siguiente esquema que representa el espacio de búsqueda, el cual, a su vez, puede ser visto como un árbol, dónde los estados se muestran como nodos, y los estados padres son nodos de los cuales derivan los estados hijos:

![relationship](relationship.png)

En éste caso, el estado A es *padre* de los estados B, C y D, por lo que, de igual manera, se puede decir que B, C y D son *hijos* del estado A, así como a su vez, dichos tres estados son *hermanos* entre sí.

Una vez comprendidos los conceptos anteriores, se define como *backtracking* a la técnica, donde, desde un estado inicial, se avanza hacia yendo a todos los estados hijos, posteriormente a los hijos de éstos, y así consecutivamente. Se conoce como *estados hijos* a todos aquellos a los que se puede llegar a partir de un determinado estado, conocido como *estado padre*. Se continúa yendo por cada estado hacia su hijo, uno a la vez, de modo que cada estado solo se visite en una única ocasión.

Al momento de avanzar en el espacio de búsqueda, se exploran todos los hijos de un estado en concreto antes de explorar los estados del mismo nivel. De ésta forma, se sigue un camino en concreto, que, una vez explorado, se modifica para que explore otros estados dentro del mismo espacio de búsqueda.

![DFS](DFS.png)

Es de ahí donde surge la naturaleza ***recursiva*** de la DFS: al momento de explorar el espacio de búsqueda por medio de profundidad, se explora un estado y los hijos de éste, antes de explorar los estados hermanos y sus subsecuentes hijos. Una vez que se termina 

A diferencia de una *búsqueda en amplitud (BFS)*, donde se exploran todos los estados hermanos derivados de un mismo padre y, posteriormente, los hijos de dichos estados, en una búsqueda en profundidad 


 


