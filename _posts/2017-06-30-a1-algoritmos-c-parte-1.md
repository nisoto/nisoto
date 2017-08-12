---
layout: post
title: Anexo N°1, algoritmos resueltos en C (parte I)
tags: C/C++
eye_catch:
---

Este capítulo anexo del curso de C (si no has visto el curso, has clic [aquí](https://nisoto.github.io/2017/04/21/introduccion-c/)) contiene varios algoritmos resueltos que van desde problemas básicos (como sumar dos números, por ejemplo), hasta problemas algo más complejos (utilización de sentencias condicionales, iterativas, etc.).

<!--more-->

## Ejercicios básicos
---------------------

**1.-** Escriba un algoritmo que lea desde teclado un número entero cualquiera e imprima por pantalla su doble.

``` c
#include <stdio.h>

int main()
{
    int n;
    printf("Ingrese un numero: ");
    scanf("%d", &n);
    printf("Su doble es: %d\n", n*2);
    return 0;
}
```

**2.-** Escriba un algoritmo que lea desde teclado un número entero cualquiera e imprima por pantalla su doble, triple y cuádruple.

``` c
#include <stdio.h>

int main()
{
    int n;
    printf("Ingrese un numero: ");
    scanf("%d", &n);
    printf("Su doble es: %d\n", n*2);
    printf("Su triple es: %d\n", n*3);
    printf("Su cuadruple es: %d\n", n*4);
    return 0;
}
```

**3.-** Escriba un algoritmo que lea desde teclado dos números enteros cualesquiera e imprima por pantalla la suma de ellos.

``` c
#include <stdio.h>

int main()
{
    int a, b;
    printf("Ingrese primer numero: ");
    scanf("%d", &a);
    printf("Ingrese segundo numero: ");
    scanf("%d", &b);
    printf("%d + %d = %d\n", a, b, a+b);
    return 0;
}
```

**4.-** Escriba un algoritmo que lea desde teclado dos números enteros cualesquiera e imprima por pantalla su producto.

``` c
#include <stdio.h>

int main()
{
    int a, b;
    printf("Ingrese primer numero: ");
    scanf("%d", &a);
    printf("Ingrese segundo numero: ");
    scanf("%d", &b);
    printf("%d * %d = %d\n", a, b, a*b);
    return 0;
}
```

**5.-** Escriba un algoritmo que lea desde teclado dos números enteros cualesquiera (los cuales serán el dividendo y el divisor, respectivamente) e imprima por pantalla el cuociente y resto [**Ayuda:** utilizar `%`].

``` c
#include <stdio.h>

int main()
{
    int a, b;
    printf("Ingrese dividendo: ");
    scanf("%d", &a);
    printf("Ingrese divisor: ");
    scanf("%d", &b);
    printf("Division = %d\n", a/b);
    printf("Resto = %d\n", a%b);
    return 0;
}
```

**6.-** Escriba un algoritmo que lea desde teclado tres números enteros cualesquiera e imprima por pantalla la suma de los dos primeros multiplicado por el tercero.

``` c
#include <stdio.h>

int main()
{
    int a, b, c, result;
    printf("Ingrese primer numero: ");
    scanf("%d", &a);
    printf("Ingrese segundo numero: ");
    scanf("%d", &b);
    printf("Ingrese tercer numero: ");
    scanf("%d", &c);
    result=(a+b)*c;
    printf("Resultado: %d\n", result);
    return 0;
}
```

## Ejercicios intermedios
-------------------------

**1.-** Escriba un algoritmo que lea desde teclado dos números enteros cualesquiera y determine cuál de ellos es el mayor [**Ayuda:** se puede dar el caso que ambos números sean iguales].

``` c
#include <stdio.h>

int main()
{
    int a, b;
    printf("Ingrese primer numero: ");
    scanf("%d", &a);
    printf("Ingrese segundo numero: ");
    scanf("%d", &b);
    if(a>b)
    {
        printf("%d es el mayor\n", a);
    }
    else if(a<b)
    {
        printf("%d es el mayor\n", b);
    }
    else
    {
        printf("Los numeros son iguales\n");
    }
    return 0;
}
```

**2.-** Escriba un algoritmo que lea desde teclado un número entero cualquiera y determine si es par o impar.

``` c
#include <stdio.h>

int main()
{
    int n;
    printf("Ingrese un numero: ");
    scanf("%d", &n);
    if(n%2==0)
    {
        printf("El numero ingresado ES PAR\n");
    }
    else
    {
        printf("El numero ingresado NO ES PAR\n");
    }
    return 0;
}
```

**3.-** Escriba un algoritmo que lea desde teclado un número entero cualquiera y determine si es positivo, negativo o igual a cero.

``` c
#include <stdio.h>

int main()
{
    int n;
    printf("Ingrese un numero: ");
    scanf("%d", &n);
    if(n>0)
    {
        printf("El numero ingresado es POSITIVO\n");
    }
    else if(n<0)
    {
        printf("El numero ingresado es NEGATIVO\n");
    }
    else
    {
        printf("El numero ingresado es igual a CERO\n");
    }
    return 0;
}
```

## Ejercicios difíciles
-----------------------

**1.-** Escriba un algoritmo que imprima por pantalla los **n** primeros números naturales, donde "n" se lee desde teclado [**Ayuda:** un número natural es todo número positivo y distinto de cero].

``` c
#include <stdio.h>

int main()
{
    int n, i=1;
    printf("Ingrese un numero: ");
    scanf("%d", &n);
    printf("Los %d primeros números naturales son:\n\n");
    while(i<=n)
    {
        printf("%d\n", i);
        i++;
    }
    return 0;
}
```

**2.-** Escriba un algoritmo que determine e imprima por pantalla la suma de los **n** primeros números naturales, donde "n" se lee desde teclado [**Nota:** utilizar sentencias iterativas].

``` c
#include <stdio.h>

int main()
{
    int n, i=1, s=0;
    printf("Ingrese n: ");
    scanf("%d", &n);
    while(i<=n)
    {
        s+=i;
        i++;
    }
    printf("La sumatoria de los %d primeros numeros es: %d\n", n, s);
    return 0;
}
```

**3.-** Escriba un algoritmo que determine e imprima por pantalla la cantidad de dígitos de un número entero cualquiera (leído desde teclado).

``` c
#include <stdio.h>

int main()
{
    int n, c=0, aux;
    printf("Ingrese un numero: ");
    scanf("%d", &n);
    aux=n;
    while(n>0)
    {
        c++;
        n/=10;
    }
    printf("El numero %d tiene %d digitos\n", aux, c);
    return 0;
}
```

**4.-** Escriba un algoritmo que determine e imprima por pantalla la suma de todos los dígitos de un número entero cualquiera (leído desde teclado).

``` c
#include <stdio.h>

int main()
{
    int n, aux, s=0;
    printf("Ingrese un numero: ");
    scanf("%d", &n);
    while(n>0)
    {
        aux=n%10;
        s+=aux;
        n/=10;
    }
    printf("La suma de sus digitos es: %d\n", s);
    return 0;
}
```

**5.-** Escriba un algoritmo que determine e imprima por pantalla todos los divisores de un número entero cualquiera (leído desde teclado).

``` c
#include <stdio.h>

int main()
{
    int n, i=1;
    printf("Ingrese un numero: ");
    scanf("%d", &n);
    printf("Divisores:\n\n");
    while(i<=n)
    {
        if(n%i==0)
        {
            printf("%d\n", i);
        }
        i++;
    }
    return 0;
}
```

**6.-** Escriba un algoritmo que lea desde teclado un número entero cualquiera y determine si es o no primo.

``` c
#include <stdio.h>

int main()
{
    int n, i=1, c=0;
    printf("Ingrese un numero: ");
    scanf("%d", &n);
    while(i<=n)
    {
        if(n%i==0)
        {
            c++;
        }
        i++;
    }
    if(c==2)
    {
        printf("El numero ingresado ES PRIMO\n");
    }
    else
    {
        printf("El numero ingresado NO ES PRIMO\n");
    }
    return 0;
}
```

**7.-** Escriba un algoritmo que lea desde teclado un número entero cualquiera y determine si es o no palíndromo [**Nota:** un número es palíndromo cuando se lee igual de izquierda a derecha, que de derecha a izquierda].

``` c
#include <stdio.h>

int main()
{
    int n, n2, aux, num=0;
    printf("Ingrese un numero: ");
    scanf("%d", &n);
    n2=n;
    while(n2>0)
    {
        aux=n2%10;
        num=num*10+aux;
        n2/=10;
    }
    if(n==num)
    {
        printf("El numero ingresado ES PALINDROMO\n");
    }
    else
    {
        printf("El numero ingresado NO ES PALINDROMO\n");
    }
    return 0;
}
```

**8.-** Escriba un algoritmo que lea desde teclado un número entero cualquiera y determine su inverso.

``` c
#include <stdio.h>

int main()
{
    int n, aux, num=0;
    printf("Ingrese un numero: ");
    scanf("%d", &n);
    while(n>0)
    {
        aux=n%10;
        num=num*10+aux;
        n/=10;
    }
    printf("El numero invertido es: %d\n", num);
    return 0;
}
```
