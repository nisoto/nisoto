---
layout: post
title: Tipos de datos elementales en Ruby
tags: Ruby
eye_catch:
---

En este cuarto capítulo del curso de Ruby (si no has visto el capítulo anterior, has clic [aquí](https://nisoto.github.io/2017/03/29/variables-ruby/)) verás los distintos tipos de datos elementales, los cuales se clasifican principalmente en **números** y **cadenas**. Aprenderás a trabajar con ellas, es decir, a inicializarlas y manipularlas a lo largo de la ejecución de un programa y por último, conocerás algunos de los métodos más utilizados, tanto para los números como para las cadenas (recuerda que en Ruby todo es un objeto, y todo objeto tiene sus métodos).

<!--more-->

## Números
----------

En Ruby tenemos 2 grupos generales de números: los **Enteros** (`int`) y los de **Punto flotante** (`float`). Por ejemplo:

``` ruby
entero = 20
punto_flotante = 20.0 
```

Tal como sucede en otros lenguajes, si ejecutas una operación entre 2 números enteros, el resultado será un entero; y ocurrirá lo mismo para los números de punto flotante. Veamos el siguiente fragmento de código:

``` ruby
irb(main):001:0> 12/5
=> 2
irb(main):002:0> 12.0/5.0
=> 2.4
```

Otra cosa importante es que en Ruby los números **no son primitivos**, **¡son objetos!**; así que como todo objeto tiene métodos, los números no son la excepción. Veamos algunos de los métodos más utilizados:

``` ruby
# Convertir un número entero a punto flotante
10.to_f

# Convertir un número de punto flotante a entero
12.23.to_i # Retornará la parte entera, en este caso 12

# Valor absoluto
-10.abs

# Verificar si un número es par
3.even? # En este caso retornará false ya que 3 es impar

# Retornar el número siguiente (sucesor)
2.next
```

Como te habrás dado cuenta, existe un sin fin de métodos para los números, por lo que te recomiendo que revises la documentación de Ruby si quieres conocerlos todos.

## Cadenas
----------

Una cadena o **string** corresponde a un conjunto de caracteres (recuerda que un caracter puede ser una letra, un espacio o incluso un signo). Se inicializan de la siguiente manera:

``` ruby
cadena = "Hola mundo"
cadena2 = 'Hola mundo'
```

Como pudiste notar, puedes utilizar tanto las comillas dobles como las simples (aunque generalmente se utilizan las comillas dobles).

Antes de continuar, debes tener claro que una **variable** es un identificador que se le asigna a un objeto. En los ejemplos anteriores, la cadena es un objeto de la clase `String`, por lo tanto contamos con los distintos métodos existentes para dicha clase (los cuales se detallan más adelante).

Por lo general, a la hora de manipular cadenas, querrás tener variables que incluyan el resultado de una operación, para ello existen 2 formas:

### Concatenación

Veamos el siguiente ejemplo:

``` ruby
nombre = "Nicolas"
puts "Hola " + nombre
```

### Interpolación

Si tomamos el ejemplo anterior:

``` ruby
nombre = "Nicolas"
puts "Hola #{nombre}"
```

Cabe destacar que lo que está dentro de las llaves se evalúa como **código de Ruby**.

Al igual que los números, las cadenas también son métodos. Veamos algunos de los métodos más utilizados:

``` ruby
# Determinar la cantidad de caracteres de una cadena
"nicolas".length

# Convertir una cadena a mayúscula
"nicolas".upcase

# Convertir una cadena a minúscula
"NICOLAS".downcase

# Convertir la primera letra de una cadena a mayúscula
"nicolas".capitalize
```

Tal vez te parezca raro que los métodos detallados anteriormente no tengan el respectivo paréntesis al final. En Ruby, no es obligatorio usar paréntesis, pues solo se recomiendan cuando el método recibe parámetros, por ejemplo:

``` ruby
cadena = "Mi primera cadena en Ruby"
puts cadena.slice(3,7)
```

El método `slice` crea una subcadena, donde el primer parámetro corresponde al inicio de la subcadena (desde donde queremos comenzar) y el segundo parámetro corresponde a la cantidad de caracteres que queremos mostrar desde el inicio de la subcadena.

Debido a que existen muchos métodos para las cadenas, una forma (o truco) de saber cuales son todos los métodos disponibles es ejecutar la siguiente línea de código (en la consola interactiva, IRB):

``` ruby
"".methods
```

Para mayor información, te recomiendo que revises la documentación de [Ruby](https://www.ruby-lang.org/es/documentation/).

Una cosa importante es que si utilizas tildes, puede que tengas problemas a la hora de ejecutar tus programas, por lo que te recomiendo agregar, al principio de tu código, la siguiente línea:

``` ruby
# encoding: utf-8
```

### Caracteres no imprimibles

``` ruby
\n # Salto de línea
\t # Tabulación
```

Es importante mencionar que para los caracteres no imprimibles **se debe utilizar doble comilla**, ya que de esta forma se interpretan, mientras que si utilizamos comillas simples, éstos se conservan. Veamos el siguiente ejemplo para que notes la diferencia:

``` ruby
irb(main):001:0> puts "Hola\n\n\n"
Hola


=> nil
irb(main):002:0> puts 'Hola\n\n\n'
Hola\n\n\n
=> nil
```

Además de los métodos vistos anteriormente para las cadenas, existen otros que pueden ser de gran utilidad:

``` ruby
# Convertir una cadena a número entero
"2".to_i

# Convertir una cadena a número de punto flotante
"3".to_f

# Convertir un número (entero o de punto flotante) a cadena
1.to_s

# Retorna True o False dependiendo si la cadena está vacía o no
"nicolas".empty?

# Determina si la cadena contiene a la subcadena "Ruby" (retorna True o False)
"Esto es una cadena en Ruby".include? 'Ruby'

# Invertir una cadena
"nicolas".reverse
```

¿Qué pasaría ahora si intentamos convertir la cadena `"1asdf"` a número? Mediante los métodos `to_i` o `to_f`, lo que haría Ruby sería tomar la cadena y considerar los números que se encuentran al principio, ignorando todo lo demás. Por ejemplo:

``` ruby
irb(main):001:0> "4asdf".to_i
=> 4
irb(main):002:0> "4qwerty".to_f
=> 4.0
irb(main):003:0> "345asdf".to_i
=> 345
```

¿Y si ahora tuviéramos la cadena `"asd1fgh"`? A diferencia del ejemplo anterior (donde el número está al principio), si la cadena que queremos convertir **no** comienza con un número, el resultado será un `0`. Por ejemplo:

``` ruby
irb(main):001:0> "asd1fgh".to_i
=> 0
irb(main):002:0> "asd1fgh".to_f
=> 0.0
```

### Métodos peligrosos

Un método es peligroso cuando modifica al objeto sobre el que se está trabajando, por ejemplo:

``` ruby
cadena = "nicolas"
cadena.upcase! # El signo de exclamación modifica al objeto
puts cadena
```

Al imprimir la variable `cadena`, nos daremos cuenta que el texto se ha modificado.
