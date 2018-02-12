# Ordenación por intercambios o "burbuja" (Bubble sort)

Es quizás el método más sencillo pero también el menos eficiente. Se le llama de burbuja porque sigue la idea del proceso que ocurre al mezclar en un tubo líquidos con diferentes pesos, se van acomodando o “burbujeando” los más ligeros hacia arriba y los mas pesados hacia el fondo.

El método consiste en comparar y ordenar todas las parejas adyacentes del conjunto (intercambiándolas si es necesario) de manera que el elemento menor del conjunto se mueva a la primera posición del conjunto. De la misma manera se mueve el segundo menor a la posición 2 y este proceso se repite hasta  ordenar el penúltimo elemento menor del conjunto.
Por ejemplo si el conjunto es:

[20,  10,  25,  5,  30,  15] 	se realizan 5 pasos

**Paso 1**. Se comparan y ordenan las parejas: 

(30, 15) intercambio (15, 30)

(5, 15)  ya ordenada, no hay intercambio

(25, 5) intercambio (5, 25)

(10, 5) intercambio (5, 10)

(20, 5) intercambio (5, 20) obteniendo como resultado el conjunto:

{`5`, 20, 10, 25, 15, 30} 


**Paso 2.** 
Se comparan y ordenan las parejas: (15,30), (25, 15), (10, 15) y (20, 10)
 
{ `5`, `10`, 20, 15, 25, 30 }

**Paso 3.** Se comparan y ordenan las parejas:
(25,30), (15, 25) y (20, 15) 

{ `5`, `10`, `15`, 20, 25, 30 }

**Paso 4.** Se comparan y ordenan las parejas: (25,30) y (20, 25) 

 
{`5`, `10`, `15`, `20`, 25, 30 }

**Paso 5.** Se compara y ordena la pareja: (25,30)   

{`5`, `10`, `15`, `20`, `25`, 30 }

Implementación

<pre>
void burbuja(int a[], int n){
	for(int i =0; i &lt n-1; i++){
		for(int j =n-1; j &gt i; j--){
			if(a[j] &lt a[j-1]){
				int aux = a[j];
				a[j] = a[j-1];
				a[j-1] = aux;
			
			}
		}
	}	
}
</pre>
