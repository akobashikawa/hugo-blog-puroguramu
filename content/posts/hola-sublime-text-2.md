---
title: 'Hola Sublime Text 2!'
date: 2012-02-22T22:34:00.001-05:00
draft: false
url: /2012/02/hola-sublime-text-2
tags: 
- sublime
- editor
- blogger
---

[![](http://3.bp.blogspot.com/-GAcPqZLiy-E/T0WtNTBdyJI/AAAAAAAABvs/-KutAcqdQUM/s1600/sublimetext2-icon.png)](http://3.bp.blogspot.com/-GAcPqZLiy-E/T0WtNTBdyJI/AAAAAAAABvs/-KutAcqdQUM/s1600/sublimetext2-icon.png)

[Sublime Text 2](http://www.sublimetext.com/2) es un nuevo editor de texto que estoy probando.  
  
Mi editor de textos favorito es [Notepad++](http://notepad-plus-plus.org/). Antes lo fue [jEdit](http://www.jedit.org/). Pero, cuando jEdit me empezó a parecer demasiado pesado, encontré en npp una buena alternativa. Iniciaba mucho más rápido, también coloreaba la sintaxis, también tenía tabs... además empecé a pasar la mayor parte del tiempo en Windows, así que comencé a usarlo cada vez más. Mucho más con el cómodo manejo de encodings (más que en cualquier otro editor que haya visto), el plugin para FTP y con el soporte para Zencoding.  
  
Hace unos días, de pronto, descubrí Sublime Text 2. Lo recomendaban en unos video tutoriales sobre jQuery en [net.tuts.com](http://net.tuts.com/). Y me está pareciendo interesante. Aún me está costando un poco acostumbrarme a las nuevas secuencias de teclas pero me gusta mucho lo de los cursores múltiples, las selecciones rectangulares, las selecciones múltiples, la forma en que maneja la configuración. No es open source pero tiene una arquitectura extensible. No es gratis pero uno puede probarlo indefinidamente... sólo hay que cerrar el recordatorio de compra de vez en cuando.  
  
Tengo ciertos hábitos al editar texto, así que aquí resumo lo que voy haciendo mientras aprendo cómo hacerlo en ST2.  
  
Preferencias Generales  
Por ejemplo, para fonts, me gusta usar algo similar a Lucida Typewriter, o DejaVu Sans Mono, a 14pt. También los tabs reemplazados por 2 espacios.  
No encuentro un menú para eso. Pero se resuelve entrando a _Preferences, Settings-User_ y agregando ahí los items de configuración que uno quiera. Una referencia a los valores que se puede poner se puede ver entrando a _Preferences, Settings-Default_:  
  
```
{  
  "font\_face": "DejaVu Sans Mono",  
  "font\_size": 14,  
  "tab\_size": 2,  
  "translate\_tabs\_to\_spaces": true  
}  

```  
Zencoding  
Si uno hace una secuencia tipo zencoding seguida de un tab, se expande. Sin embargo, quisiera expansiones de documento un poco más completas (html:4s, por ejemplo). Así que buscando encuentro que para instalar Zencoding hay que instalar primero el [Sublime Package Control](http://wbond.net/sublime_packages/package_control).  
  
Para eso no hay que bajar manualmente ningún archivo, sino ejecutar en la consola de ST2 (se abre con CTRL+\` o entrando a View, Show Console), lo siguiente:  
  
```
import urllib2,os; pf='Package Control.sublime-package'; ipp=sublime.installed\_packages\_path(); os.makedirs(ipp) if not os.path.exists(ipp) else None; urllib2.install\_opener(urllib2.build\_opener(urllib2.ProxyHandler())); open(os.path.join(ipp,pf),'wb').write(urllib2.urlopen('http://sublime.wbond.net/'+pf.replace(' ','%20')).read()); print 'Please restart Sublime Text to finish installation'  

```  
Luego de eso, reinicio ST2. Luego, entro a Tools, Command Pallete, Package Control::Install Package y elijo Zencoding en la lista de paquetes. Reinicio ST2 nuevamente. Pruebo crear un documento html, escribo html:4s, TAB, funciona :-D  
  
Para una guía rápida de cómo usar Zencoding en ST2, se puede revisar [http://code.google.com/p/zen-coding/wiki/SublimeTextZenCodingEn](http://code.google.com/p/zen-coding/wiki/SublimeTextZenCodingEn)  
  
A veces, uno quiere que cierto documento se trate de cierta manera (por ejemplo los .module de Drupal son php). Para indicarlo manualmente, en el menú elegir View, Syntax y elegir el tipo.  

### Update

El package Zencoding cambio de nombre a Emmet.

_*Url archivado: [Hola Sublime Text 2!](https://akcdev.blogspot.com/2012/02/hola-sublime-text-2.html)*_
