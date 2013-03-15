---
layout: post
title: "Octopress"
date: 2013-03-14 01:15
photo: http://o.tiuque.cl/img/octopress.png
comments: true
categories: 
- aprendiendo
tags:
- ruby
- Jekyll
- Octopress
- Terminal

---
##Cachando cómo usar Octopress

	Es bacán.
– [Álex](http://twitter.com/Kyuumeitai "Twitter del Álex")

Esa fue la primera opinión que escuché sobre Octopress, antes de eso ni cachaba que existía. Había [leído sobre Jekyll](http://ajipirijou.com/blog/ahora-usamos-jekyll "Artículo de @elJOjo cuando se pasó de WordPress a Jekyll"), pero hasta ahí nomás entendía.

<!-- more -->
{% img left http://placekitten.com/320/250 Place Kitten #2 %}
![Octopress](http://o.tiuque.cl/images/octopress.png "Imagen de Octopress")
Le estoy haciendo modificaciones, para entender bien cómo es la estructura de los archivos que componen el resultado final, lo que viene después del *rake generate*.
Aparte de eso, **tengo que aprender a escribir en [Markdown](http://daringfireball.net/projects/markdown/basics "Artículo sobre el Markdown")**, menos mal que [Mou](http://mouapp.com/) ayuda harto.

##Investigación (o *googleo* común)

Resulta que me molesta un poquitín que no se pueda traducir todo de una, ya que, si se cree tan bacán, Octopress debería tener algo para moverse con la [i18n](http://es.wikipedia.org/wiki/Internacionalizaci%C3%B3n_y_localizaci%C3%B3n "Artículo en Wikipedia donde se explica qué es la internacionalización"). **¿Por qué no tendrá un .MO y un .PO?** Con [Poedit](http://www.poedit.net/ "Herramienta usada en traducción de plugins y themes de WordPress y otras cuestiones que vengan hechos para ser traducidos") se podría arreglar todo bonito rápidamente. [Hace 17 días](https://github.com/imathis/octopress/issues/451 "Issue de un alemán que quiere traducir su instalación de Octopress") se dijo que no va a ir en una versión próxima, ASÍ QUE NO IMPORTA, TOTAL IGUAL SE PUEDE METER MANO A TODO Y ESPERAR QUE NO EXPLOTE.

###Cosas bacanes
* Es _responsive_ (¡Eeeeeeeh!).
* Es fácil entender cómo funciona y qué crea al regenerarse con los últimos cambios aplicados.
* Los _widgets_ que trae son fáciles de activar y configurar.
* Configurar el dominio no fue tan complejo, sólo tuve que usar [Heroku](http://www.heroku.com/ "Hosting de aplicaciones muy bonito y simpático"), creando la aplicación desde el Terminal, [como te indican en la documentación](http://octopress.org/docs/deploying/heroku/) y en [la documentación de Heroku](https://devcenter.heroku.com/articles/custom-domains) está la explicación para que el dominio apunte para allá y todo se vea profesionalmente bacán. 

###Cosas que le faltan (o _no bacanes_)
* ¿Podría tener una imagen destacada por cada post? No encontré que se abordara el tema en lo básico.
* No me gustó que lo de los tags no viniera activado por defecto. Espero que no sea tan difícil de aplicar/configurar.
* ESONOMÁS.


##Cambios agregaos a la mala
* Traducir detalles en `source/_layouts/post.html`. Con eso ahora dice «Comentarios», «Escrito por» y… otras cosas.
* Crear el `twitter.html` en `asides` para insertar los últimos tuiteos.
* Creación de `tags.html` en `source/_includes/post/` para llamar a los tags incluidos en el `.markdown` del post, aunque todavía no enlazan como las categorías. **Falta esfuerzo**.
* En `source/_includes/custom/navigation.html` está el menú principal. Traduje los enlaces que habían y le agregué mi Twitter, porsiaca.

