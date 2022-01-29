---
title: 'Personalizando bullets'
date: 2010-07-23T17:51:00.007-05:00
draft: false
url: /2010/07/personalizando-bullets
tags: 
- html
- blogger
---

[![](http://4.bp.blogspot.com/_K2xwnQ4Llso/TEohBxEEVHI/AAAAAAAABJg/VqKW0rvixoU/s200/us-games-juggling-balls.jpg)](http://4.bp.blogspot.com/_K2xwnQ4Llso/TEohBxEEVHI/AAAAAAAABJg/VqKW0rvixoU/s1600/us-games-juggling-balls.jpg)

Normalmente, una lista tipo **ul** luce así:  

*   Item 1
*   Item 2
*   Item 3

Se puede usar CSS para cambiar el tipo del bullet (que por default es _disc_):  
**list-style:disc**  

*   Item 1
*   Item 2
*   Item 3

**list-style:circle**  

*   Item 1
*   Item 2
*   Item 3

**list-style:square**  

*   Item 1
*   Item 2
*   Item 3

**list-style:none**  

*   Item 1
*   Item 2
*   Item 3

**list-style:url(flecha\_roja.gif)**  

*   Item 1
*   Item 2
*   Item 3

Para controlar la posición del bullet, se puede usar la técnica de poner la imagen como fondo del item.  
En este ejemplo aplico los estilos en línea, para ilustrar la idea. Sin embargo, en un caso real, lo usual es que use clases y bloques u hojas de estilo para indicar lo mismo.  
  
```
<ul style="list-style:none;">  
<li   
  style="background:url(flecha\_roja.gif) 1px 2px  
  no-repeat; padding-left:10px;">  
  Item 1: Bullet más cerca y centrado</li>  
<li  
  style="background:url(flecha\_roja.gif) right 2px  
  no-repeat; width: 250px;">  
  Item 2: Bullet a la derecha</li>  
</ul>  

```  

*   Item 1: Bullet más cerca y centrado
*   Item 2: Bullet a la derecha

  
Puede ver un demo en [aquí](http://www.kobaonline.com/rulo/demos/html-bullets/)  
  

_Crédito de la imagen: [http://www.robbinssports.com](http://www.robbinssports.com/sporting-goods-store/images/us-games-juggling-balls.jpg)_

_*Url archivado: [Personalizando bullets](https://akcdev.blogspot.com/2010/07/personalizando-bullets.html)*_
