---
title: 'Resolviendo inicio MySQL con Xampp en Ubuntu'
date: 2011-06-16T01:12:00.000-05:00
draft: false
url: /2011/06/resolviendo-inicio-mysql-con-xampp-en
tags: 
- mysql
- linux
- xampp
- blogger
---

[![](https://4.bp.blogspot.com/-KmhYf9ZalO4/TUwhyQVJXyI/AAAAAAAABQ8/GpJ-i1hu6wo/s1600/tux-100.png)](https://4.bp.blogspot.com/-KmhYf9ZalO4/TUwhyQVJXyI/AAAAAAAABQ8/GpJ-i1hu6wo/s1600/tux-100.png)

Instalé **Lampp** (_Xampp para Linux_, xampp-linux-1.7.4.tar.gz) en **Ubuntu** (_Natty Narwhal_).  
  
La ruta de instalación es **/opt/lampp**  
  
Para iniciar lampp:  
  
```
sudo /opt/lampp/lampp start  

```  
Obtuve un mensaje de error, indicando que MySQL no podía iniciar.  
  
Parece que el problema tiene que ver con los derechos de escritura. La solución que me funcionó fue:  
  
```
sudo -s  
cd /opt  
chmod -R 777 lampp  
chmod 755 lampp/etc/my.cnf  

```  
Espero le sea de ayuda. Quizás alguien encuentre una mejor solución.

_*Url archivado: [Resolviendo inicio MySQL con Xampp en Ubuntu](https://akcdev.blogspot.com/2011/06/resolviendo-inicio-mysql-con-xampp-en.html)*_

---
### Comentarios archivados:

>
> Te falto una p en lamp (lampp) aunque poco a poco me acerco a la solucion aun no la tengo de todas formas gracias fue muy util tu ayuda
> \
> [Unknown](https://www.blogger.com/profile/09647490901397100547 "noreply@blogger.com") [2012-09-15 10:28]

>
> Gracias por tu observación. Corregí esa parte. Buena suerte.
> \
> [Rulo Kobashikawa](https://www.blogger.com/profile/07020497448167262255 "noreply@blogger.com") [2012-09-15 10:33]

>
> Gracias!! En verdad me ayudo bastante :D Que dios te bendiga
> \
> [Xavier](https://www.blogger.com/profile/07386089212713909494 "noreply@blogger.com") [2014-01-21 07:22]

>
> Gracias también :-)
> \
> [Rulo Kobashikawa](https://www.blogger.com/profile/07020497448167262255 "noreply@blogger.com") [2014-01-21 16:18]

>
> Me funcionó, muchas gracias amigo!!!
> \
> [Anónimo](# "noreply@blogger.com") [2014-06-13 14:19]

>
> Me alegra, buena suerte!
> \
> [Rulo Kobashikawa](https://www.blogger.com/profile/07020497448167262255 "noreply@blogger.com") [2014-06-13 16:18]

>
> gracias amigo.
> \
> [Unknown](https://www.blogger.com/profile/08863688343512226779 "noreply@blogger.com") [2017-05-16 10:50]

>
> Gracias también :)
> \
> [Rulo Kobashikawa](https://www.blogger.com/profile/07020497448167262255 "noreply@blogger.com") [2017-05-16 14:02]
