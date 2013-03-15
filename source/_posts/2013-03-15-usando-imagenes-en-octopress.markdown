---
layout: post
title: "Usando imágenes en Octopress"
date: 2013-03-15 00:08
comments: true
categories:
- aprendiendo
tags:
- imágenes
- img
- UTF-8
- es_ES
- Codificación

---
##La complicación
Resulta que al intentar agregarle imágenes al [post anterior](/aprendiendo/octopress "Post sobre empezar a usar Octopress") tuve problemas y sólo después de **varios** intentos caché que el problema era por un tema que creí haber solucionado al configurar el sistema por primera vez: **la codificación**.
<!--more-->
###Caracteres bonitos
Los hispanohablantes tenemos caracteres bonitos, como la todopoderosa **eñe**, ***las vocales con tilde*** y la **u con cremillas** (ü). Estos caracteres le hacen problema al universo en línea cuando se meten en nombres de archivos y… en todo. Por eso, al configurar el repositorio donde alojes Octopress debes adelantarte, querido hispanohablante. Esto se hace con lo siguiente:
	
	export LANG=es_ES.utf8
Luego, para verificar que quedó bien, hay que darle a:
	
	locale
Si el resultado se parece a lo siguiente, estamos bien:

	LANG="es_ES.utf-8"
	LC_COLLATE="es_ES.utf-8"
	LC_CTYPE="es_ES.utf-8"
	LC_MESSAGES="es_ES.utf-8"
	LC_MONETARY="es_ES.utf-8"
	LC_NUMERIC="es_ES.utf-8"
	LC_TIME="es_ES.utf-8"
	LC_ALL=
{% img /images/utf8-locale.png center %}

##¿Y entonces? ¿Cómo se hace?
Luego de eso, podemos insertar imágenes, como la que está arriba de este párrafo. Para eso, hay que seguir lo que dicta el _plugin_ que viene gratis dentro de Octopress desde su nacimiento. Esto se puede leer en [su documentación](http://octopress.org/docs/plugins/image-tag/ "Explicación del uso del comando para insertar imágenes en el contenido del post en Octopress"). Básicamente se trata de:

	{% img [clases asignadas] /ruta/a/la/imagen [ancho] [alto] [el title [alt de la imagen]] %}

Fueron varias horas metido en el problema, aunque debo confesar que para matar la frustración jugué un rato al [Team Fortress 2](http://store.steampowered.com/app/440/ "Juego muy bonito y enriquecedor").

Eso nomás, por ahora.