---
layout: post
title: Introducción a Ruby on Rails
tags: Ruby Ruby-on-Rails RoR
eye_catch:
---

En este primer capítulo del curso verás qué es primero **Ruby on Rails**, un poco de historia acerca de este Framework, su filosofía (o principios) y por último, la arquitectura con la que trabaja: El **Modelo Vista Controlador** (comúnmente abreviado MVC).

Es importante destacar que a lo largo del desarrollo de este curso se hará uso de la versión más estable hasta el momento: la 5.0 (si tienes la versión 4.2 no te preocupes ya que también sirve; en cambio, si posees alguna versión más antigua que la 4.2 es recomendable actualizar).

<!--more-->

## Ruby on Rails
----------------

Ruby on Rails (comúnmente abreviado **RoR**) es un Framework de código abierto para desarrollar aplicaciones y servicios web utilizando **Ruby** como lenguaje de programación.

Este Framework fue desarrollado por David Heinemeier Hansson (DDH) como parte de su trabajo en **Basecamp**, y fue lanzado en julio de 2004.

Lo más probable es que pienses qué tiene de especial este Framework si es tan joven, la respuesta es simple: grandes empresas y/o proyectos utilizan esta tecnología (Basecamp como se dijo anteriormente, Github, Airbnb, Twitter, etc.) por lo que a pesar de no tener más de 15 años de vida, ha cambiado y evolucionado mucho en este corto periodo de tiempo.

## Filosofía
------------

La filosofía de Ruby on Rails se basa en 2 aspectos muy importantes:

### 1. Don't Repeat Yourself (DRY)

Significa que **no deberíamos repetir código**, configuración o en otros casos hasta la documentación.

Un claro ejemplo sería que normalmente en una aplicación de Rails definimos la estructura (o configuración) de la base de datos en un solo lugar, y no en archivos externos y/o varios archivos como ocurre con otros Frameworks, logrando así ahorrar tiempo, trabajo y errores (ya que si queremos modificar algo solo debemos recurrir a dicho archivo y corregirlo).

### 2. Convention over configuration

Significa que está construido sobre **convenciones** en lugar de configuraciones, es decir, hacer lo que nosotros podríamos pensar que hace.

Para que quede más claro lo que dije en el punto anterior, un ejemplo sería que Rails cuenta con ActiveRecord, el cual nos permite comunicarnos con la base de datos utilizando objetos en lugar de sentencias SQL, es decir, **¡Nada de SQL!**.

## Arquitectura
---------------

Ruby on Rails hace uso de la arquitectura (o patrón) MVC (Model View Controller, que en español significa Modelo Vista Controlador), la cual simplifica la implementación de la aplicación dividiéndola en varias capas, donde cada una de las capas es responsable de realizar una tarea determinada.

MVC consta de 3 capas, las cuales se detallan a continuación:

* **Model:** se encarga de encapsular los datos y la lógica de negocios de la aplicación (tiene una constante comunicación con la base de datos).
* **View:** nos ayuda a construir las vistas (o interfaces), las cuales estarán en constante interacción con el cliente.
* **Controller:** se encarga de interpretar las entradas o peticiones de los clientes y también de responderlas (comunicándose ya sea con la capa Model o la capa View, dependiendo de lo que solicite el usuario).

La imagen que verás a continuación explica de una manera sencilla todo lo anteriormente explicado:

![MVC]({{ site.baseurl }}/assets/img/MVC.jpg)
