---
title: 'Montando HTML sobre un flash'
date: 2010-06-01T16:13:00.006-05:00
draft: false
url: /2010/06/montando-html-sobre-un-flash
tags: 
- flash
- javascript
- html
- web
- blogger
---

[![](https://2.bp.blogspot.com/_K2xwnQ4Llso/TAV3-Lpy3DI/AAAAAAAABHw/Q3yFy4RCD20/s320/flash_html_popup.png)](https://2.bp.blogspot.com/_K2xwnQ4Llso/TAV3-Lpy3DI/AAAAAAAABHw/Q3yFy4RCD20/s1600/flash_html_popup.png)

**Problema**:  
Hay un objeto flash que debe funcionar como un botón que abra una ventana html flotante.  
  

**Solución:**

Para abrir una ventana html flotante usaría window.open().  
Encuentro que no es posible asociar a un objeto flash (definido con el tag object),un evento onclick.  
  
Se me ocurre que podría cubrir el objeto flash con un bloque html de las mismas dimensiones al que si pudiera asociar un evento onclick.  
  
Para eso, me baso en un patrón que aparece en [Pro CSS and HTML Design Patterns](http://www.cssdesignpatterns.com/Chapter%2001%20-%20MAKING%20CSS%20EASY/index.html), de Michael Bowers.  
Consiste en posicionar absolutamente un div dentro de otro.  
  
Hago que el div banner\_container contenga al objeto flash, pero también al div banner\_overlay, que lo cubrirá:  
  

<div id="banner\_container">  
  <div id="banner\_overlay">  
  </div>  
  <object...>...</object>  
</div&gt

  
La clave está en hacer que banner\_container tenga position:relative y banner\_overlay tenga position:absolute. Además, ambos deben tener las mismas dimensiones del objeto flash, para que lo cubran exactamente.  
  
#banner\_container {  
    position: relative;  
    width: 200px;  
    height: 100px;  
}  
#banner\_overlay {  
    position: absolute;  
    width: 200px;  
    height: 100px;  
    border: 1px solid #abe;  
}  
  
Luego, se puede usar javascript sobre el div banner\_overlay. Por ejemplo, con jquery:  
  
$(document).ready(function() {  
    $('#banner\_overlay').click(function() {  
        var w = window.open('ventana1.html', 'Ventana 1', 'width=400,height=300');  
    });  
});  
  
Puede encontrar un demo [aquí](http://www.kobaonline.com/rulo/jquery/).

_*Url archivado: [Montando HTML sobre un flash](https://akcdev.blogspot.com/2010/06/montando-html-sobre-un-flash.html)*_

---
### Comentarios archivados:

>
> hola muy bueno tus recomendaciones y ayudas, gracias
> \
> [Jocy](https://www.blogger.com/profile/09048458569924074587 "noreply@blogger.com") [2010-06-26 14:23]
