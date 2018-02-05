# Búsqueda en Profundidad

Una búsqueda en profundidad es un tipo de búsqueda recursiva
Una **búsqueda en profundidad**, tambien conocida como *Depth First Search (DFS)* es un tipo de búsqueda recursiva, cuyo funcionamiento se basa en el ***backtracking***. 

Para comprender el funcionamiento del *backtracking*, se necesitan comprender tres conceptos. Dos de dichos conceptos son *estado padre* y *estado hijo*. Un *estado padre* es aquel a partir del cual se pueden llegar a otros estados, derivados de éste; aquellos "nuevos" estados se conocen como *estados hijos*. De lo anterior, se puede extraer que dos estados son *hermanos* si ambos son hijos del mismo estado padre.

![relationship](relationship.png)

Se conoce como *backtracking* a la forma de realizar una búsqueda, donde, desde un estado inicial, se avanza hacia yendo a todos los estados hijos, posteriormente a los hijos de éstos, y así consecutivamente. Se conoce como *estados hijos* a todos aquellos a los que se puede llegar a partir de un determinado estado, conocido como *estado padre*. Se continúa yendo por cada estado hacia su hijo, uno a la vez, de modo que cada estado solo se explore una sola vez. (sin pasar por el mismo nodo más de una vez) hasta que no se pueda avanzar más; llegado éste momento, se comienza a dar marcha atrás, de tal manera que se busquen nuevos caminos por donde poder avanzar.


