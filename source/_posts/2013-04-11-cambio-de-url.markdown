---
layout: post
title: "Cambio de URL"
date: 2013-04-11 02:23
comments: true
categories: blog

---
Originalmente este blog estaba en cualquier subdominio de **tiuque.cl**. Lo configuré así después de ver el tutorial de Octopress alojado en Heroku.
También en el principio la idea era usar el blog sólo para escribir de Octopress, pero eso es demasiado monotemático. Así que ahora está en **hector.palmatellez.cl** para que parezca que son pensamientos míos.

<!--more-->
{% img /images/settings-heroku.png %}
##Detalles sobre el cambio de URL

Cosas a tomar en cuenta a la hora de cambiar de URL un Octopress alojado en Heroku:

* Cambio desde las **opciones de la app en Heroku**. En la sección _Domains_ hay que agregar el subdominio que escojamos.
*  Crear [cambio en los DNS](https://devcenter.heroku.com/articles/custom-domains "Documentación de Heroku explicando cambios en DNS para apuntar a Heroku") de nuestro administrador del dominio. En mi caso, el hosting. Es fácil y rápido el cambio, pero no instantáneo. A mí me desesperó que fuera más de 6 horas. Obviamente, el sitio seguirá pudiendo ser visto desde **[nombredelaapp].herokuapp.com**.
* **Disqus** — es importante porque los comentarios dejan de funcionar cuando estás en el nuevo dominio, por lo que hay que ir nuevamente.

##¿Y ahora qué viene?

Ahora yo quiero tratar de escribir más. De cualquier cosa relacionada con lo que me tinque escribir.
Espero publicar cuestiones seguido acá, aunque no consiga tantos millones de visitas.