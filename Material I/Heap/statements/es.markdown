# Ordenación por Montículos (heapSort)

Este método usa una estructura de datos llamada heap, la cual consta de un árbol binario en el cual cada nodo mantiene un valor mayor que el de todos sus descendientes, de esta manera la raíz del heap siempre tiene el valor mayor. 

En forma repetitiva se intercambia el valor mayor del heap con el último elemento, se quita el último elemento del heap y con el resto de los elementos se reconstruye el heap.

Los pasos que se aplican son:
1.	Construir un heap con los elementos del arreglo.

2.	Mientras el heap tenga mas de un elemento:

a)	Intercambiar la raíz con el último elemento del arreglo

b)	Disminuir en 1 el tamaño del heap (quitar la última posición)

c)	Reconstruir el heap con el resto de los elementos (sin considerar las posiciones ya ordenadas)

### Construir un Heap

Para construir un heap, el arreglo es considerado como un árbol binario completo, es decir; un arreglo donde la posición 0 es la raíz, las posiciones desde **0** hasta **cociente(n/2)** son nodos interiores tales que si están en una posición **k**, su hijo izquierdo estará en la posición **2*k+1** y su hijo derecho estará en la posición **2*k+2**. Los nodos debajo de la raíz (posiciones desde 2 hasta n) tienen como nodo padre al que esta situado en la posición **(k-1)/2**.

Por ejemplo, para el arreglo {50, 40,  90, 10, 35, 60, 75} el árbol binario completo se vería así:

![fig1](heap1.jpg)

Se comienza desde la posición 1 (hijo izquierdo de la raíz) hasta el último nodo y se revisa si está ordenado con su padre, es decir, que sea menor o igual que el padre, en caso contrario se intercambian. El proceso completo se describe en la siguiente Figura.

![fig2](heap2.jpg)

El heap construido se muestra en la siguente Figura.

![fig3](heap3.jpg)

El código para construir el heap se muestra a continuación.

<pre>
void consHeap(int a[], int n){
	for(int i = 1; i<n;i++){
		int k = i;
		int padre = (k-1)/2;
		while(k>0 && a[k] > a[padre]){
			int aux = a[k];
			a[k] = a[padre];
			a[padre] = aux;
			k = padre;
			padre = (k-1)/2;
		}
	}
}
</pre>


###Reconstruir el heap
Para Reconstruir el heap se realiza lo siguiente:


Mientras el heap tenga mas de un elemento

a)	Eliminar la raíz intercambiándola con el último elemento del arreglo.

b)	Reconstruir el heap con el resto de los elementos (sin considerar las posiciones ya ordenadas)

Para la reconstrucción, la nueva raíz se acomoda de arriba hacia abajo, ordenando con respecto al mayor de los hijos, hasta quedar en el lugar que le corresponda de manera que cumpla con la propiedad del heap.

A continuación se detalla el procedimiento del ordenamiento por Heap.

![fig4](heap4.jpg)
![fig5](heap5.jpg)
![fig6](heap6.jpg)
![fig7](heap7.jpg)
![fig8](heap8.jpg)
![fig9](heap9.jpg)

Por último se muestran las funciones para reconstruir un heap y para ordenar por dicho método

<pre>
void reconsHeap(int a[], int n){
	int aux = a[0];
	a[0] = a[n-1];
	a[n-1] = aux;
	int k = 0;
	int izq = 1;
	int der = 2;
	int fin = 0;
	int ult = n-2;
	while(!fin && k<=((ult-2)/2)){ //k todos los que tienen padre
		if (izq == ult){ //Solo tiene hijo izquierdo
			if(a[k] < a[izq]){
				aux = a[k];
				a[k] = a[izq];
				a[izq] = aux;	
			}
			fin = 1;
		}
		else{//Tiene dos hijos
			if(a[k] < a[izq] && a[izq]>= a[der]){
				aux = a[k];
				a[k] = a[izq];
				a[izq] = aux;
				k = izq;
			}
			else{
				if(a[k] < a[der] && a[der]> a[izq]){
					aux = a[k];
					a[k] = a[der];
					a[der] = aux;
					k = der;
				}
				else{
					fin = 1;
				}
				
			}
			izq = 2*k+1;
			der = 2*k+2;
		}
	}
	
}
</pre>



<pre>
void ordHeap(int a[], int n){
	consHeap(a,n);
	int nElem = n;
	while (nElem>1){
		reconsHeap(a,nElem);
		nElem--;
	}
}
</pre>
