# Concepto de pila e implementación

Las pilas son estructuras dinámicas de datos que siguen el principio del Last In First Out (LIFO), es decir, el último elemento que se insertará en una pila es el primero que se eliminará de ella. Por ejemplo, una pila de bandejas en una mesa: la bandeja en la parte superior de la pila es el primer elemento que se moverá si necesita una bandeja específica de esa pila.

**Insertar y eliminar elementos**

Las pilas tienen restricciones en la inserción y eliminación de elementos. Los elementos se pueden insertar o eliminar solo desde un extremo de la pila, es decir, desde la parte superior. El elemento en la parte superior se llama $top()$. Las operaciones de inserción y eliminación de elementos se denominan $push()$ y $pop()$, respectivamente.

Cuando se elimina el elemento superior de una pila, si la pila permanece no vacía, entonces el elemento justo debajo del elemento superior anterior se convierte en el nuevo elemento superior de la pila, es decir, el elemento $top()$. Por ejemplo, en la pila de bandejas, si toma la bandeja en la parte superior y no la reemplaza, la segunda bandeja se convierte automáticamente en el elemento superior ($top()$) de esa pila.

Una pila se puede visualizar de la siguiente manera:

![Pila](pila.png)

**Operaciones**

Sea $pila[]$ un arreglo (de tamaño igual a la cantidad máxima de elementos que puede tener la pila en cualquier momento de la ejecución) que representa la pila y sea $tam$ la cantidad de elementos en la pila. Inicialmente el arreglo está vacío y $tam$ es igual a 0 (ya que no hay ningún elemento en la pila).

* $isempty()$: Checa si la pila está vacía

<pre>
bool isempty()
{
    if(tam==0)
        return true;
    return false;
}
</pre>

* $psize()$: Devuelve el tamaño de la pila.

<pre>
int psize()
{
    return tam;
}
</pre>

* $push(x)$: Inserta el elemento $x$ en la parte superior de la pila.

<pre>
void push(int x)
{
    pila[tam]=x;
    tam++;	
}
</pre>

**Nota: Esta función se declara dependiendo el tipo de dato de la pila.**

* $pop( )$: Elimina el elemento que se encuentra en la parte superior de la pila.

<pre>
void pop()
{
    tam--;
}
</pre>

**Nota: Para usar esta última función se debe verificar primero si hay elementos en la pila.**

* $top( )$: Devuelve el elemento que se encuentra en la parte superior de la pila.

<pre>
int top()
{
    return pila[tam-1];
}
</pre>

**Nota: Para usar esta última función  se debe verificar primero si hay elementos en la pila y se declara dependiendo el tipo de dato de la pila.**

# Utilizar pilas con struct 

Una estructura de datos es un grupo de elementos de datos y funciones agrupadas bajo un nombre. La ventaja de implementar una pila con struct es que puedes declarar varias pilas que realizan las funciones dadas en la estructura y con la implementación antes vista tendrías que realizar las funciones para cada pila que desees ocupar.

El código para implementar una pila que tenga las funciones antes vistas con struct es el siguiente:

<pre>
struct stpila
{
    int tam;
    int pila[1000005];
    stpila() //constructor = sirve para inicializar datos de la estructura
    {
	  tam=0;
    }
    bool isempty()
    {
	  if(tam==0)
		  return true;
	  return false;
    }
    int psize()
    {
	  return tam;
    }
    void push(int x)
    {
	  pila[tam]=x;
	  tam++;	
    }
    void pop()
    {
      tam--;
    }
    int top()
    {
	  return pila[tam-1];
    }
};
</pre>

Declaración (nombre_de_tipo_de_estructura nombre_del_dato):

<pre>
stpila p;
</pre>

Ejemplo de uso de la pila con struct (nombre.función):

<pre>
int t=p.top() //t es igual al número de la parte superior de la pila "p"
p.push(4); //agrega a la pila "p" el número 4
p.pop(); //quita el elemento de la parte superior de la pila "p"
</pre>


# Uso de stl::stack 

La STL ofrece una estructura de datos ya implementada llamada $stack$, que trabaja como una pila y tiene las 5 funciones antes vistas:

* Para usarla es necesario hacer #include &lt;stack&gt; y using namespace std; (este último para no tener que poner $stl::$ cada vez que usemos la pila). 

* Con $stack < T > N$ declaramos una pila que almacena datos de tipo $T$ y el nombre de la pila es $N$.
 
* $push(x)$, $top()$ y $pop()$ son funciones que se llaman y se usan igual en $stl::stack$.

* $psize()$ se llama $size()$ en $stl::stack$ y se usa igual.

* $isempty()$ se llama $empty()$ en $stl::stack$ y se usa igual.

#Problema de ejemplo

# [Paréntesis][1]

Tienes una secuencia formada por paréntesis de apertura '(' y cierre ')' y tu tarea es  verificar si esta secuencia de paréntesis es correcta, es decir, que si existe un paréntesis que abre, entonces debe existir otro que cierra con la correspondencia correcta. 

Es muy fácil ver que la secuencia se puede representar como una pila de la siguiente forma: si encuentro un paréntesis de apertura, lo inserto en la pila y si encuentro un paréntesis de cierre, quiere decir que en la pila tiene que haber al menos un paréntesis de apertura que es su correspondiente y quito ese paréntesis de apertura de la pila, en caso contrario, quiere decir que la secuencia de paréntesis es incorrecta al no tener correspondencia. Al final tengo que checar si hay elementos en la pila, ya que al haberlo, quiere decir que algunos paréntesis de abertura no tiene su respectivo paréntesis de cierre y la cadena sería incorrecta.

* Código sin STL y sin struct: 

<pre>
#include&lt;stdio.h&gt;
#include&lt;algorithm&gt;
#include&lt;string.h&gt;
char pila[1000005];
int tam;

bool isempty()
{
    if(tam==0)
        return true;
    return false;
}

int psize()
{
    return tam;
}

void push(char x)
{
    pila[tam]=x;
    tam++;
}

void pop()
{
    tam--;
}

char top()
{
    return pila[tam-1];
}

char sec[1000006];
int N;
int main()
{
    gets(sec);
    N=strlen(sec);
    for(int i=0; i&lt;N; i++)
    {
        if(sec[i]=='(')
            push(sec[i]);
        else
        {
            if(!isempty())
                pop();
            else
            {
                printf("NO");
                return 0;
            }
        }
    }
    if(!isempty())
        printf("NO");
    else
        printf("SI");
    return 0;
}
</pre>

* Código con struct:

<pre>
#include&lt;stdio.h&gt;
#include&lt;algorithm&gt;
#include&lt;string.h&gt;
struct stpila
{
    char pila[1000005];
    int tam;
    stpila()
    {
        tam=0;
    }
    bool isempty()
    {
        if(tam==0)
            return true;
        return false;
    }
    int psize()
    {
        return tam;
    }

    void push(char x)
    {
        pila[tam]=x;
        tam++;
    }

    void pop()
    {
        tam--;
    }
    char top()
    {
        return pila[tam-1];
    }
};
stpila p;
char sec[1000006];
int N;
int main()
{
    gets(sec);
    N=strlen(sec);
    for(int i=0; i&lt;N; i++)
    {
        if(sec[i]=='(')
            p.push(sec[i]);
        else
        {
            if(!p.isempty())
                p.pop();
            else
            {
                printf("NO");
                return 0;
            }
        }
    }
    if(!p.isempty())
        printf("NO");
    else
        printf("SI");
    return 0;
}
</pre>

* Código con STL:

<pre>
#include&lt;stdio.h&gt;
#include&lt;algorithm&gt;
#include&lt;string.h&gt;
#include&lt;stack&gt;
using namespace std;
stack &lt;char&gt; p;
char sec[1000006];
int N;
int main()
{
    gets(sec);
    N=strlen(sec);
    for(int i=0; i&lt;N; i++)
    {
        if(sec[i]=='(')
            p.push(sec[i]);
        else
        {
            if(!p.empty())
                p.pop();
            else
            {
                printf("NO");
                return 0;
            }
        }
    }
    if(!p.empty())
        printf("NO");
    else
        printf("SI");
    return 0;
}
</pre>

# Tarea

* A jugar 2048

* Atestamiento del callejón

* Notación posfija

* Artista

* Guardias

* Plantas Vs Plantas

* Código QROVI

* Globos

* Destruyendo edificios 

[1]: https://omegaup.com/arena/problem/COMI-Parentesis#problems
