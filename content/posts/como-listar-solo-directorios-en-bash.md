---
title: 'Cómo listar sólo directorios en bash'
date: 2011-02-04T10:57:00.001-05:00
draft: false
url: /2011/02/como-listar-solo-directorios-en-bash
tags: 
- linux
- bash
- blogger
---

[![](http://3.bp.blogspot.com/_K2xwnQ4Llso/TUwhyQVJXyI/AAAAAAAABQ8/7Vr3QRUEWG8/s1600/tux-100.png)](http://3.bp.blogspot.com/_K2xwnQ4Llso/TUwhyQVJXyI/AAAAAAAABQ8/7Vr3QRUEWG8/s1600/tux-100.png)

Hay varias formas. La primera me parece la más elegante (cuenta el que la compartió que la descubrió recien a los tres años de usar Linux):  
  
ls -d \*/  
ls -l | grep ^d  
ls | grep /$  
  
Referencia: http://www.linuxquestions.org/questions/programming-9/how-can-i-list-directories-only-in-linux-375219/

_*Url archivado: [Cómo listar sólo directorios en bash](https://akcdev.blogspot.com/2011/02/como-listar-solo-directorios-en-bash.html)*_
