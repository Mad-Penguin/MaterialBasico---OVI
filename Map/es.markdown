# Concepto de map

Un diccionario es una estructura donde podemos guardar datos ordenados según una clave, de tal modo que resulte muy eficiente buscar el dato conociendo su clave correspondiente. Por ejemplo, en un diccionario real, la clave es una palabra, mientras que el dato guardado es la definición de la misma. La STL ofrece diversas estructuras de datos que pueden ejercer funciones parecidas a las de un diccionario. La más importante es el map &lt; K , T &gt;, donde K es el tipo de la clave y T es el tipo de los datos. Se requiere, además, que los elementos de tipo K sean ordenables.

La principal característica que se espera de un diccionario es que las operaciones de insertar un nuevo dato con su clave, buscar si una clave existe, y recuperar el dato asociado, sean veloces. En concreto, se espera que tarden tiempo proporcional al logaritmo base 2 del número de elementos almacenados en el diccionario. Esto se corresponde, intuitivamente, con el tiempo que tardaríamos a encontrar una palabra en un diccionario real siguiendo el algoritmo de búsqueda binario: abrimos el diccionario por la mitad, vemos en qué mitad del diccionario está la palabra buscada, volvemos a abrir por la mitad de la parte donde está la palabra, etc. Como a cada paso descartamos la mitad del trozo de diccionario que nos interesaba, tardamos tantos pasos como veces podamos dividir por la mitad el número de palabras del diccionario, es decir, el logaritmo base 2 de este número. La implementación usual de los tipos map  es usando árboles binarios de búsqueda.

# Uso de stl::map

Para que tu programa use maps, es necesario añadir #include&lt;map&gt; y using namespace std; (este último para no tener que poner $stl::$ cada vez que usemos los maps) al principio de tu código. Todos los elementos de un map son del mismo tipo.

En un map, podemos insertar y recuperar datos de modo muy parecido a como usaríamos un vector, escribiendo m[c]=d; insertamos un dato d con clave c (o modificamos el dato antiguo, si la clave c ya estuviera en el diccionario), y escribiendo m[c] recuperamos el dato con clave c. Por ejemplo, un map &lt; int , T &gt; funciona de un modo parecido a un vector &lt; T &gt;, con la ventaja de que no necesitamos preocuparnos de su tamaño, o de si accededemos fuera de rango, porque cualquier entero puede actuar como clave. 

Escribir m[c] siempre sirve para recuperar un dato con clave c. ¿Qué ocurre cuando no hay ningún dato con clave c? En otros lenguajes de programación, esto provocaría un error en tiempo de ejecución. La STL, sin embargo, hace lo siguiente: toma las medidas necesarias para que este intento de recuperación no provoque ningún error. Para ello, el map m inserta un dato con clave c y dato vacío (0 si el dato es de tipo int, double o bool, "" si el dato es de tipo string, etc.), y retorna ese dato vacío. Por lo tanto: nunca hay que escribir m[c] a menos que estemos seguros de que exista la clave c, o que queramos insertar en el map la clave no existente.

Para saber si una clave está o no en el map sin insertarla debemos usar el método **find**: este método nos devuelve un iterador que nos indica si ha encontrado o no la clave, y qué dato asociado tiene la misma. Más adelante veremos los iteradores de un map; por ahora, lo único que necesitamos saber es que para saber si la clave existe o no existe en el map m sólo necesitamos hacer m.find(c) y comparar el valor que retorna con m.end(): si son iguales, es que la clave no existe; de otro modo, sabemos que escribir m[c] es seguro, y que devolverá el dato asociado. Haciendo lo descrito anteriormente estaríamos realizando dos búsquedas, una primera m.find(c) para saber si el dato existe, y una segunda m[c] para encontrar el dato asociado. En realidad, el iterador que devuelve el find ya contiene el dato asociado, sin que necesitemos buscarlo de nuevo en el diccionario: habría que guardar la respuesta en una variable de tipo iterador, compararlo con m.end(), y si son distintos, usar este mismo iterador para acceder al dato. Para eliminar el elemento con clave c de un map basta con hacer **m.erase(c)**. El erase también funciona si recibe un iterador (como los devueltos por el find) en vez de una clave. Al igual que con otras estructuras de la STL, también podemos hacer **m.size()** para conocer el número de elementos almacenados, **m.empty()** para saber si está o no está vacío, y **m.clear()** para borrar todos los elementos del map.

Una de las operaciones más usuales de un map es la de recorrer todos los elementos que contiene. Internamente, el map guarda todos los elementos que hemos insertado ordenados según su clave: podemos recorrer los datos guardados siguiendo este orden, usando iteradores. Un iterador es, en cierto modo, la posición que ocupa un par clave-dato dentro del diccionario. A través de un iterador podemos acceder no sólo a la clave y al dato, sino también al elemento siguiente y anterior del diccionario. De este modo podemos recorrerlo, elemento a elemento, de un modo idéntico al que ya vimos con los vectores.

Si m es un map &lt; K ,T &gt; y it es un iterador que apunta a un elemento del diccionario, se tiene que it->first es la clave del elemento, de tipo const K, y que it->second es el dato correspondiente, de tipo T. Dado un iterador it, las operaciones ++it; y --it; hacen que el iterador apunte al siguiente o anterior elemento del diccionario. El método **m.begin()** devuelve un iterador que apunta al primer elemento del map, mientras que **m.end()** devuelve un iterador que apunta una posición después del último elemento del diccionario. (Este era el iterador que devolvía el m.find(c) para indicar que no había encontrado la clave c.) Para recorrer un map, por lo tanto, basta con empezar con el iterador m.begin() e irlo incrementando con ++it; hasta comprobar que es igual a m.end(), momento en el que habremos acabado de recorrer por orden todos los elementos del map.

Por último, sólo nos falta decir cómo crear una variable de tipo iterador: el tipo de un iterador a un map<K,T> se llama **map &lt; K,T &gt;::iterator**. Con esto, ya podemos recorrer todos los elementos de un map. Por ejemplo, completamos el programa que calculaba cuántas veces aparecía cada palabra por la entrada, haciendo que escriba el número de apariciones ordenadamente (según el orden lexicográfico de las palabras que aparecen, que hacen de claves en este ejemplo).


Con lo que sabemos podemos recorrer los elementos del map uno por uno, empezando por el principio o por el final, hasta encontar el positivo más pequeño; esto, sin embargo, sigue siendo un método lento. Lo que necesitamos es buscar una clave (por ejemplo, el nómero 0) y, caso de no existir, obtener un iterador a un elemento cercano a la clave buscada, de modo que con unos pocos incrementos o decrementos adicionales podamos encontrar el iterador al elemento buscado. Un método que hace lo que queremos es el **m.lower_bound(c)** que, dada una clave c, retorna un iterador a la entrada de clave c si esta existe (al igual que el find), pero que, si no existe ninguna entrada con clave c, devuelve un iterador a la primera entrada con clave mayor que la clave c dada , o m.end() si una tal entrada no existe (a comparación de **m.upper_bound(c)** que devuelve un iterador a la primera entrada con clave mayor que la clave c dada o m.end() si una tal entrada no existe.

#Problema de ejemplo

# [Tecleando números][1]

Podemos ir contando las repeticiones con un map (la clave es el número y el dato son las repeticiones).

* Código:

<pre>
#include&lt;stdio.h&gt;
#include&lt;map&gt;
using namespace std;
int n;
long long a;
map&lt;long long,long long&gt; mapita;
map&lt;long long,long long&gt;:: iterator it;
char aux;
int main()
{
    scanf("%d",&n);
    for(int i=0; i&lt;n; i++)
    {
        scanf(" %c",&aux);
        scanf("%lld",&a);
        if(aux=='A')
        {
            mapita[a]++;
        }
        if(aux=='B')
        {
            it=mapita.find(a);
            if(it!=mapita.end())
                printf("%lld\n",mapita[a]);
            else
                printf("0\n");
        }
    }
    return 0;
}
</pre>

# Tarea

* Tablero multiplicador

* Triples

* Alfa buena maravilla onda dinamita escuadrón lobo

[1]: https://omegaup.com/arena/problem/Tecleando-numeros/#problems
