# Introduccion

La búsqueda binaria es uno de los algoritmos fundamentales tanto en la programación competitiva como en general en las ciencias de la computación. 

Para adentrarse en el tema, hay que mencionar el problema clásico de aplicación de una búsqueda binaria:

***Dado un arreglo de enteros ordenados de manera creciente, determinar si el numero $x$ aparece en dicho arreglo.***

De momento se expondrá una solución plenamente teórica y muy a grandes rasgos:

Como su nombre indica se necesitará definir el espacio de búsqueda, el cual inicialmente es el arreglo completo (todos los elementos). A partir de esto el algoritmo se basa en preguntar por el elemento que esta justo en medio del espacio de búsqueda y así poder descartar la mitad de este, y reducir su tamaño justo a la mitad. Eventualmente se llegará a un punto donde el espacio de búsqueda será un solo elemento del arreglo el cual nos dará la pauta para saber si $x$ existe o no en el arreglo.

# Generalización de la propiedad binaria

Pero lo realmente interesante de esta técnica es que no solo sirve para encontrar un elemento en algún arreglo ordenado, sino que se puede aplicar en cualquier problema que satisfaga lo siguiente:

*Dado un espacio de búsqueda acotado por $[ini,fin]$ y una expresión booleana $f(x)$, donde si $f(y)$ se cumple, entonces $f(y+1)$ también se cumple; se desea encontrar el mayor valor de $z$ tal que $f(z)$ no se cumple*

De lo anterior también se puede inferir que si $f(z)$ no se cumple, entonces $f(z-1)$ tampoco lo hace. Entonces al evaluar valores consecutivos en $f(x)$ se puede observar algo como lo siguiente.

![funcion](funcion.png)

# Complejidad

Debido a que en cada iteración este algoritmo reduce a la mitad el espacio de búsqueda, su complejidad en tiempo es $O(log_2 N)$, donde $N$ es el tamaño del espacio de búsqueda inicial.

# Implementación

Estos son dos ejemplos de como resolver el problema clásico. 

Donde el arreglo $A$ es el que tiene los elementos ya ordenados, $ini$ y $fin$ las variables que controlan el espacio de búsqueda y $x$ el valor que se quiere encontrar. 

$Recursiva:$
<pre>
int busq_bin(int ini,int fin,int x){
     if(ini == fin){
          if(A[ini] == x) return ini;
          return -1;
     }

     int md = (ini + fin)/2;

     if(A[md] >= x){
          return busq_bin(ini,md,x);
     }else{
          return busq_bin(md+1,fin,x);
     }
}
</pre>

$Iterativa:$
<pre>
int busq_bin(int ini,int fin,int x){
     
     while(ini!=fin){
          int md = (ini + fin)/2;

          if(A[md] >= x){
               fin = md;
          }else{
               ini = md + 1;
          }
     }

     if(A[ini] == x) return ini;
     return -1;
}
</pre>
# Problemas recomendados

 - [Adivina el número][1]
 
 - [Fulanito][2] 

 - [Tiringo-riringo][3]

 - [L-¿Cuánto nos toca? ][4]


  [1]: https://omegaup.com/arena/problem/COMI-Adivina-el-numero#problems
  [2]: https://omegaup.com/arena/problem/Fulanito#problems
  [3]: https://omegaup.com/arena/problem/probD#problems
  [4]: https://omegaup.com/arena/problem/cuanto#problems