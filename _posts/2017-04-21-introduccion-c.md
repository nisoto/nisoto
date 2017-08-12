---
layout: post
title: Introducción al lenguaje C
tags: C/C++
eye_catch:
---

En este capítulo verás un poco de historia acerca de este famoso lenguaje de programación, sus principales características, las fases de desarrollo de un programa escrito en C y sus componentes, entre otros temas. Y por último, aprenderás a crear tu primer programa: el clásico y famoso "Hola Mundo".

<!--more-->

## Marco teórico
----------------

El lenguaje C fue creado entre 1970 y 1972 por Brian Kernighan y Dennis Ritchie para escribir el código del sistema operativo Unix. Desde su nacimiento se fue implantando como el lenguaje de programación de sistemas favorito para muchos programadores, sobre todo por ser un lenguaje que conjugaba la abstracción de los lenguajes de alto nivel con la eficiencia del lenguaje máquina. Los programadores de sistemas que trabajaban sobre MS-DOS y Macintosh también utilizaban C, con lo cual la totalidad de aplicaciones de sistema para microprocesadores y para sistemas UNIX está escrita en este lenguaje.

A mediados de los 80, C se convierte en un estándar internacional ISO. Este estándar incluye tanto la definición del lenguaje como una enorme biblioteca de funciones para entrada/salida, tratamiento de textos, matemáticas, etc.

A mediados de los 80 también se crea C++, extensión de C orientada a objetos (C++ se convierte en estándar ISO en 1998). Una vez que aparece C++, el lenguaje C no siguió siendo modificado, pues C++ sería el que incorporaría nuevos cambios.

## Características
------------------

* Orientado a la programación de sistemas.
* Es altamente transportable.
* Es muy flexible.
* Genera código muy eficiente.
* Es muy expresivo (se pueden realizar muchas funciones escribiendo pocas líneas de código).
* Es muy poco modular.
* Realiza pocas comprobaciones.
* Da poca disciplina al programador.

## Fases de desarrollo de un programa en C
------------------------------------------

### El preprocesador

Transforma el programa fuente, convirtiéndolo en otro archivo fuente **"predigerido"**. Las transformaciones incluyen:

* Eliminar los comentarios.
* Incluir en la fuente el contenido de los ficheros declarados con `#include <fichero>` (a estos ficheros se les suele llamar cabeceras).
* Sustituir en el fuente las macros declaradas con `#define` (por ejemplo `#define CIEN 100`).

### El compilador

Convierte el código fuente entregado por el preprocesador en un archivo en lenguaje máquina: fichero objeto. Algunos compiladores pasan por una fase intermedia en lenguaje ensamblador.

### El enlazador

Un fichero objeto es código máquina, pero no se puede ejecutar, porque le falta código que se encuentra en otros archivos binarios. El enlazador genera el ejecutable binario, a partir del contenido de los ficheros objetos y de las bibliotecas. Las bibliotecas contienen el código de funciones precompiladas, a las que el archivo fuente llama (por ejemplo `printf`).

En la siguiente imagen se puede apreciar con detalle las fases de desarrollo de un programa escrito en C:

![fases]({{ site.baseurl }}/assets/img/fase-programa-c.jpg)

## Bibliotecas estándares
-------------------------

El lenguaje C es muy simple, pues carece de tipos y servicios que forman parte de otros lenguajes. Además, no tiene tipo booleano, no maneja las cadenas y menos la memoria dinámica.

No obstante, el estándar de C define un conjunto de bibliotecas de funciones, que necesariamente vienen con todo entorno de compilación de C y que satisfacen estos servicios elementales.

Las interfaces de estos servicios vienen definidas en unos ficheros cabeceras (header files). El nombre de estos ficheros suele terminar en **".h"**.

Algunos de los servicios proporcionados por las bibliotecas estándares son:

* Entrada y salida de datos (`stdio.h`).
* Manejo de cadenas (`string.h`).
* Memoria dinámica (`stdlib.h`).
* Rutinas matemáticas (`math.h`).

## Componentes del lenguaje C
-----------------------------

Sigue el paradigma de la programación estructurada:

**Algoritmos + Estructuras de datos = Programas**

Estructuras de datos:

* Literales.
* Tipos básicos (todos numéricos).
* Tipos enumerados.
* Tipos estructurados (struct, union).
* Punteros y vectores.

Construcciones algorítmicas:

* Construcciones condicionales (if, switch).
* Construcciones iterativas (while, for, do-while).
* Subrutinas (funciones y procedimientos).

Además de lo anterior, tiene otros elementos:

* Comentarios.
* Inclusión de ficheros.
* Macros.
* Compilación condicional.

El preprocesador es quien normalmente se encarga de interpretar estas construcciones.

## Estructura de un fichero fuente
----------------------------------

Un fichero fuente en lenguaje C tendrá la siguiente estructura típica:

``` c
#include <biblioteca1.h>
#include <biblioteca2.h>

...Declaraciones de funciones...

...Definiciones (cuerpos de funciones)...
...Declaraciones de variables globales...

main()
{
    Cuerpo del main...
}

...Otras definiciones de funciones...
```

Las declaraciones y definiciones se pueden hacer en cualquier orden, aunque es preferible declarar las funciones al principio del programa (por legibilidad).

`main` es simplemente una función más del programa, con la particularidad de que es el punto de entrada al programa.

## Comentarios
--------------

En el C original, tienen la forma: `/* Cualquier texto */`

Los comentarios se pueden extender varias líneas, pero no se pueden anidar (comentarios dentro de otros). En C++ se usan también comentarios de una sola línea, cuya sintaxis es: `// Cualquier texto`

Todo lo que se escriba a partir de las dos barras es un comentario. El comentario termina con el final de la línea.

Ejemplos:

``` c
/* Esto es un comentario
     de varias líneas
*/
// Este es un comentario de C++
// Este es otro comentario
```

## Ejemplo de programa en C
---------------------------

``` c
#include <stdio.h> /* Esta librería o biblioteca incluye las funciones printf (salida) y scanf (entrada) */

int main() /* Función principal, aquí es donde se ejecuta el código */
{
    printf("Hola Mundo"); /* Mensaje de salida */
    return 0; /* Significa que el programa terminó sin errores */
}
```
