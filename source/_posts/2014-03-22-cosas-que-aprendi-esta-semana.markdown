---
layout: post
title: "Cosas que aprendí esta semana"
date: 2014-03-22 21:16
comments: true
categories: aprendiendo
tags: [php, jekyll, assemble, scss, sprites, include, mailrox]

---
Hay varias cosas que quizás debería haber aprendido antes sobre lo que hago, por varias razones las aprendí esta semana, que ya termina. Voy a tratar de enumerarlas para que no se me olvide que las aprendí esta semana:
<!--more-->

#### PHP tiene un servidor de desarrollo que se puede abrir desde Terminal

{% img left /images/php-dev-server.png 350 "Servidor de desarrollo de PHP" %} 
 Este se abre así `$ php -S localhost:8000`. Va `localhost` porque eso es lo que vamos a escribir en el navegador cuando estemos probando esos PHP con includes penquitas. Lo que va después de los dos puntos es el puerto que le designemos. Funciona altiro (por lo menos con `PHP 5.4.24` que es el que tengo ahora).

#### Hay una herramienta bacán y gratuita para armar mails

{% img right /images/mailrox.png 350 "Mailrox" %}Está en Beta, por lo que probablemente algún día cercano cierre las cuentas existentes o las limite, por ahora, hay que aprovechar: [Mailrox](https://www.mailrox.com/) se llama el servicio que permite en el mismo navegador hacer los cortes y arreglos necesarios para que el mail quede _armado_ de acuerdo a los estándares necesarios para que se vea bien en todos lados. Además, tiene varias _features_ que aún no he probado, como la de trabajo colaborativo. En caso de que uno sea fijón e incrédulo producto de haber trabajado con Dreamweaver, por poner un ejemplo traumático, también existe la posibilidad de meterle mano al código a través del `WYSIWYG`.  

#### Sprites con SCSS

Entendía el concepto detrás de los sprites al usar [Compass](http://compass-style.org/), pero nunca me dediqué a entender cómo funcionaba y cómo y dónde aplicarlo. Creo ahora entenderlo y ya lo he usado en un par de miniproyectos personales. Porsiaca, se [explica acá](compass-style.org/help/tutorials/spriting/ "Tutorial del uso de sprites en Compass").

#### Usar _includes_ en HTML con Assemble

En los proyectos con [Yeoman](http://yeoman.io/) siempre me daba un poquito de lata cuando necesitabas incluir el mismo header y el mismo footer en todas las páginas, después, si había una variación, había que andar buscando todos los `.html` para corregir. Una lata.
Eso era al usar el generador llamado `webapp`, sin embargo, existen hartos [generadores hechos por la comunidad](http://yeoman.io/community-generators.html), además de [los generadores oficiales](http://yeoman.io/official-generators.html). 

Entre los de la comunidad se encuenta el `generator yawa`[[1]](https://github.com/p-j/generator-yawa). Este incluye algo muy bonito llamado [Assemble](http://assemble.io/). **Assemble** hace algo similar a [Jekyll](http://jekyllrb.com/), pero utilizando magias de Javascript y no de Ruby. Lo más básico es la existencia de una carpeta dentro de `app` llamada `templates`, ahí hay: `layouts`, `pages` y `partials`.
  
En `app/templates/layouts` estará la principal llamada `default.hbs`, en `app/templates/pages` debería estar `index.hbs` y las demás uno las va creando.

Para llamar un _partial_, después de crearlo en su directorio correspondiente, debe hacerse el llamado desde la plantilla o página necesaria utilizando: `{{> nombre-partial }}`. O por lo menos así me funcionó a mí.

___

De eso nomás me acuerdo que aprendí esta semana. No fue tan poco, ¿cierto?
Ya, si fue poco, da lo mismo. Pa' mí fue harto.
