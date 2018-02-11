# Ordenación por Selección (Selection sort)


Este método esta basado en la técnica de selección que usan los maestros de pre-primaria para  formar a sus alumnos por estatura. Dado un grupo en orden aleatorio, el maestro en forma repetitiva, selecciona al niño más pequeño y lo mueve a la línea ordenada. Este proceso continua hasta que todos los niños sean movidos a la fila ordenada. Esto se muestra en la siguiente figura.

![fig1](1Seleccion.jpg)
Aplicado a un conjunto de datos el método consiste en buscar el elemento más pequeño del conjunto e  intercambiarlo con el que está en la primera posición; luego se busca el segundo más pequeño y se intercambia con el que está en segunda posición; así sucesivamente hasta intercambiar el de la penúltima posición. Por ejemplo para ordenar el siguiente conjunto:

![fig2](2seleccion.png)

El código de esta función sería:

<pre>
void seleccion(int a[], int n){
	for(int i =0; i< n-1; i++){
		int posM = i;
		for(int j=i+1; j<n; j++){
			if(a[j]<a[posM]){
				posM = j;			
			}
		}
		int aux = a[i];
		a[i] = a[posM];
		a[posM] = aux;
	}	
}
</pre>


