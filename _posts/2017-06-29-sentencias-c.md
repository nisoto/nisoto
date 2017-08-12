---
layout: post
title: Sentencias en C
tags: C/C++
eye_catch:
---

En este cuarto capítulo del curso de C (si no has visto el capítulo anterior, has clic [aquí](https://nisoto.github.io/2017/06/23/entrada-y-salida-c/)) verás las sentencias (simples, compuestas, condicionales, iterativas y de control), las cuales son la base para implementar algoritmos.

<!--more-->

## Introducción
---------------

En C existen construcciones para implementar algoritmos:

* **Sentencias** (simples y compuestas).
* **Construcciones condicionales** (if, switch).
* **Construcciones iterativas** (while, do-while, for).
* **Instrucciones de control de flujo** (break, continue, goto).
* **Subprogramas** (funciones y procedimientos).

Cabe destacar que los **subprogramas** serán abordados con detalle en el siguiente capítulo.

## Sentencias (statements)
--------------------------

Una sentencia corresponde a un fragmento de código. Podemos encontrar dos tipos de sentencias:

### Simple

Es una expresión terminada en punto y coma. Sintaxis:

``` c
sentencia_simple;
```

### Compuesta

Es una serie de sentencias entre llaves. Sintaxis:

``` c
{
    sentencia_1;
    sentencia_2;
    ...
    sentencia_N;
}
```

Ejemplos:

``` c
/* Sentencia simple */
x=y*5;

/* Sentencia compuesta con llaves */
{
    a=b;
    b=x+1;
    num_prod+=b;
    printf("Hay %d productos\n", num_prod);
}
```

``` c
/* Sentencias compuestas dentro de otras */
{
    { w++; }
    { x=1; y=2; }
    { z=0; printf("Hola mundo\n"); }
    { a=1; b=3; c=4; d=b*b-4*a*c; }
}
```

## Sentencias condicionales
---------------------------

### Sentencia if

La construcción `if` sirve para ejecutar código sólo si una condición es cierta. Su sintaxis es:

``` c
if(condicion)
{
    sentencia_1;
    sentencia_2;
    ...
}
```

La condición corresponde a una expresión de cualquier clase. Si el resultado de la expresión es cero, se considera una condición **falsa**; en cambio, si el resultado de la expresión no es cero (por lo general es igual a uno), se considera una condición **verdadera**.

Ejemplo:

``` c
int x=1;

int main()
{
    if(x==1)
        printf("La variable x es igual a 1\n");
    if(x>=2 && x<=10)
        printf("La variable x está entre 2 y 10\n");
}
```

**Nota:** si dentro de la construcción `if` hay sólo una sentencia simple, no es necesario que vaya dentro de llaves.

### Construcción else

Con la construcción `else` se pueden definir acciones para cuando la condición del `if` sea falsa. La sintaxis es:

``` c
if(condicion)
{
    sentencia_a1;
    ...
}
else
{
    sentencia_b1;
    ...
}
```

Ejemplo:

``` c
if(x==1)
    printf("La variable x es igual a 1\n");
else
    printf("La variable x es distinta de 1\n");
```

### Construcción switch

Se utiliza para ejecutar acciones diferentes según el valor de una expresión. Su sintaxis es:

``` c
switch(expresion)
{
    case valor_1:
        sentencia_a1;
        ...
    break;
    case valor_2:
        sentencia_b1;
        ...
    break;
    ...
    default:  /* Esta opción cumple el mismo rol que la construcción "else" */
        sentencia_c1;
        ...
}
```

Las sentencias **a** (sentencia_a1, etc.) se ejecutarán si expresión adquiere el valor_1, lo mismo ocurrirá con las sentencias **b** y así sucesivamente. Cualquier otro valor de expresión conduce a la ejecución de las sentencias **c**, que viene indicado por la palabra reservada `default`.

Ejemplo:

``` c
int opcion;
printf("Escriba 1 si desea continuar, 2 si desea terminar: ");
scanf("%d", &opcion);
switch(opcion)
{
    case 1:
        printf("Continuemos\n");
    break;
    case 2:
        salir=1;
    break;
    default:
        printf("Opcion no valida\n");
}
```

## Sentencias iterativas (bucles)
---------------------------------

Permiten realizar un proceso una o varias veces hasta que se cumpla cierta condición.

### Bucle while

``` c
while(condicion)
{
    sentencia_1;
    sentencia_2;
    ...
}
```

La sentencia se ejecuta una y otra vez mientras la condición sea cierta.

Ejemplo:

``` c
int main()
{
    int x=1;
    while(x<100)
    {
        printf("Linea numero %d\n", x);
        x++;
    }
}
```

Ejemplo utilizando el operador de predecremento:

``` c
int main()
{
    int x=10;
    while(--x)
        printf("Una linea\n");
}
```

En cada iteración se decrementa la variable **x** y se comprueba el valor devuelto por `--x`. Cuando esta expresión devuelva un cero, se abandonará el bucle. Esto ocurre después de la iteración en la que **x** es igual a **uno**.

### Bucle for

``` c
for(expresion_inicial; condicion; expresion_de_paso)
{
    sentencia_1;
    sentencia_2;
    ...
}
```

La expresión inicial se ejecuta antes de entrar en el bucle. Si la condición es cierta, se ejecuta la sentencia y después la expresión de paso. Luego se vuelve a evaluar la condición, y así se ejecuta la sentencia una y otra vez hasta que la condición sea falsa.

El bucle `for` es (casi) equivalente a:

``` c
expresion_inicial;
while(condicion)
{
    sentencia_1;
    sentencia_2;
    ...
    expresion_de_paso;
}
```

Ejemplo:

``` c
int i;
for(i=0; i<10; i++)
    printf("%d\n", i);
```

Las tres expresiones del bucle `for` se pueden omitir, con el siguiente resultado:

* `expresion_inicial`: No se hace nada antes del bucle.
* `condicion`: La condición es siempre cierta (1).
* `expresion_de_paso`: No se hace nada tras la iteración.

### Bucle do-while

``` c
do{
    sentencia_1;
    sentencia_2;
    ...
}while(condicion);
```

La sentencia se ejecuta al menos la primera vez; luego, mientras la condición sea cierta, se itera la sentencia.

Esta sentencia no es muy recomendable ya que las construcciones `while` y `for` bastan para diseñar cualquier clase de bucles. Muy procos programas hoy en día utilizan esta construcción.

### Control de bucles: break y continue

`break` y `continue` permiten controlar la ejecución de los bucles `while`, `for` y `do-while`. Se puede salir de un bucle directamente con `break`; mientras que `continue` va directamente al final del bucle y emprende una nueva iteración.

``` c
while(condicion)
{
    ...
    break;
    ...
}

while(condicion)
{
    ...
    continue;
    ...
}
```

### Instrucción goto

Sirve para saltar incondicionalmente a un punto cualquiera del programa. Su sintaxis es:

``` c
goto etiqueta;
```

Donde **etiqueta** es un identificador que indica el punto al que queremos saltar. La etiqueta se define colocándola en el punto adecuado seguida de dos puntos (:). Sólo se puede saltar a una etiqueta que se encuentre en la misma función donde se invoca a `goto`.

Ejemplo:

``` c
parriba:  /* Declaración de etiqueta */

    ...
    /* Salto directo a una etiqueta */
    if(error) goto pabajo;
    ...
    if(repetir) goto parriba;

pabajo:  /* Declaración de etiqueta */
```

**Nota:** en las sentencias iterativas, siempre debe existir alguna sentencia que afecte la condición, en caso contrario se convierte en un ciclo infinito (loop).
