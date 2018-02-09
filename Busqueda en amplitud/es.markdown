# Introducción

El algoritmo de búsqueda en amplitud es un método para visitar todos los elementos de un espacio de búsqueda, exactamente una vez y en un orden tal que, el primer elemento visitado es la raíz, luego se visitan todos los elementos a un "paso" de la raíz, luego todos los elementos a "dos" pasos de la raíz, etc.

Se utiliza una cola para mantener el orden en que se visitan los elementos.

Si representamos los elementos a visitar como un árbol, siendo el nodo 1 la raíz, los elementos se visitarían de la siguiente forma.

![bfs](bfs.gif)

Cada vez que un elemento está en la cola será pintado de color gris, cuando se procesa se vuelve color negro, y sus hijos son agregados a la cola, por lo tanto se vuelven color gris. Esta animación representa el orden como entran a la cola los elementos, para ser procesados después.

![como](como.gif)

# Algoritmo

La idea principal de la búsqueda en amplitud que elementos que están cerca del punto inicial, se visitarán antes que los elementos más lejanos al punto inicial. Para llevar el orden de los elementos a visitar se ocupa una cola, así, los elementos que entran primero a la cola se procesan primero que los elementos que entraron después.

La estructura general de una búsqueda en amplitud es

    {

       declarar cola de tipo Elemento

       declarar arreglo de elementos visitados

       declarar elementoRaiz,elementoHijo

       interstar elementoRaiz a la cola

       mientras !condición de parado

       {

         procesar elemento al frente de la cola
   
         insertar elementos hijos no visitados a la cola

       }

    }


# Problema de ejemplo y explicación del algoritmo

Tienes una calculadora de **4** dígitos decimales que sólo puede realizar **2** operaciones: multiplicar por **A** y dividir entre **B**. Si el resultado de multiplicar un número por **A** es un número de más de **4** dígitos la calculadora da como resultado **1**. Si el resultado de dividir entre **B** no es un número entero, entonces la calculadora trunca el resultado entregando únicamente la parte entera. Por ejemplo, si $A=2$ y $B=3$ entonces $20xA=40$ y $20/B=6$ mientras que $6,000×A=1$ y $6,000/B=2,000$. La calculadora siempre comienza con el número $1$ y almacena el último resultado obtenido para utilizarlo en la siguiente operación. Escribe un programa que dados $A$ y $B$ encuentre el número mínimo de pasos que se tienen que realizar con la calculadora para obtener un número $N$ comenzando en el $1$ y utilizando únicamente las dos operaciones válidas.

Para resolver este problema es muy útil una búsqueda en amplitud, porque queremos saber la mínima cantidad de pasos para llegar a $N$ empezando desde 1, y como una búsqueda en amplitud visita primero todos los elementos a un "paso", luego los que están a dos "pasos", etc., entonces la primera vez que lleguemos a $N$, el número de "pasos" que utilizamos será la respuesta.

El código solución podría quedar así:

    {

    //Declaramos una cola, para mantener el orden de los numeros que vamos a calcular

    #include < stdio.h>

    #include< queue>

    using namespace std;

    int n,a,b;
    struct nodo

    {
        int pasos,valor;

    };

    queue< nodo>cola;

    nodo padre,hijo;
    bool v[10001];


    int main()

    {

    //leemos los datos de entrada

    scanf("%d %d %d",&a,&b,&n);

    //revisamos que no sea el caso especial n=1//
    if(n==1)
    {
        printf("%d",n);
        return 0;
    }

    //marcamos como visitado el número 1, y lo 
    metemos en la cola con 0 pasos, para generar los
    demás números iniciando por el 1

    v[1]=true;
    padre.valor=1;
    padre.pasos=0;
    cola.push(padre);

    //ahora visitamos números uno por uno, guardando 
    los siguientes números que se pueden visitar con 
    una operación más, y como primero los números que 
    podemos obtener con una operación, luego con 2, 
    etc., el primer número que obtengamos tendrá en 
    el número de pasos la respuesta que buscamos

    while(!cola.empty())
    {
        padre=cola.front();
        cola.pop();
        hijo=padre;

        hijo.valor*=a;
        if(hijo.valor>9999)
            hijo.valor=1;


        if(v[hijo.valor]==false)
        {
            v[hijo.valor]=true;
            hijo.pasos++;
            cola.push(hijo);
            if(hijo.valor==n)
            {
                printf("%d",hijo.pasos);
                return 0;
            }
        }

        hijo=padre;
        hijo.valor/=b;
        
        //si no se ha visitado se marca y encola
        if(v[hijo.valor]==false)
        {
            v[hijo.valor]=true;
            hijo.pasos++;
            cola.push(hijo);
            if(hijo.valor==n)
            {
                printf("%d",hijo.pasos);
                return 0;
            }
        }

    }

    return 0;

    }


# Problemas de práctica

https://omegaup.com/arena/problem/Intersecciones#problems
https://omegaup.com/arena/problem/OIEG2013SSA#problems

