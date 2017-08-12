---
layout: post
title: Arreglos en C
tags: C/C++
eye_catch:
---

En este sexto capítulo del curso de C (si no has visto el capítulo anterior, has clic [aquí](https://nisoto.github.io/2017/06/29/subprogramas-c/)) verás una de las estructuras de datos más utilizada en el mundo de la programación: los **arrays** (arreglos en español). Un array nos permite almacenar información de un mismo tipo (**¡ojo con eso!**) en casillas y, además, pueden ser de infinitas dimensiones. En este capítulo sólo nos centraremos en arrays unidimensionales (vectores) y bidimensionales (matrices).

<!--more-->

## Vectores
-----------

Un vector es una **estructura de datos** que permite almacenar un conjunto de elementos, todos de un mismo tipo. Se puede visualizar como una **secuencia contigua de celdas** (o casillas), cada una de las cuales puede guardar un elemento.

A modo de ejemplo, el siguiente vector (llamado A) posee 10 celdas, cada una almacena un valor (en este caso enteros). Cada celda, comúnmente, es identificada por un **índice** (valor entero) que comienza en cero (0).

![vector]({{ site.baseurl }}/assets/img/vector.png)

De esta manera, si deseamos referirnos al tercer elemento del vector A, lo indicamos como `A[2]`. Nótese que todos los elementos son del mismo tipo de dato, por lo que el vector A es de tipo entero. El primer elemento es `A[0]` y el último es `A[9]`.

La dimensión o tamaño de un vector corresponde al número de celdas que lo conforman. En el caso anterior, el tamaño es de 10 casillas.

Sobre las celdas de un vector, se pueden realizar todas las operaciones que permitan sus elementos. Por ejemplo, si deseamos obtener la suma de los 3 primeros elementos del vector A antes descrito, entonces se puede escribir `A[0] + A[1] + A[2]`.

### Declaración de un vector

En lenguaje C, un vector se declara como:

``` c
tipo nombre[dimension];
```

Esta declaración avisa al compilador que debe reservar un espacio de memoria para cada elemento del vector. Por ejemplo, el vector C de 12 caracteres se declara como:

``` c
char C[12];
```

En este caso, como cada carácter ocupa 1 byte de memoria, el compilador reservará 12 bytes de memoria para almacenar el vector C. Si deseamos almacenar la cadena "hola mundo" en el vector, quedaría algo como:

![vectorchar]({{ site.baseurl }}/assets/img/vector2.png)

Otros ejemplos:

``` c
int a[10];
float b[30];
double x[45];
char s[100];
```

El uso de los vectores para el manejo de información es enorme, porque se pueden utilizar para **ordenar**, **buscar**, **modificar**, **reemplazar**, **borrar**, etc.; sabiendo que los elementos están contiguos y son posibles de identificar sin confusión.

### Llenado de un vector

Por ejemplo, si tenemos el siguiente vector:

``` c
int a[10];
```

Para llenarlo, podemos hacerlo de dos maneras distintas:

#### Casilla por casilla

``` c
a[0]=34;
a[1]=27;
...
a[9]=236;
```

#### Utilizando sentencias iterativas

``` c
/* Bucle while */
int i=0, dato;
while(i<10)
{
    printf("Ingrese dato: ");
    scanf("%d", &dato);
    a[i]=dato;
    i++;
}

/* Bucle for */
int i, dato;
for(i=0; i<10; i++)
{
    printf("Ingrese dato: ");
    scanf("%d", &dato);
    a[i]=dato;
}
```

Nótese que los dos métodos de llenado hacen exactamente lo mismo.

## Matrices
-----------

Una matriz es una **estructura de datos** que permite almacenar una colección de elementos, todos del mismo tipo. La diferencia con los vectores está en que, en las matrices, los elementos no están organizados linealmente, sino que su organización es **bidimensional**, es decir, en filas y columnas.

A modo de ejemplo, la siguiente matriz (denominada M) posee 25 celdas, distribuidas en 5 columnas y 5 filas. Cada celda de la matriz es identificada por 2 índices (valores enteros) que comienzan en [0][0].

![matriz]({{ site.baseurl }}/assets/img/matriz.png)

De esta manera, si deseamos referirnos a una celda ubicada en la tercera fila y tercera columna de la matriz M, lo indicamos como `M[3][3]`. Nótese que todos los elementos de la matriz son del mismo tipo de dato (en este caso, entero) por lo que la matriz M es de tipo entero. El primer elemento de la matriz es `M[0][0]` y el último es `M[4][4]`.

El tamaño de una matriz corresponde al número de celdas que lo conforman. En el caso anterior, el tamaño es de 25 (5x5).

Una característica importante de una matriz cuadrada (aquella que tiene igual número de filas y columnas), son sus diagonales (principal y secundaria). Por ejemplo, en la matriz anterior, la diagonal principal queda definida por las celdas: `M[0][0]`, `M[1][1]`, `M[2][2]`, `M[3][3]`, `M[4][4]`; y la diagonal secundaria queda definida por las celdas: `M[0][4]`, `M[1][3]`, `M[2][2]`, `M[3][1]`, `M[4][0]`.

Sobre las celdas de una matriz, se pueden realizar todas las operaciones que permitan sus elementos. Por ejemplo, si deseamos obtener la suma de los elementos de la diagonal principal de la matriz M antes descrita, entonces se puede escribir: `M[0][0] + M[1][1] + M[2][2] + M[3][3] + M[4][4]`.

Una matriz puede tener diferentes números de filas y columnas. Por ejemplo, una matriz P puede ser definida con 10 columnas y 6 filas. En este caso, no se aplica la definición de diagonal.

### Declaración de una matriz

En lenguaje C, una matriz se declara como:

``` c
tipo nombre[filas][columnas];
```

Por ejemplo, una matriz x (de enteros) de 2 filas y 3 columnas se declara como:

``` c
int x[2][3];
```

Si deseamos almacenar los números 23, 34, 500, 11, 0 y 9001 (en ese orden), quedaría algo como:

![matriz]({{ site.baseurl }}/assets/img/matriz2.png)

Otros ejemplos:

``` c
int m[3][3];
float n[3][5];
double o[6][2];
```

### Llenado de una matriz

Por ejemplo, si tenemos la siguiente matriz:

``` c
int m[3][4];
```

Para llenarla, al igual que en los vectores, podemos hacerlo de dos maneras distintas:

#### Casilla por casilla

``` c
m[0][0]=120;
m[0][1]=23;
...
m[2][3]=365;
```

#### Utilizando sentencias iterativas

``` c
/* Bucle while */
int i=0, j=0, dato;
while(i<3)
{
    while(j<4)
    {
        printf("Ingrese dato: ");
        scanf("%d", &dato);
        m[i][j]=dato;
        j++;
    }
    i++;
}

/* Bucle for */
int i, j, dato;
for(i=0; i<3; i++)
{
    for(j=0; j<4; j++)
    {
        printf("Ingrese dato: ");
        scanf("%d", &dato);
        m[i][j]=dato
    }
}
```

Nótese que los dos métodos de llenado hacen exactamente lo mismo.
