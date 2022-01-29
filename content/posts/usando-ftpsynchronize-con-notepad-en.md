---
title: 'Usando FTP_synchronize con Notepad++ en Windows 7'
date: 2010-01-11T11:49:00.005-05:00
draft: false
url: /2010/01/usando-ftpsynchronize-con-notepad-en
tags: 
- windows
- editor
- blogger
---

[![](http://4.bp.blogspot.com/_K2xwnQ4Llso/S0tWV8obHrI/AAAAAAAAALA/d-qD4EHfJKc/s200/notepad_plus.png)](http://4.bp.blogspot.com/_K2xwnQ4Llso/S0tWV8obHrI/AAAAAAAAALA/d-qD4EHfJKc/s1600-h/notepad_plus.png)

Notepad++ es un editor de texto muy util para programar. Lo uso bastante para HTML, CSS, javascript, php, etc. Su menú encoding permite ver y cambiar de manera muy fácil el encoding de un archivo; por ejemplo, es sencillo pasar ANSI a Unicode UTF-8, con BOM o sin BOM, y viceversa (para una nota sobre lo que es ANSI, puede ver [ASCII, ANSI, Roman 1, and What's All That?](http://flex.sys-con.com/node/45949))  
  
Lo había venido usando con uno de sus plugins, FTP\_synchronize, y me sorprendió un poco descubrir que la nueva versión 5.6.3 que instalé ya no lo incluía por default.  
Afortunadamente, es posible bajarlo \[[Edit files on FTP with Notepad++ plugin](http://www.rarst.net/software/notepadpp-ftp-plugin/)\]. Puede hacerlo desde [SourceForge::Notepad++ Plugins::FTP\_synchronize](http://sourceforge.net/projects/npp-plugins/files/FTP_synchronize/)  
  
Yo bajé de allí el archivo FTP\_synchronize\_0\_9\_6\_1\_dll.zip. Al abrirlo hallé 2 dll y una nota indicando que aquel marcado con una A era para los Windows sin soporte para unicode (la A es por ANSI). Así que coloqué FTP\_synchronize.dll en el directorio plugins de Notepad++, luego cerre y volví abrir el editor y encontré que FTP\_synchronize aparecía en el menú plugins.  
  
Configuré el acceso a una cuenta e ingresé a los directorios sin problema. Pero, cuando intentaba editar algún archivo, me aparecía el mensaje "Unable to create directory for file C". Aparentemente Windows 7 no deja escribir así nomás a los programas en el disco (aunque opino que debería dejar hacerlo en sus subdirectorios propios). Felizmente encontré en Internet una forma de solucionar el problema \[[Problems using the Notepad++ FTP\_Synchronize Plugin with Vista](http://www.technicallychris.com/2009/06/13/problems-using-the-notepad-ftp_synchronize-plugin-with-vista/)\].  
  
Lo que yo hice fue ir al directorio de plugins de Notepad++ para crear manualmente el subdirectorio FTP\_synchronize. Luego, fue necesario que le hiciera clic derecho para ver sus propiedades y modificar los permisos de acceso de Users sobre ese directorio, para que pudieran crear, eliminar, y modificar los archivos y directorios que pudiera contener.  
  
Finalmente, pude editar el archivo que que quería (en mi caso era cambiarle el encode a UTF8 sin BOM).

_*Url archivado: [Usando FTP_synchronize con Notepad++ en Windows 7](https://akcdev.blogspot.com/2010/01/usando-ftpsynchronize-con-notepad-en.html)*_
