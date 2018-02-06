# Introduccion

Los arreglos son la respuesta a la pregunta "¿cómo puedo almacenar fácilmente una gran cantidad de datos?".
Un arreglo es, esencialmente, una variable con un solo nombre que puede almacenar múltiples valores, pero cada valor indexado por un número.
Puede pensar en un arreglo como una lista numerada donde puede acceder a los elementos por dicho número.


De momento se expondrá una solución plenamente teórica y muy a grandes rasgos:

Como su nombre indica se necesitará definir el espacio de búsqueda, el cual inicialmente es el arreglo completo (todos los elementos). A partir de esto el algoritmo se basa en preguntar por el elemento que esta justo en medio del espacio de búsqueda y así poder descartar la mitad de este, y reducir su tamaño justo a la mitad. Eventualmente se llegará a un punto donde el espacio de búsqueda será un solo elemento del arreglo el cual nos dará la pauta para saber si $x$ existe o no en el arreglo.

# Generalización de la propiedad binaria

Pero lo realmente interesante de esta técnica es que no solo sirve para encontrar un elemento en algún arreglo ordenado, sino que se puede aplicar en cualquier problema que satisfaga lo siguiente:

*Dado un espacio de búsqueda acotado por $[ini,fin]$ y una expresión booleana $f(x)$, donde si $f(y)$ no se cumple, entonces $f(y-1)$ tampoco se cumple; se desea encontrar el menor valor de $z$ tal que $f(z)$ se cumple.*

De lo anterior también se puede inferir que si $f(z)$ se cumple, entonces $f(z+1)$ también lo hace. Entonces al evaluar valores consecutivos en $f(x)$ se puede observar algo como lo siguiente.

![funcion](funcion.png)

Y gracias a todo esto es que se puede ir reduciendo a la mitad el espacio de búsqueda.

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

![ejemplo](ej.gif)

# Problemas recomendados

 - [Adivina el número][1]

 - [Fulanito][2]

 - [Tiringo-riringo][3]

 - [LHC][4]

 - [L-¿Cuánto nos toca?][5]

 - [Chocolates CIIC 2015][6]

 - [Los laboratoristas][7]

 - [Planetas][8]

 - [Comprador de Bloques][9]


  [1]: https://omegaup.com/arena/problem/COMI-Adivina-el-numero#problems
  [2]: https://omegaup.com/arena/problem/Fulanito#problems
  [3]: https://omegaup.com/arena/problem/probD#problems
  [4]: https://omegaup.com/arena/problem/LHC#problems
  [5]:  https://omegaup.com/arena/problem/cuanto#problems
  [6]: https://omegaup.com/arena/problem/Chocolates-CIIC-2015#problems
  [7]: https://omegaup.com/arena/problem/Los-laboratoristas#problems
  [8]: https://omegaup.com/arena/problem/Planetas#problems
  [9]: https://omegaup.com/arena/problem/Comprador-de-Bloques#problems
