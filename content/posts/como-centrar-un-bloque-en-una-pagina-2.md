---
title: 'Cómo centrar un bloque en una página 2'
date: 2011-02-16T13:30:00.002-05:00
draft: false
url: /2011/02/como-centrar-un-bloque-en-una-pagina-2
tags: 
- css
- center
- html
- blogger
---

[![](https://3.bp.blogspot.com/-N0g311E0a9w/TDepqPckZoI/AAAAAAAABJQ/E9ODF_y8rf4/s1600/center_in_page.png)](https://3.bp.blogspot.com/-N0g311E0a9w/TDepqPckZoI/AAAAAAAABJQ/E9ODF_y8rf4/s1600/center_in_page.png)

En el artículo [Cómo centrar un bloque en una página](https://akcdev.blogspot.com/2010/07/como-centrar-un-bloque-en-una-pagina.html), contaba sobre un método que venía utilizando para lograr centrar un bloque en una página.  
  
Ayer, un amigo me mostró una página posicionada de ese modo que no cabía en la ventana de su navegador Safari. Este mostraba el centro pero no permitía alcanzar la cabecera, ni siquiera usando la barra de scroll. En otros navegadores, como Firefox, Chrome e incluso Internet Explorer, si un bloque no cabe en la ventana, se muestra lo que quepa, de arriba hacia abajo. Pero en el suyo lo hacía desde el centro hacia afuera.  
  
Comprobé que otras páginas que había hecho usando ese método presentaban el mismo problema cuando las veía con Safari y reducía las dimensiones de la ventana.  
  
Buscando la explicacion a esto, encontré el artículo [Easy Vertical Centering with CSS](http://www.search-this.com/2008/05/15/easy-vertical-centering-with-css/), que muestra un método diferente a los usuales, bastante simple y que, sorprendentemente, funciona en todos los navegadores en los que lo he probado, incluyendo Firefox 3.6, Chrome 9, Safari 5, IE8 e IE6.  
  
**La idea**  
La idea básica es mover el top del bloque de contenido al centro de la página y luego corregir el desplazamiento subiéndolo la mitad de la altura del bloque de contenido.  
  
Usualmente, en el bloque de contenido, se usa algo como:  
  
```
#page {  
  width: 960px;  
  height: 684px;  
  position: absolute;  
  top: 50%;  
  left: 50%;  
  margin-top: -342px;  
  margin-left: -480px;  
}  

```  
Pero presenta el problema del que estamos hablando, que cuando la página es mas alta que la ventana es difícil alcanzar la cima.  
  
Hay otro método que usa una técnica ingeniosa: usar un **bloque flotante** para jalar al bloque de contenido. Una propiedad del bloque flotante es que jalará mientras se pueda; si algo se interpone (como otro bloque o el borde de la ventana), dejara de hacerlo. Es justamente lo que se necesita.  
  
Aquí, el HTML de una página que usa ese método:  
  
```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">  
<html xmlns="http://www.w3.org/1999/xhtml">  
<head>  
<title>Page Center</title>  
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1" />  
<style type="text/css">  
html, body {  
 height: 100%;  
 margin: 0;  
 padding: 0;  
}  
body {  
 background-color: #eed;  
 min-width: 960px;  
 min-height: 683px;  
}  
#vertical-float {  
 **float: left;**  
 height: 50%;  
 margin-top: -342px; /\* half vertical height\*/  
 width: 100%;  
}  
#page {  
 clear: both;  
 background: #fff;  
 width: 960px;  
 height: 683px;  
 margin: 0 auto;  
 overflow: auto;  
}  
</style>  
</head>  
<body>  
<div id="vertical-float"></div>  
<div id="page-wrapper"> <div id="page">  
    <h1>Content</h1>  
  </div>  
</div>  
</body>  
</html>  

```  
Observar que la información de la altura del bloque de contenido (#page) está presente tanto en el bloque de contenido como en el bloque auxiliar (#vertical-float).  

[![](https://3.bp.blogspot.com/-XM5EBSwSBY4/T_SurFg_MTI/AAAAAAAAB7E/kVUKORoyZAY/s320/center_in_page.jpg)](https://3.bp.blogspot.com/-XM5EBSwSBY4/T_SurFg_MTI/AAAAAAAAB7E/kVUKORoyZAY/s1600/center_in_page.jpg)

  
**Referencias**  

*   [Easy Vertical Centering with CSS](http://www.search-this.com/2008/05/15/easy-vertical-centering-with-css/)
*   [http://jsfiddle.net/rulokc/hF52h/](http://jsfiddle.net/rulokc/hF52h/)
*   [http://jsfiddle.net/rulokc/5mkBJ/](http://jsfiddle.net/rulokc/5mkBJ/)

_*Url archivado: [Cómo centrar un bloque en una página 2](https://akcdev.blogspot.com/2011/02/como-centrar-un-bloque-en-una-pagina-2.html)*_
