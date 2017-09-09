---
layout: post
title: Arrays en Ruby
tags: Ruby
eye_catch:
---

En este sexto capítulo del curso de Ruby (si no has visto el capítulo anterior has clic [aquí](https://nisoto.github.io/2017/08/10/entrada-y-salida-ruby/)) aprenderás a utilizar una de las estructuras de datos más utilizadas en el mundo de la programación: los arrays (arreglos en español). A pesar de que en la mayoría de los lenguajes de programación los array permiten almacenar información de un mismo tipo, en Ruby es algo distinto.

<!--more-->

## ¿Qué es un Array?
--------------------

Un array es un contenedor donde podemos almacenar datos (o elementos) y, a diferencia de muchos otros lenguajes de programación, éstos pueden ser de distinto tipo. Cabe destacar que en Ruby (y en Python) a un array se le conoce también como **list** (lista en español).

### Declaración de un Array

Existen 2 formas de crear (declarar) un array, la primera es utilizando corchetes (`[]`):

``` ruby
first_array = []
```

Mientras que la segunda se realiza mediante el comando `new`:

``` ruby
second_array = Array.new
```

### Inicialización de un Array

Para almacenar elementos a nuestro array, basta con agregarlos dentro de los corchetes y separados entre comas, como se detalla a continuación:

``` ruby
first_array = ["Ruby", "Python", "JavaScript"]
```

### Imprimiendo un Array

Si ahora queremos imprimir los elementos de un array, debemos utilizar el comando `puts`:

``` ruby
puts first_array.to_s
puts second_array.to_S
```

Es importante utilizar el método `to_s` para que no haya conflicto (este método convierte toda la lista a string para imprimirla sin problemas).

Acceder a los elementos de un array es bastante simple, sólo basta con especificar el índice del elemento que queremos manipular, por ejemplo:

``` ruby
puts first_array[1]
```

El número `1` significa que acabamos de acceder al segundo elemento de la lista (recuerda que en la mayoría de los lenguajes de programación, los arreglos comienzan con el índice `0`).

## Manejo de Arrays
-------------------

Existen varios métodos que nos simplifican bastante el trabajo con arrays, algunos se especifican a continuación:

``` ruby
# Imprimir el primer elemento de un array
puts first_array.first

# Imprimir el último elemento de un array
puts first_array.last

# Imprimir los N primeros elementos del array
puts first_array.take(N)

# Imprimir desde el elemento N+1 hasta el último elemento del array
puts first_array.drop(N)

# Determinar el largo de un array
puts first_array.length
puts first_array.count
puts first_array.size

# Determina si un array está vacío o no (retorna true o false dependiendo del caso)
puts first_array.empty?

# Agrega la cadena "Rails" al final del array (pueden ser elementos de cualquier tipo)
second_array.push("Rails")

# Agrega la cadena "Laravel" en el índice 1 (el elemento que estaba en dicha posición será desplazado a la posición siguiente)
second_array.insert(1,"Laravel")

# Eliminar el último elemento del array
second_array.pop

# Eliminar el primer elemento del array
second_array.shift

# Elimina el elemento que se encuentra en la posición i
second_array.delete_at(i)
```
