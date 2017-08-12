---
layout: post
title: Primeros pasos en Ruby on Rails
tags: Ruby Ruby-on-Rails RoR
eye_catch:
---

En este tercer capítulo del curso de Ruby on Rails (si no has visto el primer capítulo, has clic [aquí](https://nisoto.github.io/2017/04/28/instalacion-y-configuracion-ruby-on-rails/)) aprenderás todas las bases teóricas respecto a Rails que te permitirán configurar de manera inicial una aplicación.

<!--more-->

## Crear un proyecto
--------------------

Una vez instalado Ruby y Ruby on Rails en nuestra computadora, crearemos un nuevo proyecto, para ello ejecutamos el siguiente comando en la terminal:

```
rails new myapp
```

Rails inmediatamente comenzará a crear varias carpetas y archivos necesarios para el proyecto (tales como app, db, config, Gemfile, etc.), y por último, instalará las **Gemas** por default. Acabo de mencionar un término que tal vez no conozcas; en Rails, las **gemas** (gems) son el equivalente a las librerías en otros lenguajes, es decir, código predefinido, las cuales se alojan en un fichero llamado Gemfile.

Un punto importante a la hora de crear un proyecto es el gestor de bases de datos a utilizar. En el caso anterior no se especificó ninguna, por lo que Rails por defecto utilizará sqlite3 (el cual viene instalado junto con nuestro sistema operativo). Si quisiéramos utilizar otra (como MySQL, por ejemplo) debemos agregar lo siguiente al final:

```
rails new myapp -d mysql
```

Lo mismo ocurrirá si quisiéramos utilizar PostgreSQL:

```
rails new myapp -d postgresql
```

Una vez creado nuestro proyecto, para ingresar a él ejecutamos el comando:

```
cd myapp
```

Y luego utilizamos:

```
ls
```

Para visualizar todas las carpetas y ficheros que contiene.

## Estructura de un proyecto
----------------------------

Si ejecutamos el comando `ls` dentro de la carpeta de nuestro proyecto podremos visualizar todas las carpetas y ficheros, los cuales poseen la siguiente estructura:

```
app
bin
config
db
lib
log
public
test
tmp
vendor
.gitignore
Gemfile
Gemfile.lock
README.md
Rakefile
config.ru
```

El significado de cada directorio o fichero se detalla a continuación:

* `app/`: dentro de este directorio hay varios subdirectorios, donde se destacan el modelo (`models`), la vista (`views`) y el controlador (`controllers`), es decir, el patrón MVC.
* `config/`: este directorio contiene los principales ficheros para configurar la aplicación, es decir, la configuración de la base de datos (`database.yml`), la estructura de su entorno (`environment.rb`) y las rutas (`routes.rb`), entre otros.
* `db/`: dentro de esta carpeta se encuentra la estructura de la base de datos, es decir, todas las tablas existentes con sus respectivos atributos.
* `lib/`: contiene módulos extendidos de la aplicación.
* `log/`: contiene los archivos Log de la aplicación.
* `public/`: contiene datos disponibles para los usuarios de la aplicación, tales como las hojas de estilo (`css`), imágenes, etc.
* `test/`: dentro de este directorio se encuentran todos los ficheros que nos ayudarán a realizar pruebas en la aplicación.
* `tmp/`: aquí se encuentran los archivos temporales.
* `vendor/`: contiene la tercera parte del código, tales como plugins y gemas.
* `.gitignore`: en este fichero se encuentran algunos patrones que git ignora.
* `Gemfile`: junto al fichero `Gemfile.lock`, te permiten especificar qué gemas son necesarias para la aplicación.
* `Rakefile`: este fichero localiza y carga tareas que pueden ser ejecutadas desde la línea de comandos. La lista de tareas es definida a través de los componentes de Rails.
* `config.ru`: en este fichero se encuentra la configuración Rack para servidores usados para iniciar la aplicación.

## Iniciando el servidor web
----------------------------

Nuestra aplicación de Rails ya está funcionando, lo único que nos falta es iniciar el servidor. Para ello, ejecutamos el siguiente comando en la terminal (y dentro del proyecto, obviamente):

```
rails server
```

O también:

```
rails s
```

Esto lanzará Puma, un servidor web incorporado en Rails por defecto (el cual está escrito en Ruby). Para ver tu aplicación en acción, abre tu navegador preferido y accede a [http://localhost:3000](http://localhost:3000). Deberías ver la página de información por defecto de Rails.

![holarails]({{ site.baseurl }}/assets/img/hirails!.png)

La página de bienvenida nos asegura que tenemos el software configurado correctamente. Para detener el servidor web, presiona `Ctrl` + `C` en la terminal donde se está ejecutando. Rails generalmente no requiere reiniciar el servidor web; los cambios realizados serán tomados automáticamente por el servidor.

## Hola mundo en Rails
----------------------

### Generando el controlador

Cuando accedemos a una aplicación (ya sea de escritorio o web) lo primero que vemos es algún mensaje de bienvenida. Para hacer lo mismo en nuestra aplicación debemos crear como mínimo un controlador y una vista.

Para crear un nuevo controlador, debemos ejecutar el generador de controladores y especificar el nombre de dicho controlador y luego una acción. Por ejemplo, si queremos que nuestro controlador se llame `welcome` y la acción `index`, debemos ejecutar lo siguiente:

```
rails generate controller welcome index
```

O también:

```
rails g controller welcome index
```

Rails creará una serie de archivos y añadirá una ruta por ti, donde los archivos más importantes son el controlador (que se encuentra en `app/controllers` y la vista (que se encuentra en `app/views`)

### Instalando un editor de código (IDE)

Antes de continuar, es importante mencionar que necesitarás un editor de código para que te resulte fácil programar. Es por ello que te recomiendo [sublime text 3](https://www.sublimetext.com/3) o [atom](https://atom.io/), los cuales son gratuitos y muy completos.

### Hello, Rails!

Una vez instalado tu editor de código, abre el fichero `app/views/welcome/index.html.erb` y edítalo para que contenga sólo esta línea de código (aunque puedes personalizarla a tu gusto):

``` html
<h1>Hello, Rails!</h1>
```

### Estableciendo la página principal

Lo único que nos falta es decirle a Rails cuándo queremos que se muestre `Hello, Rails!`. En nuestro caso, deseamos mostrarlo al acceder a la portada de nuestro sitio ([http://localhost:3000](http://localhost:3000)); sin embargo, la página por defecto del Framework está ocupando ese lugar.

Para realizar este proceso, lo primero que debemos hacer es borrar el archivo `index.html` ubicado dentro de la carpeta `public` de la aplicación, para luego ir a `config/routes.rb` y borrar lo siguiente:

``` ruby
get "welcome/index"
```

Y agregar:

``` ruby
root :to => "welcome#index"
```

Esta línea de código le indica a Rails que debe asociar las peticiones de la raíz de la aplicación a la acción `index` del controlador `welcome`, mientras que `get "welcome/index"` le indica a Rails que asocie peticiones de [http://localhost:3000/welcome/index](http://localhost:3000/welcome/index) a la acción `index` del controlador `welcome`.

Si ahora accedes a la dirección [http://localhost:3000](http://localhost:3000) en tu navegador, ¡Verás el mensaje `Hello, Rails!` que colocaste dentro de la vista `app/views/welcome/index.html.erb`!

![hellorails!]({{ site.baseurl }}/assets/img/hellorails.png)
