---
layout: post
title: Entrada y salida de datos en C
tags: C/C++
eye_catch:
---

En este tercer capítulo del curso de C (si no has visto el capítulo anterior, has clic [aquí](https://nisoto.github.io/2017/04/24/manipulacion-datos-c/)) verás la entrada y salida de información en el lenguaje C, donde aprenderás a ingresar, por ejemplo, un número o un carácter desde teclado para manipularlo a tu antojo.

<!--more-->

## Salida por pantalla (printf)
-------------------------------

Permite desplegar un mensaje o información por algún dispositivo de salida. La función `printf` se utiliza según el siguiente formato:

``` c
printf("Cadena de formato", arg1, arg2, ..., argN);
```

Donde se puede encontrar:

* El texto que se desea imprimir.
* Caracteres especiales (secuencias de escape).
* Indicaciones del formato de los argumentos.

Los argumentos son expresiones cualesquiera. Para utilizar `printf`, es necesario escribir al principio del programa la directiva (biblioteca):

``` c
#include <stdio.h>
```

### Formatos de printf

* `%d`: Entero.
* `%u`: Entero sin signo.
* `%x`: Entero hexadecimal.
* `%c`: Carácter.
* `%f`: Coma flotante (float).
* `%e`: Coma flotante (double).

Ejemplo:

``` c
int num=1234;
char letra='h';

int main()
{
    printf("num es igual a %d y letra es igual a %c", num, letra);
}
```

Se puede modificar el formato de salida, indicando cuántos decimales llevará el número, si se rellena de ceros por la izquierda, etc. A continuación se presentan algunos ejemplos:

* `%5d`: Entero decimal alineado a la izquierda, ocupando cinco espacios.
* `%04u`: Entero sin signo ocupando cuatro espacios, y rellenando de ceros a la izquierda si hace falta.
* `%.2e`: Número real (de doble precisión) con dos y sólo dos decimales.
* `%5.3d`: Entero ocupando cinco espacios; aparecen tres cifras como mínimo.

### Secuencias de escape

* `\n`: salto de línea.
* `\t`: tabulación.
* `\a`: sonido.

Ejemplo:

``` c
int main()
{
    printf("Hola mundo\n");
}
```

## Entrada de datos (scanf)
---------------------------

Permite el ingreso de datos desde el exterior. Con la función `scanf` se pueden recoger datos desde teclado. Su sintaxis es:

``` c
scanf("formato", &arg1, &arg2, ...);
```

En formato se especifica qué tipo de dato se quiere leer. Se utiliza la misma descripción de formato que en `printf`. Al igual que la función `printf`, se debe incluir la cabecera `<stdio.h>`.

Ejemplo:

``` c
int x, y;
scanf("%d %d", &x, &y);
```

Importante:

* Si no se antepone el ampersand (`&`), el resultado puede ser desastroso.
* En `scanf` sólo van descripciones de formato, nunca texto normal. Si se quiere escribir antes un texto, hay que utilizar `printf`.
