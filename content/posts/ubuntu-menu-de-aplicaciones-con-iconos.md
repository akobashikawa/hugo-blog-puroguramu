---
title: 'Ubuntu menú de aplicaciones con iconos'
date: 2011-06-17T11:36:00.002-05:00
draft: false
url: /2011/06/ubuntu-menu-de-aplicaciones-con-iconos
tags: 
- ubuntu
- linux
- blogger
---

[![](http://3.bp.blogspot.com/-LD1XnA0zJ6g/TfuCYDUCc8I/AAAAAAAABWY/08Y2rlw1drY/s200/application_menu_icons.png)](http://3.bp.blogspot.com/-LD1XnA0zJ6g/TfuCYDUCc8I/AAAAAAAABWY/08Y2rlw1drY/s1600/application_menu_icons.png)

En **Ubuntu Natty Narwhal**, no me agrada mucho que **Unity**, el nuevo sistema de escritorio de Ubuntu, requiera que uno descienda varios niveles para encontrar el menú de aplicaciones (_Ubuntu logo, More Apps, All Applications_).  
  
Así que he instalado **Cairo**, que provee un docker similar al que se usa en Mac, o al que provee también [**RocketDock**](http://rocketdock.com/) en **Windows**. Lo bueno de Cairo es que provee un acceso directo al menú de aplicaciones.  
  
Sin embargo, noto que el menú de aplicaciones no muestra los iconos sino sólo la etiqueta de cada opción.  
  
Encontré en [tips4linux.com](http://tips4linux.com/toggle-the-ubuntu-system-menu-icons-to-visible/) una manera de solucionarlo. Ejecutar en la consola de comandos:  
  
```
gconftool-2 --type Boolean --set /desktop/gnome/interface/menus\_have\_icons True  

```  
Referencias  

*   [Toggle the Ubuntu System menu icons to Visible](http://tips4linux.com/toggle-the-ubuntu-system-menu-icons-to-visible/)

_*Url archivado: [Ubuntu menú de aplicaciones con iconos](https://akcdev.blogspot.com/2011/06/ubuntu-menu-de-aplicaciones-con-iconos.html)*_
