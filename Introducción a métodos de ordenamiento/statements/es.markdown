# Métodos de ordenación

La ordenación es una de las operaciones más importantes en la programación ya que facilitan el proceso sobre un conjunto de datos, en la mayoría de los casos es más fácil procesar los datos si se encuentran ordenados que si no lo están. Por ejemplo, la búsqueda de un teléfono en una guía telefónica o de una palabra en un diccionario es mucho más fácil debido a que dichos datos están ordenados. Se han desarrollado varios métodos para ordenar datos, algunos son simples e intuitivos, como el de intercambio directo y otros más complicados como es el caso del método rápido pero con la ventaja de ser muy eficiente.


Definimos al proceso de **ordenar** como: reagrupar o reacomodar un conjunto de datos en un orden determinado (ascendente o descendente).

Si se ordena ascendentemente quiere decir que: $a_{1} <= a_{2} <= … <= a_{n}$


Los métodos de ordenación suelen clasificarse por su complejidad en:

**Métodos simples o directos**. Caracterizados por ser cortos, fáciles de implementar y por ser útiles en conjuntos de datos pequeños. Generalmente estos métodos tienen una complejidad cuadrática.

La complejidad algorítmica se expresa en una forma conocida como notación O-grande, donde la **O** representa la complejidad del algoritmo y la **n** representa el número de datos del conjunto que se usa en el algoritmo. Las métricas que se usan para medir la complejidad incluyen entre otros aspectos el número de comparaciones  y el número de movimientos de los datos del conjunto.

La complejidad cuadrática expresada como $O(n^{2})$ significa que operar un conjunto de 100 elementos es 100 veces mayor que operar un conjunto de 10 elementos.
En esta categoría se encuentran los métodos de: Intercambio directo o “burbuja”. Selección directa, e
Inserción directa.

**Métodos complejos.** Son más complicados de implementar pero por lo general más eficientes que los métodos simples. Se pueden aplicar a conjuntos de datos grandes y su complejidad en muchos casos es logarítmica. La complejidad logarítmica es expresada como $O(n$ $log $ $n)$.

En esta categoría se encuentran los métodos de: Mezcla o mergeSort, Rápido o quickSort y Montículos o heapSort.

