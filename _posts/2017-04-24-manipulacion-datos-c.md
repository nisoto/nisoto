---
layout: post
title: Manipulación básica de datos en C
tags: C/C++
eye_catch:
---

En este segundo capítulo del curso de C (si no has visto el capítulo anterior, has clic 
[aquí](https://nisoto.github.io/2017/04/21/introduccion-c/)) verás todos los tipos de datos existentes en el lenguaje C, el uso de variables para almacenar los datos y los operadores (ya sea aritméticos, lógicos y de relación). Y por último, el desbordamiento (overflow), redondeo y la famosa "conversión de tipos" o **Casting** (convertir un entero a real, por ejemplo).

<!--more-->

## Literales
------------

Un literal corresponde a un dato escrito directamente (por ejemplo `"Hola"`, `1234`, etc.).

Nombre         | Descripción        | Ejemplo
-------------- | ------------------ | -------------
Decimal        | Entero de base 10  | `123789`
Hexadecimal    | Entero de base 16  | `AFC16`
Octal          | Entero de base 8   | `12367`
Caracter       | Byte en ASCII      | `'A'`
Coma flotante  | Número real        | `3.45e6`
Cadena         | Texto literal      | `"Hola Mundo"`

## Tipos básicos (elementales)
------------------------------

Los datos en C han de tener un tipo. Las variables contienen datos, y se han de declarar del tipo adecuado a los valores que van a contener. C dispone de los siguientes tipos básicos:

* `int`: Enteros (números enteros positivos y negativos).
* `char`: Caracteres (letras).
* `float`: Números en coma flotante (números reales).
* `double`: Números en coma flotante de doble precisión.
* `void`: No-tipo (se emplea con punteros).

Todos estos tipos, a excepción de `void`, son tipos numéricos, incluso el tipo `char`. Se pueden construir tipos de datos más elaborados a partir de estos tipos básicos:

* Vectores y Matrices.
* Punteros.
* Tipos estructurados (registros).

## Variables
------------

Una variable corresponde a un espacio de almacenamiento en memoria RAM, la cual está definida por 4 elementos: nombre, dirección, tipo y valor.

Declaración:

``` c
tipo nombre;
```

Ejemplo:

``` c
int pepe;
```

Las variables globales se declaran justo antes de `main()`.

También existen las constantes, las cuales se diferencian a las variables en que no cambian durante la ejecución de un programa. Una constante se define anteponiendo la palabra `const`.

Ejemplo:

``` c
const float pi=3.14;
```

## Rangos de valores y tipos modificados
----------------------------------------

### Enteros

Una variable entera acepta valores positivos y negativos dentro de un rango determinado, que depende de la plataforma y del compilador (en computadoras bajo MS-DOS suele estar entre -32768 y 32767; en Linux son enteros de 32 bits).

Existen modificadores para el tipo `int`, para alterar el rango de valores sobre el que trabaja:

* `short`: Entero corto (rango más pequeño).
* `long`: Entero largo (rango más amplio).
* `unsigned`: Entero sin signo (0, 1, ..., N).
* `signed`: Entero con signo (-N, ..., 0, ..., N).

Los modificadores de tamaño (`short`, `long`) y de signo (`signed`, `unsigned`) se pueden combinar. Por omisión, un entero es `signed` (en la práctica, esta palabra reservada casi nunca se emplea).

Ejemplos:

``` c
unsigned sin_signo;      /* Entero sin signo */
long saldo_cuenta;       /* Entero largo con signo */
unsigned long telefono;  /* Entero largo sin signo */
```

### Tipo char

El tipo `char` permite manejar caracteres (letras), aunque se trata de un tipo numérico. Normalmente el rango va de -128 a +127 (`signed char`), o bien de 0 a 255 (`unsigned char`). Los literales de tipo carácter se pueden utilizar como números.

Ejemplo:

``` c
char caracter;
int entero;
int main()
{
    caracter=65;  /* Valdría como una 'A' */
    entero='A';   /* Valdría como un 65 */
}
```

La siguiente tabla explica de manera más clara todo lo anterior:

![tiposdedatos]({{ site.baseurl }}/assets/img/tiposdedatos.jpg)

## Identificadores
------------------

Un identificador es un nombre que define a una variable, una función o un tipo de dato. Un identificador válido debe comenzar con una letra o por el carácter de subrayado (`_`), seguido de cualquier cantidad de letras, dígitos o subrayados.

Es importante destacar que C distingue las mayúsculas de las minúsculas y además, no se pueden utilizar palabras reservadas como int, char o while. Muchos compiladores no permiten el uso de letras acentuadas o eñes (ñ).

Ejemplos válidos:

``` c
char letra;
int Letra;
float CHAR;
char _caracter;
int _variable_;
int cantidad_envases;
short numero_;
double precio123;
int __;
long LoG;
```

Ejemplos no válidos:

``` c
int 123var;     /* Comienza con dígitos */
char int;       /* Palabra reservada */
int una sola;   /* Contiene espacios */
int US$;        /* Contiene el símbolo $ */
int var.nueva;  /* Contiene el punto (.) */
int eñe;        /* Puede no funcionar, por lo que no es recomendable */
```

## Operadores básicos
---------------------

### Aritméticos

* Suma (`+`)
* Resta (`-`)
* Multiplicación (`*`)
* División (`/`)
* Resto (`%` o `mod`): devuelve el resto de una división entera.

### Relación

* Menor (`<`)
* Mayor (`>`)
* Menor o igual (`<=`)
* Mayor o igual (`>=`)
* Igual (`==`)
* Distinto (`!=`)

### Lógicos

* Y (`&&`)
* O (`||`)
* No (`!`)

## Expresiones
--------------

Los datos se manipulan mediante expresiones, que sirven para calcular valores. En C hay varios operadores para construir expresiones.

Una expresión combina varias operaciones y devuelve un valor. Se pueden utilizar paréntesis para agrupar subexpresiones.

Ejemplos:

``` c
1
2+2
4+6/2
(3*5+12)%7
((50/4+1)-17%2)*3
```

Los operadores `*`, `/` y `%` tienen precedencia sobre la suma y la resta.

## Asignaciones
---------------

La forma de dar valor a una variable es:

``` c
variable=expresion;
```

Lo que se conoce como asignación.

También se puede dar valor a una variable en el mismo momento en que se declara (inicialización):

``` c
tipo variable=expresion;
```

Una variable que se declara sin inicializar contiene un valor indeterminado.

Ejemplo:

``` c
int valor1=0;    /* Variable inicializada con el valor 0 */
int valor2;      /* Variable no inicializada */

int main()
{
    valor1=4+3;  /* Asignación */
    valor2=5;    /* Otra asignación */
}
```

Una asignación es una expresión, esto quiere decir que:

* Devuelve un valor.
* Una asignación puede incrustarse dentro de una expresión más compleja.

El valor devuelto por la asignación `a=b` es el resultado de evaluar `b`.

Ejemplo:

``` c
c=20-(b=2*(a=5)+4
/* a valdrá 5 (por la expresión a=5)
   b valdrá 2*(5)+4=14
   c valdrá 20-(14)=6 */
```

En consecuencia, una asignación se puede colocar en cualquier sitio donde se puede emplear una expresión.

## Uso de variables
-------------------

Una expresión puede ser el nombre de una variable. En ese caso, el resultado de la expresión es el valor de la variable.

Ejemplo:

``` c
int valor1=5;
int valor2=1;

int main()
{
    valor2=(valor1*4)-valor2;
}
```

## Operadores booleanos
-----------------------

El tipo de dato booleano es aquel que puede representar valores de lógica binaria, esto es 2 valores, que normalmente representan **falso** o **verdadero**.

En C no existe el tipo de dato booleano, así que el resultado de la expresión utiliza números enteros: si la condición es cierta, devuelve un uno (**1**); si no es cierta, devuelve un cero (**0**).

Ejemplo:

``` c
int a=3, b=5, c=3, result1, result2;

int main()
{
    result1=(a<b);   /* Se evalúa la condición. Como es verdadera, en result1 se guardará un 1 */
    result2=(b==c);  /* Esta condición no se cumple, por lo que en result2 se guardará un 0 */
}
```

También se pueden agrupar expresiones booleanas con paréntesis.

Ejemplo:

``` c
(a>0 && a<10) || a==20
```

Será cierto si `a` está entre 1 y 9 (ambos inclusive), o vale 20.

## Operadores avanzados (asignación)
------------------------------------

* Simple (`=`)
* Incremento (`++`)
* Decremento (`--`)
* Suma (`+=`)
* Resta (`-=`)
* Multiplicación (`*=`)
* División (`/=`)

Los operadores de incremento, decremento y asignación compuesta (suma, resta, multiplicación y división) permiten modificar el contenido de una variable de forma eficiente y abreviada.

Ejemplos de los operadores de asignación:

``` c
a++    /* a=a+1 */
a--    /* a=a-1 */
a+=12  /* a=a+12 */
a-=5   /* a=a-5 */
a*=2   /* a=a*2 */
a/=3   /* a=a/3 */
```

## Operadores "pre" y "post"
----------------------------

Si el operador `++` o `--` se coloca a la izquierda, se llama preincremento o predecremento, respectivamente. Si se coloca a la derecha, se llama postincremento o postdecremento.

Cuando se escriben estas expresiones dentro de expresiones más complejas, el valor que se devuelve es:

* Operaciones "pre": el valor nuevo de la variable afectada.
* Operaciones "post": el valor anterior de la variable afectada.

Ejemplo:

``` c
x=1;
a=++x;  /* Preincremento */
/* a valdrá 2, x valdrá 2 */

x=1;
a=x++;  /* Postincremento */
/* a valdrá 1, x valdrá 2 */
```

Las asignaciones compuestas devuelven el nuevo valor de la variable.

Ejemplo:

``` c
x=2;
a=(x*=3)+1;
/* x valdrá 6, a valdrá 7 */
```

## Desbordamientos y redondeos
------------------------------

### Desbordamiento (overflow)

En lenguaje C no se detectan desbordamientos. Si el resultado de una expresión está fuera del rango, el valor resultante es erróneo, pero no se interrumpe el programa ni se señaliza de ninguna forma.

Ejemplo:

``` c
/* Supongamos que tenemos 2 enteros de 16 bits
   Su rango va de -32768 a 32767 */
short int x, y;

int main()
{
    x=30000;
    y=x+3000;  /* ¡y valdrá -29769! (el valor puede ser diferente) */
}
```

### Redondeos

Si una expresión entera da un resultado fraccionario, se redondea al entero más cercano a cero (redondeo inferior). Esto ocurre aunque el destino de la expresión sea una variable en coma flotante.

Ejemplo:

``` c
int x=13/3;  /* x valdrá 4 */
```

Una manera de solucionar esto es trabajando con el tipo de dato float (real), los cuales sirven para trabajar con fracciones o números de un rango mayor que los enteros.

## Conversión de tipos (casting)
--------------------------------

El casting es un procedimiento para transformar una variable primitiva (o elemental) de un tipo a otro. Dentro del casting, se distinguen dos clases:

### Casting implícito

En este caso no se necesita escribir código para que la conversión se lleve a cabo. Ocurre cuando se realiza lo que se llama una conversión ancha (widening casting), es decir, cuando se coloca un valor pequeño en un contenedor grande.

Ejemplo:

``` c
int num1=100;
long num2=num1;  /* Un int cabe en un long */
```

### Casting explícito

En el casting explícito sí es necesario escribir código. Ocurre cuando se realiza una conversión estrecha (narrowing casting), es decir, cuando se coloca un valor grande en un contenedor pequeño. Son susceptibles de pérdida de datos.

Ejemplo:

``` c
int num1=100;
short num2=(short)num1;  /* Aquí hace falta casting explícito, short tiene menor rango que int */
```

Como se puede notar, el formato general para indicar que queremos realizar la conversión es:

``` c
(nuevo_tipo)expresion
```

En el ejemplo anterior, si se sustituye la primera línea `int num1=100` por `int num1=1000000`, el código compilaría bien, pero habría pérdida de datos, pues el `1000000` se sale del rango de short (desbordamiento), que comprende desde -32768 a 32767.

Es importante destacar que sí es posible realizar casting entre una variable primitiva `char` y una variable primitiva que almacene enteros (no olvidemos que todos los tipos de datos elementales son numéricos):

``` c
int num1=164;
char letra=(char)num1;  /* En la variable letra se guardará la letra "ñ" */
```

La siguiente tabla resume las posibilidades de casting existentes:

![tablacasting]({{ site.baseurl }}/assets/img/tablacasting.jpg)

Donde:

* `Si`: indica que el casting es implícito.
* `Si*`: indica que el casting es implícito pero se puede producir pérdida de precisión.
* `Cast`: indica que hay que hacer casting explícito.
