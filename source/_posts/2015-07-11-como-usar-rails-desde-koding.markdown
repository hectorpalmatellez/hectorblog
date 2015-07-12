---
layout: post
title: "Cómo usar Rails desde Koding"
date: 2015-07-11 15:07
comments: true
categories: rails
tags: git, koding, rails, ror

---

{% img left /images/koding/create-vm.png 350 "Crear VM" %} El problema inicial era cómo lograr instalar un entorno común de trabajo similar al que uno recrea en un Mac, pero desde Windows. Recordé que [Koding](http://koding.com/) ofrece una _VM_ gratis y se me ocurrió que podría funcionar, entonces algo así tuve que hacer:
<!-- more -->
En el plan gratuito de Koding se tiene libertad para instalar todo lo necesario. El tipo de aplicación a instalar demanda, además de Rails, tener instalado [PostgreSQL](http://www.postgresql.org/), que también coincide con ser lo gratuito que se puede tener en una aplicación en Heroku.

{% img /images/koding/create-new-vm.png "Crear nueva VM" %}

#### 1. Instalar PostgreSQL
Koding tiene un manejador propio de paquetes, a prueba de tontos, por lo que instalar PostgreSQL es súper simple:

`$ kpm install postgresql`

#### 2. Instalar Ruby y Rails
La VM en Koding ya trae Ruby instalado, pero, ya que utilizaremos una versión más actual de Rails, es necesario actualizarla, los pasos para esto son:

`$ gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3`

Luego:

`$ curl -sSL https://get.rvm.io | bash -s stable --rails` (este se demora un poco más que los otros).

Al terminar:

`$ source ~/.rvm/scripts/rvm` para actualizar lo instalado.

{% img /images/koding/ruby-rails-installed.png "Ruby y Rails instalado" %}


#### 3. Configurar Git
El proyecto en Rails ya está alojado en GitHub, por lo que parte de lo pensado es realizar cambios y hacer _commits_ desde Koding. Para identificarse en GitHub se utilizan los pasos que ellos detallan en [Generating SSH Keys](https://help.github.com/articles/generating-ssh-keys/), pero en resumen, para este caso es:

`$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"` (con el correo reemplazado, obviamente).

Esto generará dos archivos dentro de la VM: `~/.ssh/id_rsa` y `~/.ssh/id_rsa.pub`. Luego, se debe copiar el contenido de `id_rsa.pub` y guardarlo dentro de las SSH Keys autorizadas en tu propia cuenta de GitHub., estas están en: [https://github.com/settings/ssh](https://github.com/settings/ssh). Para copiar el contenido de este archivo, se puede hacer: `$ cat ~/.ssh/id_rsa.pub` y copiar este contenido en el portapapeles.
Luego ir a las SSH Keys del perfil de GitHub y pegar este contenido guardándolo con un nombre que lo identifique.
Para probar si el proceso quedó bien, se puede ejecutar: `$ ssh -T git@github.com`. Primero, pedirá permiso si se acepta agregar esa llave a la lista de _known hosts_, luego devolverá el nombre de usuario en un mensaje, con eso queda ya confirmada la conexión entre la VM y el usuario de GitHub.

{% img /images/koding/add-ssh-key.png "Agregar Key a GitHub" %}


#### 4. Clonar el repositorio
Para clonar el repositorio, hay que ir a `~/Web` y hacer `$ git clone [URL DEL REPOSITORIO] .` (con un punto al final, para que quede el repositorio en la misma carpeta y no en una con el nombre del repositorio). Lo más posible es que Git imprima este error: `fatal: destination path '.' already exists and is not an empty directory.`, esto es porque Koding genera algunos archivos en `~/Web`, que es la raíz para lo que se ve en el dominio "desde afuera", por lo que un `$ rm *` y repetir el comando de clonación del repositorio será suficiente 👌

#### 5. Rails Server
Koding siempre quedará como un entorno de desarrollo, por lo que uno normalmente ahora haría `$ rails s` para ver qué tal está el repositorio. Oh, cierto, falta el `$ bundle install`...
En caso de existir un error con la instalación de la gema `pg`, es necesario instalar una librería adicional con este comando: `$ sudo apt-get install libpq-dev`.
Luego de esto, ya será posible `$ bundle install` y `$ rails s`, sin embargo, para asegurar poder ver la VM públicamente, el comando debe ser `$ rails s -b 0.0.0.0`, con esto ya puede ser visto por cualquier persona, utilizando la IP pública que aparece en las *VM Settings* más el puerto por defecto que es normalmente el `3000`.
Al intentarlo, probablemente aparezca un error relacionado con PostgreSQL.

#### 6. Últimos detalles
Lo que falta configurar en PostgreSQL es el role con el nombre del usuario de Koding.

1. `sudo su - postgres`
2. `psql template1`
3. `CREATE ROLE [username] superuser;`
4. `ALTER ROLE username WITH LOGIN;`

Luego de esto, es necesario recrear la base de datos con `$ bundle exec rake rake db:create:all` y luego `bundle exec rake db:migrate`.

#### 7. Terminó

Luego de todos estos pasos, ya debe poder verse en la IP pública el servidor local. Los archivos se pueden editar a través de Koding y se pueden realizar commits con el usuario ya logueado.

Ahora, todo está controlado.

![Todo bajo control](http://media2.giphy.com/media/OCdsZb1Er6aeQ/giphy.gif)


 