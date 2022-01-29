---
title: 'Posicionando el footer con Flexbox'
date: 2016-10-12T11:48:00.000-05:00
draft: false
url: /2016/10/posicionando-del-footer-con-flexbox
tags: 
- css
- flexbox
- blogger
---

Una forma de posicionar el footer, con Flexbox.  
  
Cómo hacer que el footer esté siempre al fondo de la página, aún cuando el contenido sea mínimo.  

Idea
----

*   El container usa **display: flex**

*   **flex-direction: column** para indicar disponer los elementos verticalmente
*   **justify-content: space-between** para que los elementos se separen hasta ocupar toda el área

*   Para que área tenga toda la altura, el **_html, body_** y el mismo **_container_** tienen **height: 100%**

*   Para indicar la altura de un elemento dentro del flex, se puede usar algo como **flex-basis: 50px**

*   Para indicar que el elemento no se pueda contraer, **flex-shrink: 0**

*   Para indicar que main ocupe toda la altura posible, **flex: 1** (por default los demas están en 0)

  See the Pen &lt;a href='http://codepen.io/akobashikawa/pen/wzXWYb/'&gt;Footer Position with Flexbox&lt;/a&gt; by Rulo Kobashikawa (&lt;a href='http://codepen.io/akobashikawa'&gt;@akobashikawa&lt;/a&gt;) on &lt;a href='http://codepen.io'&gt;CodePen&lt;/a&gt;.

_*Url archivado: [Posicionando el footer con Flexbox](https://akcdev.blogspot.com/2016/10/posicionando-del-footer-con-flexbox.html)*_
