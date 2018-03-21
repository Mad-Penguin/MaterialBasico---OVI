# Ordenación por Mezcla (Merge sort)

Igual que el método rápido, su algoritmo se basa en la estrategia de la partición. Primero el conjunto se divide en dos partes, cada una de las cuales se ordena de manera independiente para finalmente mezclarlas para producir un solo conjunto ordenado.

Para la ordenación por mezcla se usa un algoritmo recursivo. Si se desea ordenar un conjunto con n elementos se usa el siguiente procedimiento:

![Merge1](Merge1.jpg)

Se ordena el siguiente conjunto por el método mergeSort:

![Merge2](Merge2.jpg)

La Función de mezclar dos conjuntos está dada por el siguiente código, el cual recibe como parámetro el arreglo, posición inicial (normalmente 0 en C++) y la última posición (n-1):

<pre>
void mezclar(int a[], int pIni, int pMed, int pFin){
	int aux[10000];
	for(int i =pIni; i<=pFin;i++){
		aux[i] = a[i];
	}
	int i = pIni;
	int j = pMed+1;
	int k = pIni;
	while ((i<= pMed) && (j<=pFin)){
		if (aux[i]<=aux[j]){
			a[k] = aux[i];
			i++;
		}
		else{
			a[k] = aux[j];
			j++;
		}
		k++;
	}
	while (i<= pMed){
		a[k] = aux[i];
		i++;
		k++;
	}
	while (j<= pFin){
		a[k] = aux[j];
		j++;
		k++;
	}
}

</pre>

La función para ordenar por este método es la siguiente.

<pre>

void ordMerge(int a[], int pIni, int pFin){
	if(pIni < pFin){
		int pMed = (pIni + pFin)/2;
		ordMerge(a, pIni, pMed);
		ordMerge(a, pMed+1, pFin);
		mezclar(a, pIni, pMed, pFin);		
	}
}

</pre>