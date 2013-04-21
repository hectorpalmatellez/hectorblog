---
layout: post
title: "@font-face en Firefox"
date: 2013-04-21 15:11
comments: true
categories: aprendiendo
tags: [css, font-face, Firefox, crossbrowser, css3]

---
Estaba revisando un sitio que armé en base a [Foundation](http://foundation.zurb.com/ "Responsive Framework bacán") y caché que en Firefox había un error: usé una fuente con íconos y en Chrome se veían bien, pero en Firefox sólo veía cuadraditos vacíos.
Me puse a googlear un poco y llegué a [un artículo de Stack Overflow](http://stackoverflow.com/questions/11872404/font-awesome-not-properly-displaying-on-firefox-how-to-vend-via-cdn?lq=1) donde se habla del uso de **@font-face** en Firefox cuando el sitio usa un CDN, como el prototipo que me dio el problema del que escribo ahora.
<!--more-->
##La solución
Resulta que cuando usas un CDN, como hago en el sitio que menciono, cambia la URL desde donde llamas a los archivos que crean y _pintan_ la página que se visita, por lo que cuenta como un dominio externo, cosa que Firefox no permite.
Para solucionarlo, debes crear un `.htaccess` en la carpeta donde están todas las fuentes que estés llamando, en todas sus extensiones (te apuesto que la tuya se llama `fonts`, como la mía).
El contenido de este `.htaccess` es el siguiente:

{% include_code .htacccess a crear lang:apache font-face-firefox.html %}

Luego de eso, Firefox debería dejar que se haga **@font-face** desde cualquier dominio.
Si no quedó claro, puede revisar [en este otro artículo](http://www.red-team-design.com/firefox-doesnt-allow-cross-domain-fonts-by-default "Firefox doesn’t allow cross-domain fonts") (en inglés).

###Recursos
{% img left /images/fontello.png 240 "Fontello" "Pantallazo de Fontello" %} Si necesitas fuentes con íconos, recomiendo [Fontello](http://www.fontello.com/) donde puedes crear un archivo con los caracteres que necesites. Después exportas lo necesario para hacer el proceso donde necesites.
Por ejemplo, [en este mismo sitio](/) lo tengo para los íconos de redes donde tengo cuentas (visible a la derecha, en el _sidebar_ y en el _footer_).

####CDN
En CDN no tengo mucha experiencia, pero una vez leí que es bacán para sitios con harto tráfico. Otra vez, varios meses después, caché que había una oferta para comprar 1 TB de tráfico en MaxCDN por 1 dólar, así que usé algo de lo poquito que me quedaba en Paypal para eso. Meses después, me di cuenta que en realidad nunca lo necesité, porque no he gastado ni 1 GB. De todas maneras, lo tengo a mano para usarlo cuando me salga algo en donde necesite que se cargue todo más rápido (porque sí comprobé que acelera la descarga de un sitio).


##Conclusión
Si queda alguna duda, están los comentarios y las otras vías por donde contactarme. Saludos cordiales y un abrazo a todos. _Carpe Diem_, _Memento mori_, _Wingardium leviosa_ y esas cosas bonitas que dice la gente que lee harto.
