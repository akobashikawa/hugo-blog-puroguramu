---
title: 'Termux para programar en un android'
date: 2017-04-04T19:52:00.001-05:00
draft: false
url: /2017/04/termux-para-programar-en-un-android
tags: 
- blogger
---

Termux (https://termux.com) es una aplicacion que emula una consola Linux en el Android.

Una vez instalada, se puede instalar ssh:

$ apt update  
$ apt install openssh  
$ ssh myuser@myserver.com

Una vez conectado a un servidor, se puede usar los comandos Linux de ese servidor.

Yo probe entrar a un servidor en Digital Ocean, crear un proyecto React, usar el editor vim, ejecutar el proyecto y ver el resultado en una pagina web, abierta en Chrome en el mismo celular (Android reconocio alternar  entre aplicaciones con Alt+Tab).

Si ademas cuentas con un teclado conectado via bluetooth, la sensacion puede ser como la de tener una mini laptop con touchscreen ^^

Tip:  
En Termux, para abrir mas de una consola, arrastrar el dedo desde afuera del borde izquierdo hacia adentro.

_*Url archivado: [Termux para programar en un android](https://akcdev.blogspot.com/2017/04/termux-para-programar-en-un-android.html)*_
