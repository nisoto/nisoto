---
layout: post
title: Comandos para la terminal de Linux
tags: GNU/Linux Ubuntu
eye_catch:
---

En este apartado verás los comandos básicos de GNU/Linux para su utilización en una terminal o consola. Cabe destacar que la distribución utilizada es Ubuntu en su versión 14.04 LTS.

<!--more-->

## Introducción
---------------

Un intérprete de comandos es un programa que toma la entrada del usuario (como las órdenes que teclea, por ejemplo), y las traduce a instrucciones. Podemos compararlo con el **COMMAND.COM** de MS-DOS.

En cualquier distribución Linux tendremos la **terminal** o **consola**, que abre un shell o intérprete de comandos. En Ubuntu podemos abrirla de dos formas distintas: la primera es buscando en el Dash mediante el comodín "terminal", mientras que la segunda es pulsando la combinación de teclas `Ctrl`+`Alt`+`T`.

## Nociones básicas
-------------------

Cuando tecleamos una orden, el intérprete de comandos sigue una serie de pasos:

1. Busca el nombre de la orden y comprueba si es una orden interna.
2. Comprueba si la orden es un alias, es decir, un nombre sustitutorio de otra orden.
3. Si no se cumple ninguno de los casos anteriores, busca el programa correspondiente y lo ejecuta.
4. Si el intérprete de comandos no puede encontrar la orden que hemos tecleado, muestra un mensaje de error.

El formato general de una orden en Linux es:

```
comando [-opciones] [argumentos]
```

A la hora de introducir los comandos hay que tener en cuenta las siguientes características:

* Los comandos hay que teclearlos exactamente.
* Las letras mayúsculas y minúsculas se consideran como diferentes.
* En su forma más habitual, el sistema operativo utiliza un signo de `$` para indicar que está preparado para aceptar comandos, aunque este carácter puede ser fácilmente sustituido por otro u otros elegidos por el usuario. En el caso de que el usuario acceda como administrador (root), este signo se sustituye por `#`.
* Cuando sea necesario introducir el nombre de un fichero o directorio como argumento a un comando, Linux permite escribir las primeras letras del mismo y realiza un autorrelleno al presionar la tecla `Tab`. Si no puede distinguir entre diversos casos rellenará hasta el punto en el que se diferencien.

La terminal guarda un historial de los últimos 500 comandos ejecutados en ella y tenemos varias formas de acceder a ellos rápidamente. Es muy útil para comandos largos, que no recordamos con certeza o para asegurarnos de que la sintaxis es correcta. Para acceder a estos comandos, utilizaremos la tecla `flecha arriba` para buscar el comando hasta encontrarlo, y `flecha abajo` para volver.

Para ver el historial completo en la terminal ejecutamos:

```
history
```

Ahora, si queremos ver los últimos N comandos, ejecutaremos:

```
history N
```

Si por esas casualidades de la vida quisiéramos limpiar el historial completo, ejecutamos:

```
history -c
```

## Comandos
-----------

Mostrar los archivos que se encuentran en la ruta actual:

```
ls
```

Mostrar la ruta del directorio en el cual nos encontramos:

```
pwd
```

Crear un directorio (o carpeta):

```
mkdir NombreDirectorio
```

Entrar a un directorio:

```
cd NombreDirectorio
cd /etc/apt
```

Volver al directorio anterior:

```
cd ..
```

Ir a la ruta /home/tu_usuario (carpeta o directorio **principal**):

```
cd
```

Eliminar un archivo o directorio:

```
rm NombreDirectorio
rm NombreArchivo
```

Eliminar un directorio que contenga archivos y/o directorios:

```
rm -r NombreDirectorio
```

Eliminar un directorio vacío:

```
rmdir NombreDirectorio
```
