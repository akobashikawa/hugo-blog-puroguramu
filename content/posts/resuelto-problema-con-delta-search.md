---
title: 'Resuelto Problema con Delta Search'
date: 2013-05-02T13:21:00.000-05:00
draft: false
url: /2013/05/resuelto-problema-con-delta-search
tags: 
- solución
- problema
- malware
- chrome
- blogger
---

Resuelto Problema con Delta Search
----------------------------------

Al hacer una instalación, me precipité e hice click en OK antes de leer que estaba aceptando instalar Delta Search Toolbar.

  

Cuando se instala, reemplaza a la máquina de búsqueda por default de los navegadores.

  

En el Panel de Control, Desinstalar Programas, se puede encontrar el item Delta Search y desinstalarlos, pero no se realiza una desinstalación completa, como se comprueba al continuar viendo el buscador de delta al iniciar los navegadores.

  

Resolverlo en **IE** fue relativamente sencillo. Bastó con entrar a la administración de AddOns, hacer que otra maquina de búsqueda sea la default y eliminar a Delta Search.

  

En **Firefox** no encontré que se hubiera metido.

  

En **Chrome**, entré a la configuración de motores de búsqueda y lo eliminé. Sin embargo al iniciar el navegador, abría Delta Search en una segunda ventana.

Para resolverlo, seguí el consejo de abrir el archivo **%UserProfile%\\AppData\\Local\\Google\\Chrome\\User Data\\Default\\Preferences**, buscar las ocurrencias de delta-search.com y eliminarlas, o reeemplazarlas por google.com o algo parecido. Sin embargo, el problema persistía.

  
Finalmente, **la solución** consistió en usar [AdwCleaner](http://www.bleepingcomputer.com/download/adwcleaner/). Lo instalé, localizó los problemas (entre ellos la entrada en Preferences) y me dio la opción de corregirlos.  
  

*   [http://www.techsupportall.com/how-to-remove-delta-search-home-page-ie-firefox-chrome/](http://www.techsupportall.com/how-to-remove-delta-search-home-page-ie-firefox-chrome/)

_*Url archivado: [Resuelto Problema con Delta Search](https://akcdev.blogspot.com/2013/05/resuelto-problema-con-delta-search.html)*_
