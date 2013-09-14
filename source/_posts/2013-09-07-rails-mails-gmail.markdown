---
layout: post
title: "Usar Gmail para que Devise en Rails envíe correos"
date: 2013-09-07 12:41
comments: true
categories: ror

---

{% img left /images/development.rb-mailer-gmail.png 400 %} Estuve buscando una solución simple para crear un sistema que funcione bien y no tan complejo de entender en una aplicación hecha en **Ruby on Rails**, así es como llegué a `devise`. Esta parece tener un nivel alto de aceptación, aunque no tiene actualizaciones hace harto rato. Obvio que saltan problemas y soluciones pre-armadas, como lo que pasa cuando olvidas tu contraseña y deseas re-crearla. `devise` ya trae todas las _views_ que uno podría necesitar (en `app/views/devise/`, si hiciste `$ rails generate devise:views`).
<!-- more -->
##«Todo está listo, pero no»

Sin problema pude generar el sistema de registro y logueo, un par de comandos y listo. Casi _a prueba de tontos_. Luego vino la parte donde me pregunté sobre el botón de **Recuperar Contraseña**, porque las `views` lo incluyen, lo probé y no funcionó :(

###Recuperar contraseña con `devise`

La vista está en `app/views/devise/passwords/new.html.erb` y casi no hay que tocar nada. Yo traduje un par de cuestiones nomás, aunque hay cosas que se traducen usando el [i18n de devise]("https://github.com/plataformatec/devise/wiki/I18n").

En `config/environments/development.rb` van los datos que se usan para acceder a Gmail, utilizando los datos de acceso (la primera imagen de este post). Para que funcionase en local (obvio, porque es `development.rb`). De acuerdo a la teoría que busqué, era posible no tener que poner la información en texto plano explícito en ese archivo, usando _environmental variables_, como dice [Old Man Coder](http://stevechristie.tumblr.com/post/35158776548/how-to-set-up-local-environmental-variables), sin embargo, me fue más fácil que funcionara en Heroku (`production.rb`), que en el local. Pa' qué darle tanta vuelta, si la cosa anda.

El de producción queda así:
		
	config.action_mailer.smtp_settings = {
  		address: "smtp.gmail.com",
  		port: 587,
  		domain: ENV["GMAIL_DOMAIN"],
  		authentication: "plain",
  		enable_starttls_auto: true,
  		user_name: ENV["GMAIL_USERNAME"],
  		password: ENV["GMAIL_PASSWORD"]
  	}

Algo útil es que no necesariamente tiene que ser un correo _@gmail.com_, ya que yo probé con uno que utiliza Google Apps y anda súper igual.

##Crear _environmental variables_ para Heroku

**Heroku** lo explica súper bien en [su Devcenter]("https://devcenter.heroku.com/articles/config-vars"), pero el paso exacto dado por mí fue el siguiente:

	heroku config:add GMAIL_USERNAME=CORREO@GMAIL.COM GMAIL_DOMAIN=gmail.com GMAIL_PASSWORD=CONTRASEÑA
	
Se explica solito.

##Ya, ¿y?

Después de esos pasos, falta revisar que nuestro `production.rb` tenga lo siguiente:

	config.action_mailer.default_url_options = { :host => 'http://APP.herokuapp.com' }
	config.action_mailer.delivery_method = :smtp
	config.action_mailer.smtp_settings = {
  		address: "smtp.gmail.com",
  		port: 587,
  		domain: ENV["GMAIL_DOMAIN"],
  		authentication: "plain",
  		enable_starttls_auto: true,
  		user_name: ENV["GMAIL_USERNAME"],
  		password: ENV["GMAIL_PASSWORD"]
  	}

En la primera debe ir el nombre con la URL de tu aplicación. Si utilizas un dominio asignado, sin el `herokuapp.com`, debe ir ese dominio ahí.

Con eso ya debería funcionar todo. Gracias a Google y a todos los amiguitos que lo hicieron posible n.n