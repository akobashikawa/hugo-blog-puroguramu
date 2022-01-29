---
title: 'Cómo centrar un bloque en una página'
date: 2010-07-09T18:01:00.014-05:00
draft: false
url: /2010/07/como-centrar-un-bloque-en-una-pagina
tags: 
- css
- center
- html
- blogger
---

[![](http://2.bp.blogspot.com/_K2xwnQ4Llso/TDepqPckZoI/AAAAAAAABJQ/-vgohjV6SS4/s320/center_in_page.png)](http://2.bp.blogspot.com/_K2xwnQ4Llso/TDepqPckZoI/AAAAAAAABJQ/-vgohjV6SS4/s1600/center_in_page.png)

Centrar un bloque tanto horizontal como verticalmente es algo que se requiere a veces. Lo ideal es que el centrado se acomode automáticamente cuando la ventana del navegador se redimensiona. La solución podría ser más fácil, pero la familia IE, dificulta un poco el problema.  
  

_Nota_

_**Estas soluciones funcionan en la mayoría de navegadores, incluso en IE6, pero recientemente encontré que no es así en Safari. Puede encontrar un método alternativo, que funciona en todos los navegadores, en el artículo **[Cómo centrar un bloque en una página 2](http://akcdev.blogspot.com/2011/02/como-centrar-un-bloque-en-una-pagina-2.html)._

Soluciones  

*   **En los navegadores estandar** (principalmente no-IE6), para lograr que un bloque, por ejemplo #content, de 400px por 100px, quede centrado en la página, se le puede aplicar los siguientes estilos:  
      
        #content {  
          width: 400px;  
          height: 100px;  
          position: absolute;  
          top: 0; right: 0; bottom: 0; left: 0;  
          margin: auto;  
          overflow: auto;  
      }  
      
    El truco aquí es que el margin: auto también sirve para el centrado vertical si se especifica height, position: absolute, y además top: 0; right: 0; bottom: 0; left: 0;  
    Una limitacion de esta solución es que la altura es fija. El overflow: auto es para que, cuando el contenido haga que #content sobrepase la altura especificada, aparezca un scroll.
*   **En IE6**, lo anterior no funciona. Es necesario colocar #content dentro de un #container, y usar los siguientes estilos:  
      
        #container {  
          position: absolute;  
          top: 50%;  
      }  
      #content {  
          width: 400px;  
          height: 100px;  
          position: relative;  
          margin: 0 auto;  
          top: -50%;  
          overflow: none;  
      }  
      
    Aqui se usa la técnica de mover el top del #container hacia abajo el 50% de la altura de su contenedor, body, y luego el top del #content 50% hacia arriba de la altura del **mismo #content** (debería ser de su contenedor, #container, pero este es un bug de IE6, paradójicamente util para resolver este problema mejor que en el caso estándar, pues permite que la altura vaya más allá del inicial de 100px mientras el bloque se acomoda automáticamente siempre en el centro).
*   **En IE7**, lo anterior no funciona (así que hay cosas que funcionan diferente en IE6, IE7 y IE8). Es necesario agregar un #container2, y usar los siguientes estilos:  
    

  

    #container {

      position: absolute;

      height: 50%;

      width: 100%;

    }

    #container2 {

      width: 100%;

      position: absolute;

      bottom: 0;      

    }

    #content {

      background-color: gold;

      width: 400px;

      height: 100px;

      overflow: auto;

      position: relative;

      margin: 0 auto;

      top: 50%;

    }

  

*   **Para combinar estas soluciones** en un paquete que funcione para ambos casos, se puede usar la [técnica del hack underscore](http://wellstyled.com/css-underscore-hack.html).  
    La idea de la técnica es simple e ingeniosa: Normalmente, una propiedad css que comienza con un \_, #, un punto, o un número es ignorada por los navegadores estándar (de hecho, anteponer un número al nombre de la propiedad es un truco util para desactivarla), pero IE6 filtra la cadena quitándole ese primer caracter, si es \_ o #, para usárla normalmente. De ese modo, sólo para IE6, _\_position_, o _#position_, se vuelven _position_, por ejemplo. Del mismo modo, IE7 filtra el punto y _.position_ se vuelve _position_.  
    Asi, luego de tener las cosas listas para los navegadores estándar, se puede intentar agregar o sobrescribir lo que necesitemos para IE6 e IE7, como se muestra a continuación:

  

    #container {

      \_position: absolute;

      \_top: 50%;

      .position: absolute;

      .height: 50%;

      .width: 100%;

    }

    #container2 {

      .width: 100%;

      .position: absolute;

      .bottom: 0;      

    }

    #content {

      background-color: gold;

      width: 400px;

      height: 100px;

      position: absolute;

      top: 0; right: 0; bottom: 0; left: 0;

      margin: auto;

      overflow: auto;

      \_position: relative;

      \_margin: 0 auto;

      \_top: -50%;

      \_overflow: none;

      .position: relative;

      .margin: 0 auto;

      .top: 50%;

    }

Referencias
-----------

*   [Vertical Centering in CSS](http://www.jakpsatweb.cz/css/css-vertical-center-solution.html)

_*Url archivado: [Cómo centrar un bloque en una página](https://akcdev.blogspot.com/2010/07/como-centrar-un-bloque-en-una-pagina.html)*_
