---
layout: post
title: Instalación de Ruby
tags: Ruby
eye_catch:
---

En este segundo capítulo del curso de Ruby (si no has visto el primer capítulo, has clic [aquí](http://nisoto.github.io/2017/03/13/introduccion-ruby/)) aprenderás a instalar Ruby en tu computadora y a utilizar la famosa **"Consola Interactiva de Ruby"** (en inglés Interactive Ruby Shell, que suele abreviarse como **IRB** o **irb**) la cual viene incluida en dicha instalación. Cabe destacar que la instalación se desarrolla en un computador con una distribución Linux, específicamente Ubuntu en su versión 14.04 LTS, por lo que si posees otro sistema operativo (como Windows o Mac OS) te invito a que visites [gorails](https://gorails.com/setup/ubuntu/14.04) y selecciones el sistema operativo y versión adecuada para ti.

<!--more-->

## Instalación
--------------

Lo primero que debemos hacer es instalar algunas dependencias para Ruby:

```
sudo apt-get update
sudo apt-get install git-core curl zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev python-software-properties libffi-dev nodejs
```

Ahora podemos comenzar con la instalación de Ruby, donde tendremos 3 métodos distintos: **rbenv**, **rvm** o de **fuente**. Cada uno tiene sus propias ventajas, aunque la mayoría de los programadores hoy en día prefiere hacerlo mediante rbenv por sobre rvm y de fuente (aquí verás las 3 formas). Personalmente te recomiendo que lo hagas mediante rbenv si eres nuevo en el mundo de este lenguaje.

### Instalación con rbenv

Instalar con `rbenv` es un proceso muy fácil que consta de sólo 2 pasos: instalar `rbenv` y luego `ruby-build`.

```
cd
git clone https://github.com/rbenv/rbenv.git ~/.rbenv
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(rbenv init -)"' >> ~/.bashrc
exec $SHELL

git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build
echo 'export PATH="$HOME/.rbenv/plugins/ruby-build/bin:$PATH"' >> ~/.bashrc
exec $SHELL

rbenv install 2.4.0
rbenv global 2.4.0
ruby -v
```

### Instalación con rvm

La instalación con `rvm` es un poco más sencilla que con `rbenv`:

```
sudo apt-get install libgdbm-dev libncurses5-dev automake libtool bison libffi-dev
gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
curl -sSL https://get.rvm.io | bash -s stable
source ~/.rvm/scripts/rvm
rvm install 2.4.0
rvm use 2.4.0 --default
ruby -v
```

### Instalación de fuente

Posiblemente la instalación menos útil de Ruby es desde código fuente, pero dejaré los pasos de todos modos:

```
cd
wget http://ftp.ruby-lang.org/pub/ruby/2.4/ruby-2.4.0.tar.gz
tar -xzvf ruby-2.4.0.tar.gz
cd ruby-2.4.0/
./configure
make
sudo make install
ruby -v
```

Una vez que hayas instalado Ruby utilizando cualquiera de los 3 métodos anteriores, el último paso es instalar Bundler:

```
gem install bundler
```

Si instalaste Ruby mediante `rbenv` deberás ejecutar el siguiente comando después de haber instalado Bundler:

```
rbenv rehash
```

## Consola Interactiva de Ruby
------------------------------

Una vez instalado Ruby, sólo debes abrir la terminal (`Ctrl`+`Alt`+`T`) y escribir `irb` para ingresar a la **"Consola Interactiva"** que incluye este lenguaje:

```
irb
irb(main):001:0>
```

A modo de ejemplo crearemos nuestro primer programa, el típico "Hola Mundo" por pantalla:

``` ruby
irb(main):001:0> puts "Hola Mundo"
```

Si ahora presionas la tecla **Enter** te darás cuenta de que el mensaje que acabas de escribir será mostrado por pantalla, e inmediatamente la consola quedará a la espera de una siguiente instrucción:

``` ruby
irb(main):001:0> puts "Hola Mundo"
Hola Mundo
=> nil
irb(main):002:0>
```

La consola interactiva de Ruby te servirá bastante si estás aprendiendo a utilizar este lenguaje o si quieres realizar pruebas, pero a la hora de desarrollar programas más elaborados, lo recomendable es utilizar algún editor de texto como sublime text o atom, y luego ejecutar dicho programa por consola utilizando el siguiente comando:

```
ruby hola_mundo.rb
```

Donde hola_mundo corresponde al nombre del programa y `.rb` es la extensión de Ruby (así como `.c` lo es para el lenguaje C y `.py` lo es para Python).
