---
layout: post
title: Instalación y configuración de Ruby on Rails
tags: Ruby Ruby-on-Rails RoR
eye_catch:
---

En este segundo capítulo del curso de Ruby on Rails (si no has visto el primer capítulo, has clic [aquí](https://nisoto.github.io/2017/04/27/introduccion-ruby-on-rails/)) aprenderás a instalar Rails (valga la redundancia) y a cómo crear una aplicación para posteriormente configurar el entorno de desarrollo sobre el que estarás trabajando a lo largo de este curso.

Es importante mencionar que antes de instalar Ruby on Rails en tu computadora, primero debes tener instalado el lenguaje de programación Ruby, por lo que si aún no lo has hecho, has clic [aquí](https://nisoto.github.io/2017/03/15/instalacion-ruby/). Una última cosa (y creo que más importante que la anterior) es que la instalación (tanto de Ruby como Ruby on Rails) se desarrolla en un computador con una distribución Linux, específicamente Ubuntu en su versión 14.04 LTS, por lo que si posees otro sistema operativo (como Windows o Mac OS) te invito a que visites [gorails](https://gorails.com/setup/ubuntu/14.04) y selecciones el sistema operativo y versión adecuada para ti.

<!--more-->

## Instalación de Ruby on Rails
-------------------------------

Lo primero que debemos hacer es instalar el lenguaje Ruby (más arriba, o dentro de mi blog, encontrarás el enlace al post). Una vez que tengas instalado Ruby de manera correcta, el siguiente paso es instalar **NodeJS**, el cual es muy importante ya que nos permitirá utilizar CoffeeScript y Asset Pipeline (más adelante veremos esos términos así que no te preocupes si no entiendes por el momento):

```
curl -sL https://deb.nodesource.com/setup_4.x | sudo -E bash -
sudo apt-get install -y nodejs
```

Por último, instalamos la gema de Rails:

```
gem install rails -v 5.0.1
```

Si instalaste Ruby mediante `rbenv` deberás ejecutar el siguiente comando una vez que se haya completado el proceso de instalación de la gema de rails:

```
rbenv rehash
```

Para corroborar que la instalación se haya realizado de forma exitosa, ejecuta el siguiente comando:

```
rails -v
# Rails 5.0.1
```

## Instalación de un gestor de bases de datos
---------------------------------------------

Rails por defecto utiliza sqlite3 como gestor de bases de datos, por lo que lo más probable es que quieras utilizar algún gestor más robusto como MySQL o PostgreSQL. En este apartado instalaremos y configuraremos PostgreSQL:

```
sudo sh -c "echo 'deb http://apt.postgresql.org/pub/repos/apt/ precise-pgdg main' > /etc/apt/sources.list.d/pgdg.list"
wget --quiet -O - http://apt.postgresql.org/pub/repos/apt/ACCC4CF8.asc | sudo apt-key add -
sudo apt-get update
sudo apt-get install postgresql-common
sudo apt-get install postgresql-9.5 libpq-dev
```

## Configuración de la base de datos y primeros pasos
-----------------------------------------------------

### Configuración previa

Lo primero que debemos hacer es crear un usuario en PostgreSQL, para ello abrimos una terminal y tecleamos lo siguiente:

```
sudo -u postgres createuser -s username
```

El siguiente paso es asignarle una contraseña al usuario que acabamos de crear, para ello debemos entrar a PostgreSQL mediante el comando:

```
sudo -u postgres psql
```

Y por último, ingresar lo siguiente:

```
\password username
```

Una vez que ingresemos el comando anterior, el gestor inmediatamente nos pedirá una contraseña y una vez que la ingresemos nos pedirá confirmar dicha contraseña. Una vez hecho todo lo anterior, debemos salir de PostgreSQL mediante el comando `\q`.

### Creación del proyecto y conexión con la base de datos

Ahora que tenemos configurado nuestro usuario PostgreSQL, crearemos un nuevo proyecto en Rails, para ello vamos a la terminal y escribimos:

```
rails new myapp -d postgresql
```

Rails inmediatamente comenzará a crear varias carpetas y archivos para tu proyecto (tales como app, db, config, Gemfile, etc.). Como pudiste darte cuenta, la frase `-d postgresql` indica que nuestro proyecto utilizará PostgreSQL como gestor de bases de datos por defecto. Si ignoras lo anterior (es decir, creas el proyecto mediante el comando `rails new myapp`), el proyecto utilizará sqlite3 (como se dijo anteriormente) ya que no le estamos especificando al framework qué gestor debe utilizar.

Para entrar a la carpeta de nuestro proyecto ejecutamos el comando:

```
cd myapp
```

Y luego utilizamos:

```
ls
```

Para visualizar todas las carpetas y ficheros que contiene.

Lo único que nos queda por hacer es modificar el fichero de configuración de la base de datos para que la conexión con PostgreSQL sea exitosa. Para ello, nos dirigimos a la carpeta config y luego abriremos el fichero llamado `database.yml`, borramos todo su contenido y pegamos lo siguiente:

```
development:
  adapter: postgresql
  encoding: unicode
  database: myapp_development
  pool: 5
  username: username
  password: password

test:
  adapter: postgresql
  encoding: unicode
  database: myapp_test
  pool: 5
  username: username
  password: password
```

El código anterior habla por sí solo. Una vez hecho esto, nos dirigimos nuevamente a la carpeta de nuestro proyecto (en la terminal) y tecleamos lo siguiente (en orden):

```
rake db:setup
rake db:migrate
```

El primer comando creará las bases de datos `myapp_development` y `myapp_test` y el segundo comando las enlazará con PostgreSQL.

Para comprobar que la conexión fue exitosa, crearemos un modelo y luego lo migraremos. Imaginemos por un momento que queremos crear un blog profesional en Rails; un blog posee artículos, y dichos artículos pueden tener uno o muchos comentarios. Dentro de la carpeta del proyecto ingresamos lo siguiente:

```
rails g model Article name:string description:text
```

En el comando anterior le estamos indicando al framework que queremos crear un modelo llamado Article que constará de 2 atributos: un nombre (de tipo string o varchar) y una descripción (de tipo text o varchar largo).

Por último, migraremos nuestro modelo:

```
rake db:migrate
```

El comando migrate enlazará nuestro modelo con PostgreSQL y creará una tabla llamada **articles** (el modelo debe ir en singular y la tabla en la base de datos en plural), el cual contendrá 5 campos, ¿Qué diablos pasó?, ¡Pero si sólo le agregamos 2 campos! La cuestión es simple: al migrar el modelo, automáticamente se crean 3 campos, un `id` (el cual corresponde a la llave primera, es autoincrementable y además de tipo `int`) y dos campos de tipo `date` (fecha) llamados `created_at` (fecha de creación) y `updated_at` (fecha de modificación).

Hemos creado el modelo Article y lo hemos migrado pero, ¿Cómo sabemos que en el gestor de bases de datos se creó correctamente la tabla articles?, ejecutemos el siguiente comando:

```
psql -U username myapp_development
```

Se nos pedirá una contraseña (la del usuario PostgreSQL) y una vez dentro ingresamos `\d` para ver todas las tablas que existen en la base de datos `myapp_development`. ¡Si aparece nuestra tabla **articles** es porque todo resultó bien!
