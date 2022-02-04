---
title: 'Vertical Site'
date: 2012-05-25T18:53:00.001-05:00
draft: false
url: /2012/05/vertical-site
tags: 
- css
- jquery
- programación
- javascript
- html
- web
- blogger
---

Introducción  
La motivación fue hacer un site similar a:  

*   [http://www.soleilnoir.net/believein](http://www.soleilnoir.net/believein)
*   [http://discover.store.sony.com/tablet](http://discover.store.sony.com/tablet)

Revisando believein (pude bajar el site usando wget, Firebug y un poco de paciencia), me resultaba un poco difícil encontrar la clave del comportamiento que veía.

  

Encontré una aproximación en [Curtain.js](http://curtain.js/). Sin embargo, cuando requería modificar la presentación, también me resultaba un poco difícil encontrar dónde hacerla.

  

Decidí reinventar la rueda de este caso, para tratar de comprender las ideas del proceso de solución.

  

Los sites que revisé me dieron pistas.

  
En este tutorial trato de resumir el proceso.  
  
[vertical-site@github](https://github.com/akobashikawa/vertical-site)

  

Simple HTML

*   Todo el contenido está presente en el mismo documento.
*   El contenido se divide en secciones a las que denomino pages.
*   Cada page es el destino de un link del menú. Esto permite una navegación simple a enlaces internos.

[![](https://3.bp.blogspot.com/-NWq45lMgBfI/T71r3SWPQLI/AAAAAAAAB4A/nUxS8kSmmSQ/s320/vertical-site-simple_html.png)](https://3.bp.blogspot.com/-NWq45lMgBfI/T71r3SWPQLI/AAAAAAAAB4A/nUxS8kSmmSQ/s1600/vertical-site-simple_html.png)

Aplicando estilos básicos:

[![](https://3.bp.blogspot.com/-BGpYmnfYdmg/T711cpTypuI/AAAAAAAAB4M/9k62wkIaeNA/s320/vertical-site-simple_html_css.png)](https://3.bp.blogspot.com/-BGpYmnfYdmg/T711cpTypuI/AAAAAAAAB4M/9k62wkIaeNA/s1600/vertical-site-simple_html_css.png)

  
[index.html](https://github.com/akobashikawa/vertical-site/blob/simple_html/index.html)  
[style.css](https://github.com/akobashikawa/vertical-site/blob/simple_html/css/style.css)  
  
Nav fixed  

*   Se fijan los elementos de navegación: cabecera y menú.  
    En simple\_html, estaban dentro de page-0 (para permitir ver el menú cuando se fuera a HOME). Como ahora serán siempre visibles, eso no es necesario.
    
    [![](https://4.bp.blogspot.com/-WuiRiK0CJLE/T7-0jz8PEII/AAAAAAAAB4c/-b0k9OrKJzA/s320/vertical-site-nav_fixed.png)](https://4.bp.blogspot.com/-WuiRiK0CJLE/T7-0jz8PEII/AAAAAAAAB4c/-b0k9OrKJzA/s1600/vertical-site-nav_fixed.png)
    
*   Se implementa un indicador de posición, que señale en el menú la página activa.

*   En el menú, aparece resaltado el link a.active
*   El link se activa si el url cambia
*   El url cambia

*   cuando se ingresa a mano
*   cuando se hace click en un enlace del menú
*   cuando se hace scroll

*   El plugin [address](http://www.asual.com/jquery/address/) permite responder ante un cambio del url.
    
    [![](https://4.bp.blogspot.com/-afIlfdtWGSg/T7_AK5eRxKI/AAAAAAAAB4o/cVxMr-PGofc/s320/vertical-site-nav_fixed_js.png)](https://4.bp.blogspot.com/-afIlfdtWGSg/T7_AK5eRxKI/AAAAAAAAB4o/cVxMr-PGofc/s1600/vertical-site-nav_fixed_js.png)
    

[index.html](https://github.com/akobashikawa/vertical-site/blob/nav_fixed/index.html)  
[style.css](https://github.com/akobashikawa/vertical-site/blob/nav_fixed/css/style.css)  
[script.js](https://github.com/akobashikawa/vertical-site/blob/nav_fixed/js/script.js)  
  
Scrollto  

*   Scroll animado suave.

  
[index.html](https://github.com/akobashikawa/vertical-site/blob/scrollto/index.html)  
[style.css](https://github.com/akobashikawa/vertical-site/blob/scrollto/css/style.css)  
[script.js](https://github.com/akobashikawa/vertical-site/blob/scrollto/js/script.js)  
  
_(continuará...)_

_*Url archivado: [Vertical Site](https://akcdev.blogspot.com/2012/05/vertical-site.html)*_
