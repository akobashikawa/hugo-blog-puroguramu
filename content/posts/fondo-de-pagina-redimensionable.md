---
title: 'Fondo de página redimensionable'
date: 2010-07-26T23:53:00.002-05:00
draft: false
url: /2010/07/fondo-de-pagina-redimensionable
tags: 
- background
- html
- blogger
---

PROBLEMA
--------

Cómo lograr que el fondo de una página sea redimensionable.  

SOLUCION
--------

La técnica consiste en colocar un img con un width=100%:  
  
```
<img src="friends-and-moon.jpg" width="100%"/>
```

  
Sin embargo, a menos que se trate de un popup, aparecerán barras de scroll para permitir ver el resto de la imagen que no esté en pantalla.  
  
Para evitar eso, se coloca el img dentro de un div con estilos adecuados:  
  
```
body {  
  margin:0;  
}  
#bg {  
  width: 100%; height: 100%; left: 0px; top: 0px; position: fixed;  
}  
#container {  
  position: absolute; top: 0; left: 0; width: 100%;  
}  
<!-- ... -->  
<div id="bg"><img src="friends-and-moon.jpg" width="100%"/></div>  
<div id="container">  
<!-- content -->  
</div>  

```Como se observa, luego el contenido de la página se puede colocar en un div posicionado absolutamente sobre la imagen. De ese modo se simula un fondo de página redimensionable.  
  
El problema de la presentación del scroll se soluciona de este modo en los navegadores estandar, pero persiste en IE6.  

Puede ver un demo [aquí](http://www.kobaonline.com/rulo/demos/resizable-background/).
-------------------------------------------------------------------------------------

REFERENCIAS
-----------

*   [How To: Resizeable Background Image](http://css-tricks.com/how-to-resizeable-background-image/)

_*Url archivado: [Fondo de página redimensionable](https://akcdev.blogspot.com/2010/07/fondo-de-pagina-redimensionable.html)*_

---
### Comentarios archivados:

>
> ¿Y como seria esto en blogger?
> \
> [Mauro](# "noreply@blogger.com") [2011-03-09 09:23]

>
> y si no quiero que la posición del sea fija ? puedo quitar el "fixed" y seguirá funcionando ?  
http://edadblogger.blogspot.com/
> \
> [Anónimo](# "noreply@blogger.com") [2012-09-04 13:41]
