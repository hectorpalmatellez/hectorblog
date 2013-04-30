---
layout: post
title: "Push desde diferentes remotes con Git"
date: 2013-04-28 17:48
comments: true
categories: aprendiendo
tags: [git, github, terminal, iterm]

---

Actualmente este blog está _hosteado_ en [Heroku](http://www.heroku.com/), eso quiere decir que los _commits_ se hacen hacia allá, pero igual quería tener una copia con mayor visibilidad, por lo que se me ocurrió ver una forma donde pudiera hacer _commit_ a más de una fuente (o _remote_).
Actualmente puedo hacer `git push todo` para enviar las actualizaciones a Heroku y, al mismo tiempo, [a GitHub](https://github.com/hectorpalmatellez/hectorblog).

No es tan difícil.
<!--more-->
##Preparación psicológica

Como ya se ha iniciado Git en tu proyecto (**¿CIERTO?**), es cosa de ir al Terminal, o [iTerm](http://iterm.sourceforge.net/), dependiendo de qué tan bacán erís. Allí veremos si existe `.git/config`. Si no existiera, hay que crearlo.

En mi caso, el `.git/config` existía porque [uso Heroku Accounts](/aprendiendo/heroku-accounts "Explicación sobre cómo ocupar Heroku Accounts"), así que fue cosa de añadirle sólo lo siguiente:

	[remote "todo"]
    url = https://github.com/USUARIO/REPOSITORIO.git
	url = git@heroku.USUARIO:REPOSITORIO.git

El segundo tiene la sintaxis que ocupa Heroku Accounts, por eso se ve así… creo.

##Referencias

Por si no se entendiera, acá dejo dos referencias:

* [**git to multiple repositories simultaneously**](http://stackoverflow.com/questions/4255865/git-push-to-multiple-repositories-simultaneously/4255934#4255934) en Stack Overflow.
* [**Can I push to more than one repository in a single command in git?**](http://stackoverflow.com/questions/165092/can-i-push-to-more-than-one-repository-in-a-single-command-in-git/166043#166043), en el mismo sitio del anterior.

En el próximo capítulo haremos magia negra.