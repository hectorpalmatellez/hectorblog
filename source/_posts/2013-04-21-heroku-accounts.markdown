---
layout: post
title: "Usando Heroku accounts"
date: 2013-04-21 17:21
comments: true
categories: aprendiendo
tags: [git, heroku, push, master, accounts, terminal]

---

[{% img left /images/heroku-accounts.png 320 "Heroku Accounts en GitHub" "Pantallazo a Heroku Accounts en GitHub" %}](https://github.com/ddollar/heroku-accounts) Este blog está _hosteado_ en [Heroku](https://www.heroku.com/ "Ofrece hosting gratuito para aplicaciones en varios lenguajes"). Heroku es bacán, **pero**, como es gratis, hay limitaciones. Dentro de la que más me llega, por ser principiante en estas cosas, está la de **máximo de 5 aplicaciones por cuenta**. Una vez hasta envié un correo a soporte preguntando cómo puedo hacer para poder tener más, pero ni me pescaron.
Bueno, como sea, la opción existe y se llama [heroku accounts](https://github.com/ddollar/heroku-accounts "Heroku Accounts en GitHub").
<!--more-->
##Paso a paso
Entonces, el problema es el siguiente:
	
Tienes una cuenta de Heroku, pero eres muy activo, así que ya ocupaste tu límite de aplicaciones. **¿Qué hacer?** Podría ser pagar para tener más aplicaciones, pero no encontré en el sitio dónde estaba eso más explícito, así que llegué a la herramienta que le da el título a este post.
Lo que hace `heroku accounts` es dejarte usar más de una cuenta de Heroku, así tienes muchas posibilidades de 5 aplicaciones a la vez. Esta _partición_ puede ser hecha por si tienes diferentes clientes o por si tienes varias aplicaciones que se quedan dentro de un mismo proyecto, por ejemplo.

Luego de haberte creado las cuentas e instalado `heroku accounts`, debes tener ciertos archivos siempre en mente. Creo que el que más problemas me dio por haberlo olvidado fue `~/.ssh/config`, que es donde defines la información para cada cuenta:

* Cómo se llama la cuenta
* Dónde está la llave
* El Hostname
* El nombre de usuario

Un ejemplo de cómo sería este archivo a continuación:

{% include_code Ejemplo de config para heroku accounts config.rb %}

Me parece que es bastante claro qué va en qué lugar, ¿cierto?

##Comandos útiles

* Para saber qué cuentas tienes en tu archivo `config` (o sea, que ya has configurado). Debes escribir `heroku accounts`.
* Para cambiar de cuenta, simplemente debes utilizar `heroku accounts:set nombre-de-cuenta`.
* Más hay en [la documentación](https://github.com/ddollar/heroku-accounts).

Con eso, ya hay para hacer los cambios pertinentes, tomando en cuenta que las autentificaciones funcionan. Si no funcionsen, es cosa de ir a [revisar la documentación de Heroku sobre las llaves](https://devcenter.heroku.com/articles/keys "Sobre las llaves en Heroku").

¿Te sirve? ¿No? Puedes decirme algo en los comentarios, si toca.