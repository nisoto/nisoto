---
layout: post
title: Subprogramas en C
tags: C/C++
eye_catch:
---

En este quinto capítulo del curso de C (si no has visto el capítulo anterior, has clic [aquí](https://nisoto.github.io/2017/06/29/sentencias-c/)) verás los subprogramas o **rutinas**, los cuales corresponden a **miniprogramas** cuyo fin es resolver una o varias tareas en particular de las tantas que nuestro programa final resolverá.

<!--more-->

## Introducción
---------------

Un **subprograma** (también llamado rutina), es un conjunto de instrucciones de computador, que utiliza las mismas estructuras de control y tipos de datos que un programa. Su finalidad es realizar tareas específicas de acuerdo a ciertos parámetros traspasados desde el programa.

Un subprograma se escribe dentro de un programa y puede ser invocado tantas veces como se quiera. Tiene un nombre propio, sus propias variables, constantes e identificadores, todos los cuales sólo tienen validez dentro de él.

Dependiendo del lenguaje de programación que se utilice, existen dos tipos de subprogramas: **funciones** y **procedimientos**.

## Funciones
------------

Son subprogramas que **retornan un valor**. Por ello, se pueden utilizar como parte de expresiones así como asociadas a variables. Comúnmente requieren el ingreso de parámetros para su operatoria.

La definición de una función especifica lo siguiente:

* Nombre de la función.
* Número de argumentos que lleva y tipo de dato de cada uno de ellos.
* Tipo de dato que devuelve.
* Cuerpo de la función (el código que se ejecuta).

Su sintaxis es la siguiente:

``` c
tipo_dato nombre(arg1, arg2, ...)
{
    Declaracion de variables locales...
    ... Cuerpo ...
}
```

Cada argumento se especifica como en una declaración de variable. El cuerpo de la función debe contener una sentencia donde se devuelve el resultado de la función, que se hace de esta forma:

``` c
return expresion;
```

La función devolverá el resultado de la expresión.

Ejemplo:

``` c
int suma(int a, int b)
{
    return a+b;
}
```

Esta función devuelve la suma de dos números enteros.

Para llamar a una función, se escribe su nombre y entre paréntesis los valores que se deseen dar a los argumentos:

``` c
funcion(expr1, expr2, ...)
```

Cada expresión se evalúa y su resultado se pasa como argumento a la función. Las expresiones han de tener el mismo tipo del argumento correspondiente, o al menos un tipo compatible. Si analizamos el ejemplo anterior:

``` c
x=suma(1,a+5);     /* Correcto */
y=suma("hola",5);  /* ¡Incorrecto! */
```

Una llamada a una función es una expresión, con todo lo que ello implica. Es importante tener en cuenta que no es necesario recoger en una variable el valor devuelto por la función (por ejemplo, `printf` y `scanf` son funciones que devuelven un entero).

### Funciones sin argumentos

Se declaran con la palabra reservada `void` entre paréntesis (sólo en C). Por ejemplo:

``` c
int fecha(void)
{
    ... Cuerpo ...
}
```

Y se les llama así:

``` c
dato=fecha();
```

Es decir, siempre hay que escribir paréntesis aunque no haya argumentos. En C++ se declaran sólo con los paréntesis, sin el `void`.

## Procedimientos
-----------------

Son subprogramas que **no retornan un valor**. Se invocan como una instrucción independiente. Comúnmente requieren el ingreso de parámetros para su operatoria. Su sintaxis es la siguiente:

``` c
void nombre(arg1, arg2, ...)
{
    ... Cuerpo ...
}
```

**Nota:** en C no existe diferencia entre las funciones y procedimientos, por lo tanto, a todos los subprogramas se les llama funciones (los procedimientos suelen ser llamados **funciones void**).

No es obligatorio que un procedimiento contenga sentencias `return`, puesto que no devuelve nada. No obstante, si se desea salir prematuramente de una función `void`, se puede utilizar `return`:

``` c
void rutina()
{
    ...
    if(error)
        return;
    ...
}
```

Una función en C no puede alterar las variables pasadas como parámetros. Los parámetros se pasan por valor.

Ejemplo:

``` c
/* Función inútil */
void incrementa(int variable)
{
    variable++;
}

int main()
{
    int x=33;
    incrementa(x);
    /* x no resulta afectada, sigue valiendo 33 */
    printf("La variable x es igual a %d\n", x);
}
```

Para conseguir alterar una variable pasada como parámetro, se debe recurrir a los **punteros** (que se verán más adelante).

Importante:

* En C no se pueden declarar funciones dentro de otras (funciones anidadas o locales), ya que todas las funciones son globales.
* Una función puede llamarse a sí misma (recursividad).
