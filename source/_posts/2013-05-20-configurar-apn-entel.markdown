---
layout: post
title: "Configurar APN Entel"
date: 2013-05-20 17:38
comments: true
categories: [celulares]
tags: [APN, entel, Internet Móvil, 3G]

---

{% img left /images/ss-apn1.png 280 "Elección del APN" "APNs creados" %} Después de varios meses, decidí volver a la configuración de fábrica de mi celular, que ya no tiene el sistema operativo con el que lo compré. El **Sony Ericcson Live with Walkman** (o **WT19i**) venía originalmente con Android Gingerbread (2.3.6) y a mí se me ocurrió _flashearlo_, es decir, cambiarle el sistema operativo a Ice Cream Sandwich (4.0.4) con una [ROM](http://androidforums.com/ascend-all-things-root/339633-what-rom.html#post2712142 "What is ROM? - Androidforums.com") oficial de Sony.

Como sea, el problema, al hacer restauración de fábrica, es que se pierden varios datos con una ROM no oficial, como el APN.

<!--more-->
##¿APN?

El **APN**, o _Access Point Name_, es la información con la que tu teléfono se conecta a Internet móvil de acuerdo a lo que tu proveedor de servicios da: Edge, 3G o alguna de esas que se parecen.

###El problema

Al hacer la restauración de fábrica, el celular borra **TODO** y eso incluye la información que usaba para conectarse a Internet cuando uno anda en la micro. Para solucionarlo, hay que reingresar la información. El problema es que, por lo menos mi proveedor ([Entel](http://www.entel.cl)), no entrega tan bien la información, según yo.

Según Entel, la información a continuación es suficiente:

* Nombre: **Internet Móvil**
* APN: **bam.entelpcs.cl**
* Proxy: **no definido**
* Puerto: **no definido**
* Nombre de usuario: **entelpcs**
* Contraseña: **entelpcs**
* Servidor: no definido
* MMSC: no definido
* Proxy de mensaje multimedia: no definido
* Puerto de mensaje multimedia: no definido
* MCC: 730
* MNC: 01
* Tipo de autenticación: **PAP**
* Tipo de APN: **Internet** (en algunos Smartphones puede ser “Default” o “Default,supl”)
* Nota: Si no logras conectarte y navegar deberás ingresar proxy 10.99.0.10 y puerto 8080.

Pero a mí no me funcionó.

##Lo que me funcionó
{% img right /images/ss-apn2.png "imovil.entelpcs.cl" "APN que me funcionó" %}
* Nombre: **Internet Móvil**
* APN: <span style="color:red">**imovil.entelpcs.cl**</span>
* Proxy: **no definido**
* Puerto: **no definido**
* Nombre de usuario: **entelpcs**
* Contraseña: **entelpcs**
* Servidor: no definido
* MMSC: no definido
* Proxy de mensaje multimedia: no definido
* Puerto de mensaje multimedia: no definido
* MCC: 730
* MNC: 01
* Tipo de autenticación: **PAP**
* Tipo de APN: **Internet** (en algunos Smartphones puede ser “Default” o “Default,supl”)
* Nota: Si no logras conectarte y navegar deberás ingresar proxy 10.99.0.10 y puerto 8080.

**Bastó con poner imovil.entelpcs.cl en vez de bam.entelpcs.cl**

Espero que a alguien del universo chileno le sirva alguna vez.