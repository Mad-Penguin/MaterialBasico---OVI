# Ordenación por Inserción (Insertion sort)

Este método se basa en la técnica que usan los jugadores de cartas para ordenar sus cartas en la mano. La primera carta se considera ordenada, la segunda se compara con la primera, si es mayor, la primera no se mueve y la nueva se inserta encima de la primera; sino la primera se mueve un lugar a la derecha y la nueva carta se inserta a la izquierda. A partir de la segunda carta el proceso es comparar con las anteriores (ya ordenadas) y desplazar un lugar a la derecha a las que sean mayores hasta localizar la posición donde se inserta la nueva carta.

Entonces para un conjunto de datos el método inicia considerando el primer elemento como ya ordenado y a partir del segundo se busca el lugar correcto hacia la izquierda, moviendo un lugar a la derecha a los datos mayores para posteriormente insertar (mover) el dato a ordenar en la posición del último dato que se movió a la derecha (si no se movió ningún dato, entonces, el dato a ordenar se queda en su posición).

Por ejemplo para ordenar el siguiente conjunto:

![3insertion](3insertion.jpg)

El código de esta función sería:

<pre>

void insercion(int a[], int n){
	for(int i =1; i< n; i++){
		int aux = a[i];
		int j = i-1;
		while(j>=0 && a[j]>aux){
			a[j+1] = a[j];
			j--;
		}
		a[j+1] = aux;
	}
}	
</pre>
