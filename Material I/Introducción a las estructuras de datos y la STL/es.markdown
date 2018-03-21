# Estructuras de datos

Una estructura de datos es un conjunto de elementos del mismo tipo que se relacionan entre sí y que se pueden operar como un todo. Dependiendo cuál estés usando puedes hacer diferentes tipos de operaciones, pero en general, las operaciones principales de una estructura de datos son navegar en ella, buscar o consultar información, copiar, modificar, insertar o eliminar datos e incluso verificar si está vacía.

En muchos problemas nos podemos imaginar objetos y acciones que se relacionan entre sí y por ello es muy importante conocer las estructuras de datos más comunes que se utilizan en la programación, ya que con ello lograremos implementar soluciones de manera adecuada y eficiente para esos problemas.

Este material está compuesto por 8 partes:

* Introducción a las estructuras de datos y la STL

* Vector

* Pila 

* Cola

* Lista enlazada

* Cola de Prioridad

* Set

* Map

El objetivo de este material es dar a conocer el concepto, implementación y uso de 7 estructuras de datos más usadas en la solución de problemas de olimpiada, así como proporcionar una serie de problemas para su práctica.

# Standard Template Library (STL)

La STL (Standard Template Library) es una librería estándar de estructuras de datos y algoritmos que forma parte del estándar del C++, esto garantiza que cualquier compilador de C++ debe incluir esta librería, por lo que cualquier programador puede usarla para sus códigos. El objetivo fundamental de la STL es evitar que los programadores tengan que implementar, una y otra vez, aquellos algoritmos o estructuras de datos fundamentales, como por ejemplo el algoritmo de ordenación, o estructuras de datos como la cola de prioridades (heap) o el diccionario (map).

Se debe tomar en cuenta que el uso de esta librería puede requerir mayor tiempo y memoria durante la ejecución, pero en la mayoría de los casos suelen servir para la solución adecuada de los problemas.

Con la STL los elementos de una estructura de datos se guarda en un espacio de memoria libre, por lo que es importante conocer el uso de los **iteradores**.

# Iteradores

Una de las operaciones más comunes sobre una estructura de datos es la de recorrer todos o algunos de los elementos almacenados en ella según un orden predefinido. Un iterador es un objeto que puede retornar por turno una referencia a cada uno de los elementos de la estructura de datos. Los iteradores no son punteros, pero actúan como si lo fuesen. En cierto modo, un iterador es un puntero seguro, que no sólo sirve para apuntar a un valor de un tipo, sino que además sabe desplazarse en la estructura. 

Para acceder al dato del interador se debe escribir *nombre_del_iterador y para recorrer la estructura de datos correspondiente se usa ++nombre_del_iterador o --nombre_del_iterador (esto se verá a más detalle en los siguientes temas).