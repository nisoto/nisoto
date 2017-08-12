---
layout: post
title: Entrada y salida de datos en Ruby
tags: Ruby
eye_catch:
---

En este quinto capítulo del curso de Ruby (si no has visto el capítulo anterior has clic [aquí](https://nisoto.github.io/2017/04/04/datos-elementales-ruby/)) verás la entrada y salida de información en lenguaje Ruby, donde aprenderás a ingresar, por ejemplo, un número o cadena desde teclado para manipularlo a tu antojo.

<!--more-->

## Entrada y salida
-------------------

A lo largo del curso hemos estado utilizando el método `puts`, por lo que seguramente te preguntarás ¿Qué diablos es eso? La respuesta es muy simple, `puts` hace referencia a imprimir o desplegar texto por pantalla, por ejemplo:

``` ruby
puts "Hola, esto es un texto"
```

Es importante destacar que el método `puts` es equivalente a:

``` ruby
put String
```

Lo que significa, como se dijo anteriormente, **imprimir texto**.

También tenemos el método `gets`, con el cual podemos recibir un texto desde el teclado, por ejemplo:

``` ruby
nombre = gets
```

Tal como ocurrre con `puts`, el método `gets` es equivalente a:

``` ruby
get String
```

## Primer programa
------------------

Ahora que hemos visto los métodos `puts` y `gets`, el siguiente fragmento de código corresponde a un programa que pregunta tu nombre y luego te saluda:

``` ruby
puts "Hola, como te llamas?"
name = gets
puts "Mucho gusto #{name}, como estas?"
```

Si ejecutas el código anterior, te darás cuenta que en la última cadena de texto ("Mucho gusto Nicolas, como estas?") habrá un salto de línea después de tu nombre. Esto se debe básicamente a que cuando ingresas el texto, también se guardará el salto de línea (al presionar la tecla `ENTER` o `INTRO` de tu teclado). Para solucionar este problema es que existe el método `chomp`, el cual elimina el último caracter de la cadena que ingreses desde teclado.

Si utilizamos el método `chomp` en el ejemplo anterior, quedaría algo más o menos así:

``` ruby
puts "Hola, como te llamas?"
name = gets.chomp
puts "Mucho gusto #{name}, como estas?"
```
