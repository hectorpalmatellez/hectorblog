---
layout: post
title: "Solucionando error H14 en Heroku"
date: 2013-05-03 09:21
comments: true
categories: heroku
tags: [git, error, heroku, rails, ror]


---

Quería instalar [Ruby on Rails](http://rubyonrails.org/ "Web Oficial") en Heroku pa' hacer un par de pruebas en mi cerebro. Pero me encontré con un problema que deriva en otros problemas:

* **Heroku no tiene sqlite3**, así que la base de datos no corre.

La solución propuesta es utilizar la gema `pg`, de [PostgreSQL](http://rubygems.org/gems/pg). La explicación sobre cómo hacerlo la hallé en [un tutorial de RailsGirls](http://guides.railsgirls.com/heroku/ "Instalar Ruby on Rails en Heroku").

**Pero** llegué a tener **error H14**, después de `heroku run rake db:migrate`. Y eso es...

<!--more-->

[Según el DevCenter de Heroku](https://devcenter.heroku.com/articles/error-codes#h14-no-web-processes-running) el Error H14 es:
	
	This is most likely the result of scaling your web dynos down to 0 dynos. To fix it, scale your web dynos to 1 or more dynos.
	
Es decir, es porque no tiene suficiente «poder». Partamos con que Heroku entrega espacio y la capacidad para correr aplicaciones usando su sistema sin cobrarte. **PERO** si tu aplicación no es tan simple, hay que agregarle _dynos_ a la ecuación y eso te cuesta plata. Lo gratuito es 1 _dyno_ (los _dynos_ son las «maquinitas» o _bots_, diría yo, que ejecutan tareas). Hay diferentes tipos, por lo que el de la base de datos no es el mismo que el que hace… otras cosas.

##La solución

Lo que traté de hacer después de cachar lo que decía el log (`heroku logs`), fue, desde el panel de administración del navegador, editar la cantidad de _dynos_, pero el panel no funcionaba. Estuve a punto de borrar la aplicación nomás, pero probé el ejemplo:

	$ heroku ps:scale web=1

Aunque resulta que yo necesitaba apagar el `worker` para prender el `web`, por lo que fue:

	$ heroku ps:scale worker=0
	$ heroku ps:scale web=1
	
Confirmamos con un `heroku open`, que abre la aplicación en la que estamos trabajando y _listoco_.

Por lo menos así solucioné mi problema.