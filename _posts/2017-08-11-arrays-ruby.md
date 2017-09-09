---
layout: post
title: Arrays en Ruby
tags: Ruby
eye_catch:
---

En este sexto capítulo del curso de Ruby (si no has visto el capítulo anterior has clic [aquí](https://nisoto.github.io/2017/08/10/entrada-y-salida-ruby/)) aprenderás a utilizar una de las estructuras de datos más utilizadas en el mundo de la programación: los arrays (arreglos en español). A pesar de que en la mayoría de los lenguajes de programación los array permiten almacenar información de un mismo tipo, en Ruby es algo distinto.

<!--more-->

## Array
--------

Un Array es un contenedor donde podemos almacenar datos (o elementos) y, a diferencia de muchos otros lenguajes de programación, éstos pueden ser de distinto tipo. Cabe destacar que en Ruby (y en Python) a un array se le conoce también como **list** (lista en español).











Como crear un array??

first_array = []

Existe otra manera!

second_array = Array.new

Si ahora los imprimimos:

puts first_array.to_s
puts second_array.to_s

[]
[]

Ahora almacenaremos información en un array:

first_array = ["Ruby", "Python", "JavaScript"]

Cómo acceder? -> accediendo a su índice! ejemplo

puts first_array[0]

Existen varios medodos:

puts first_array.first -> imprime el primer elemento

puts first_array.take(N) -> mostrará los N primeros elementos de la lista

puts first_array.drop(N) -> mostrará desde el término N+1 al último término de la lista

puts first_array.length -> largo del array!

puts first_array.empty? -> retorna true si está vació y false si no lo está

second_array.push("Rails") -> agrega una casilla (elemento) al final de la lista

Lo bueno de esto es que podemos almacenar información de cualquier tipo!!

Existe otro método para agregar elementos!!

second_array.insert(INDICE,ELEMENTO)

second_array.insert(1, "Laravel") --> el elemento que esté en la posición 1 será desplazado a la posición siguiente (2)

second_array.pop -> elimina el último elemento de la lista!

second_array.shift -> elimina el primer elemento de la lista!!

second_array.delete_at(INDICE) -> elimina el elemento en la posición I
second_array.delete_at(2)