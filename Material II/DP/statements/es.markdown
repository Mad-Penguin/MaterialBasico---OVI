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




  [1]: https://en.wikipedia.org/wiki/Optimal_substructure