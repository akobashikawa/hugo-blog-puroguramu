---
title: 'Enlaces simbólicos en Windows'
date: 2010-03-11T18:25:00.007-05:00
draft: false
url: /2010/03/enlaces-simbolicos-en-windows
tags: 
- windows
- blogger
---

[![](https://3.bp.blogspot.com/_K2xwnQ4Llso/S5l7sJX_lRI/AAAAAAAAAZg/I_4t-yWSCqY/s200/windows7_01.jpg)](https://3.bp.blogspot.com/_K2xwnQ4Llso/S5l7sJX_lRI/AAAAAAAAAZg/I_4t-yWSCqY/s1600-h/windows7_01.jpg)

En Linux, un enlace simbólico es un archivo o directorio ficticio que representa a un archivo o directorio real.  
  
Por ejemplo, puedo tener un enlace simbolico /usr/bin/java en lugar de /usr/bin/java-1.6 (En este caso en particular me sirve para actualizar java sin tener que tocar los archivos de configuración que se refieren a /usr/bin/java).  
  
En Windows 7, y también en Windows Vista, se puede hacer con el comando **mklink**.  
  
También es posible usar una utilidad llamada **Junction**. Funciona para Windows XP en adelante y puede descargarse de [Junction v1.05](http://technet.microsoft.com/en-us/sysinternals/bb896768.aspx)  
  
La descarga provee un zip que contiene un único archivo ejecutable que se puede colocar en C:\\Windows\\. De ese modo, está disponible en cualquier lugar que se abra la consola de comandos.  
  
En mi caso, necesitaba un enlace simbólico htdocs/site1.localhost que apuntara a htdocs/drupal/sites/site1.localhost  
Para eso, me ubiqué en htdocs y ejecuté el comando:  
  

mklink /D  site1.localhost drupal\\sites\\site1.localhost

  
o, usando junction:  
  

junction site1.localhost drupal\\sites\\site1.localhost

  
A partir de allí, cuando entro a http://localhost/site1.localhost estoy accediendo al contenido de drupal/sites/site1.localhost.  
  
Para eliminar el link:  
  

rd site1.localhost

  
ó, usando junction:  
  

junction -d site1.localhost

  
**Nota:**  
Este es un paso intermedio en mi intento de lograr una configuración drupal multisite (lo que aún no consigo), sin embargo me ha parecido útil lo que se puede hacer con Junction por sí sólo. Ojalá que a ustedes también.

_*Url archivado: [Enlaces simbólicos en Windows](https://akcdev.blogspot.com/2010/03/enlaces-simbolicos-en-windows.html)*_
