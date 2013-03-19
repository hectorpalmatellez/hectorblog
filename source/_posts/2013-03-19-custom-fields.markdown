---
layout: post
title: "Custom fields o campos personalizados en Octopress"
date: 2013-03-19 02:00
comments: true
categories: aprendiendo
tags: octopress, ruby, campo personalizado, custom field
customizado: '<span style="color: red">las vacas son bonitas</span>'
customizado2: hola, soy customizado 2

---
La pregunta que se me ocurrió era como:
> ¿Y cómo creo campos personalizados para hacer más bonitamente dinámicas las publicaciones?

Resulta que un poco de lógica y varios intentos de _googleo_ me llevaron a intentar algo parecido a lo que sale [acá](https://github.com/mojombo/jekyll/wiki/yaml-front-matter#custom-variables "YAML Front Matter en GitHub"), en el apartado de «variables personalizadas» se explica con el siguiente ejemplo:

{% include_code Ejemplo lang:ruby custom.rb %}
<!--more-->

{% img left /images/campo-customizado.png "Ejemplo de campo personalizado" "Campo customizado en el header del archivo markdown" %} Así que decidí probar un poquito y creé `customizado` en el encabezado del archivo .markdown
El paso siguiente es hacer que desde la plantilla pueda ser visible, para esto hay que ir a `source/_layouts/post.html` (porque el layout que tengo para los posts es ese, obviamente). Eso se puede ver en la segunda imagen de este post.
{% img left /images/layout-customizado.png 'Ubicación de donde se mostrará el campo' 'Ubicación en post.html donde va el campo personalizado' %}

Entonces, los pasos se reducen a lo siguiente:

+ Definir el nombre y valor del campo en el encabezado del artículo `.markdown`.
+ Editar el _layout_ correspondiente para mostrar el valor del campo personalizado.
+ Queda opcional, obviamente, el estilo que se le quiera dar, por si le querís poner una clase.

##Probando

* Si el campo personalizado va a tener HTML, como para darle una clase o alguna etiqueta específica (cosa que también se puede predefinir desde el _layout_), el valor debe ir entre apóstrofos:
{% include_code Ejemplo lang:html custom-html.html %}
(Deben ser apóstrofos porque con comillas dobles no me funcionó. Quizás algún día sepa por qué).

* El campo puede ser utilizado en el cuerpo del artículo como se hace en el ejemplo en Ruby usado más arriba. Tan simple como añadir lo siguiente entre el texto escrito:
{% include_code customizado2 lang:ruby customizado2.rb %}
Esta es la razón por la que encontré más fácil llamar los pedazos de código desde archivos externos a escribirlos de la forma corriente en la que se escribe código dentro de un post.

###ALGO TERRIBLE
Todavía no hago funcionar los tags. Los agrego en cada post, pero quedan feítos. De ahí veo si los logro corregir de alguna forma más _kawaii_~

Eso nomás por ahora–
