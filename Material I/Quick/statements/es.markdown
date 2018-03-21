# Ordenación rápida (Quick sort)

Fue desarrollado por Hoare (1962) y es considerado como el método más rápido y eficiente en los casos promedio, es decir, cuando los datos del conjunto tienen inicialmente un orden aleatorio.
Es un método con una solución de naturaleza recursiva y se basa en la partición.
La idea básica del método es la siguiente:

SI el conjunto tiene más de un elemento ENTONCES

a)	Se elije un elemento divisorio (llamado pivote).
Existen diversas maneras de elegir el pivote. Por ejemplo se toma el primer elemento del conjunto, la mediana de tres elementos: primero, medio y ultimo o bien se elije un elemento al azar.

b)	Se divide el conjunto en dos partes colocando el pivote en su posición definitiva
La partición se hace de manera que los elementos menores o iguales que el pivote queden a la izquierda de este y los mayores a la derecha.

c)	Recursivamente se ordena de la misma manera la parte izquierda 

d)	Recursivamente se ordena de la misma manera la parte derecha 

FIN


En la siguiente figura se puede observar cómo funciona el método. Para conocer la posición del pivote (en este caso se tomó el primer elemento como pivote: 50). Mediante una variable "izq" vamos avanzando desde la posición del pivote hasta encontrar un número que sea mayor que el pivote (en este caso el 90), y entonces hacemos lo mismo pero ahora de derecha a izquierda con la variable "der" hasta encontrar un dato menor que el pivote (en este caso el 30). Cuando no hemos terminado de recorrer el arreglo intercambiamos los valores donde se quedó "izq" y "der", pues recordemos que queremos pasar todos los valores menores del pivote a su izquierda y todos los mayores a su derecha.

Continuamos este proceso hasta que ya visitemos todos los elementos del arreglo ("der" sea menor o igual que "izq") e intercambiamos el pivote con el último elemento en la posición "der". Con esto solo aseguramos que el pivote esté en su lugar (porque todos los menores están a su izquierda y todos los mayores a su derecha) y se generan el subconjunto izquierdo y el subconjunto derecho. Y este proceso se repite hasta tener las posiciones de todos los pivotes.

![quick1](quick1.jpg)

Primero se muestra la implementación de la función partir, que realiza el procedimiento que se mostró en la figura. Al final regresa la posición donde quedó el pivote

<pre>
int partir(int a[], int pIni, int pFin){
	int izq = pIni;
	int der = pFin;
	int piv = a[izq];
	while(izq < der){
		while(a[izq] &lt;= piv)
			izq++;
		while(a[der] &gt; piv)
			der--;
		if (izq &lt; der){
			int aux = a[izq];
			a[izq] = a[der];
			a[der] = aux;
		}	
	}
	a[pIni] = a[der];
	a[der] = piv;
	return der;
}

</pre>

La siguiente función es el algoritmo quick sort en la que se pasa como parámetros el arreglo, la posición inicial y la final. Esta función manda a llamar a la función pivote para realizar la partición y tener dos conjuntos que también se ordenan por el mismo método.

<pre>
void ordRapido(int a[], int pIni, int pFin ){
	if (pIni &lt; pFin){
		int pos = partir(a,pIni, pFin);
		ordRapido(a, pIni, pos-1);
		ordRapido(a, pos+1, pFin);
	}
}
</pre>