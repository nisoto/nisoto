---
layout: post
title: Anexo N°2, algoritmos resueltos en C (parte II)
tags: C/C++
eye_catch:
---

Este segundo capítulo anexo del curso de C (si no has visto el capítulo anterior, has clic [aquí](https://nisoto.github.io/2017/06/30/a1-algoritmos-c-parte-1/)) contiene varios algoritmos resueltos que abarcan todo el tema de arreglos (vectores y matrices), partiendo por problemas sencillos hasta llegar a problemas algo más complejos.

<!--more-->

## Vectores
-----------

**1.-** Escriba un algoritmo que cree un vector de **n** casillas (n se lee desde teclado) y para cada casilla almacene un número entero cualquiera (ingresado por teclado).

``` c
#include <stdio.h>

void llenar_vector(int a[], int n)
{
    int i;
    for(i=0; i<n; i++)
    {
        printf("Ingrese dato %d: ", i);
        scanf("%d", &a[i]);
    }
}

int main()
{
    int n;
    printf("Ingrese largo del vector: ");
    scanf("%d", &n);
    int a[n];
    llenar_vector(a,n);
    return 0;
}
```

**2.-** Escriba un algoritmo que dado un vector lleno de **n** casillas, muestre por pantalla todos sus elementos (tanto n como los elementos de las casillas fueron ingresados desde teclado) [**Ayuda:** el vector contiene números enteros].

``` c
#include <stdio.h>

void llenar_vector(int a[], int n);

void mostrar_vector(int a[], int n)
{
    int i;
    for(i=0; i<n; i++)
    {
        printf("%d\t", a[i]);
    }
    printf("\n");
}

int main()
{
    int n;
    printf("Ingrese largo del vector: ");
    scanf("%d", &n);
    int a[n];
    llenar_vector(a,n);
    printf("\nVector:\n\n");
    mostrar_vector(a,n);
    return 0;
}
```

**3.-** Escriba un algoritmo que dado un vector lleno de **n** casillas, muestre por pantalla la suma de todos sus elementos [**Ayuda:** el vector contiene números enteros].

``` c
#include <stdio.h>

void llenar_vector(int a[], int n);
void mostrar_vector(int a[], int n);

int suma(int a[], int n)
{
    int i, s=0;
    for(i=0; i<n; i++)
    {
        s+=a[i];
    }
    return s;
}

int main()
{
    int n;
    printf("Ingrese largo del vector: ");
    scanf("%d", &n);
    int a[n];
    llenar_vector(a,n);
    printf("\nVector:\n\n");
    mostrar_vector(a,n);
    printf("\nLa suma de todos los elementos del vector es: %d\n", suma(a,n));
    return 0;
}
```

**4.-** Escriba un algoritmo que dado un vector lleno de **n** casillas, determine y muestre por pantalla el mayor y menor elemento [**Ayuda:** el vector contiene números enteros].

``` c
#include <stdio.h>

void llenar_vector(int a[], int n);
void mostrar_vector(int a[], int n);

int mayor(int a[], int n)
{
    int i, aux=-9999;
    for(i=0; i<n; i++)
    {
        if(a[i]>aux)
        {
            aux=a[i];
        }
    }
    return aux;
}

int menor(int a[], int n)
{
    int i, aux=9999;
    for(i=0; i<n; i++)
    {
        if(a[i]<aux)
        {
            aux=a[i];
        }
    }
    return aux;
}

int main()
{
    int n;
    printf("Ingrese largo del vector: ");
    scanf("%d", &n);
    int a[n];
    llenar_vector(a,n);
    printf("\nVector:\n\n");
    mostrar_vector(a,n);
    printf("\nEl mayor elemento del vector es: %d\n", mayor(a,n));
    printf("El menor elemento del vector es: %d\n", menor(a,n));
    return 0;
}
```

## Matrices
-----------

**1.-** Escriba un algoritmo que cree una matriz de **NxM** casillas (**N** y **M** se leen desde teclado) y para cada casilla almacene un número entero cualquiera (ingresado por teclado).
