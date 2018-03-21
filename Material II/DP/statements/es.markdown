#Introducción

Programación dinámica (DP) es una técnica muy poderosa y que aparece frecuentemente a la hora de resolver ciertos problemas.

La idea general es almacenar resultados obtenidos previamente ya que en caso de necesitarse en el futuro no se tendrían que calcular la respuesta nuevamente (Recordar tu pasado).

Si el problema que se está resolviendo se puede separar en sub-problemas más pequeños y estos a su vez pueden dividirse en sub-problemas aun más pequeños y en el proceso se observa over-lapping, es decir, que un mismo sub-problema aparece más de una vez; puede ser una gran señal para aplicar DP.
También debe considerarse que la solución óptima para estos sub-problemas deben contribuir a la solución óptima del problema original ([Optimal substructure o Subestructura óptima][1]).

# Tipos de DP

 - $Top-Down:$ Empieza por resolver el problema dividiéndolo en sub-problemas. Si notas que el problema ha sido resuelto antes solo regresa la respuesta almacenada, sino, resuélvelo y almacena la respuesta. Usualmente es fácil de pensarlo e imaginarlo. A esto también se le conoce como memorización.

 - $Bottom-Up:$ Analiza el problema y nota el orden en el cual los sub-problemas deben ser resueltos y empieza por los sub-problemas triviales hasta llegar al problema original. En este proceso, se garantiza que los sub-problemas ya fueron resueltos antes de resolver el problema original.

Ten en cuenta que divide and conquer (divide y vencerás) es una técnica diferente a DP, ya que en esta se divide el problema en sub-problemas de modo que no haya overlapping, para asi resolverlos de forma independiente.

#Resolviendo Fibonacci con DP

La serie de Fibonacci es la siguiente:

$F_0=1$  

$F_1=1$ 

$F_{n}=F_{n-1}+F_{n-2}$ con $n \geq 2$

Una idea de solución seria una recursiva con casos base $F_0$ y $F_1$ de la siguiente manera:

<pre>
int Fibo(int n){
    if(n &lt; 2) return 1;
    return Fibo(n-1) + Fibo(n-2);
}
</pre>

Sin embargo está solución es muy lenta para casos grandes. Analicemos lo que la función Fibo(n) hace, los estados que visita para n=5.

![fiboTree](FiboTree.png)

Como se aprecia en la imagen $F_5$ se calculó una vez, $F_4$ una vez, $F_3$ dos veces y $F_2$ tres veces.

Es evidente que estamos haciendo operaciones de más, de acuerdo a la técnica Top−Down podemos almacenar las respuestas obtenidas anteriormente para solo calcularlas una vez con una ligera modificación del código (ocupar memorización).

<pre>
int memo[maxN];

int Fibo(int n){
    if(n &lt; 2) return 1;
    if(memo[n]) return memo[n];  /// Preguntar si ya hemos calculado la respuesta antes.
    return memo[n] = Fibo(n-1) + Fibo(n-2); /// Como no se ha calculado Fibo(n), lo calculamos y lo almacenamos en memo[n]
}
</pre>

Por el hecho de que cada estado se calcula una sola vez, la complejidad es $O(n)$.

Con la técnica Bottom−Up primero se deben establecer los casos triviales, que para este ejemplo serian $F_0$ y $F_1$ ya que sabemos su valor. Después los demás casos deben ser construidos a partir de estos.

<pre>
int Fibo[maxN];
Fibo[0] = Fibo[1] = 1;  /// Casos triviales
for(int i=2; i &lt; n; i++) 
   Fibo[i] = Fibo[i-1] + Fibo[i-2];
</pre>

Como se puede observar en este segundo código, podemos obtener el valor de cualquier $F_m$ talque $m \leq n$ en constante, con un precalculo de complejidad $O(n)$.

  [1]: https://en.wikipedia.org/wiki/Optimal_substructure