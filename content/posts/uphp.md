---
title: 'uphp'
date: 2011-04-15T15:22:00.001-05:00
draft: false
url: /2011/04/uphp
tags: 
- uphp
- framework
- blogger
---

  

[![](https://4.bp.blogspot.com/-VOiPjiViZ4A/SpeOgCTX4MI/AAAAAAAAAE0/3qftQsAxguI/s200/php2sv8.png)](https://4.bp.blogspot.com/-VOiPjiViZ4A/SpeOgCTX4MI/AAAAAAAAAE0/3qftQsAxguI/s1600/php2sv8.png)

Con **HTML**, el contenido se mezcla con etiquetas que permiten mostrarlo en un navegador.

**CSS** permite separar la data del formato de la data del contenido.

**Javascript** permite poner código en las etiquetas para manipular el documento e interactuar con sus elementos.

**Unobstrusive javascript** es una forma de usar javascript que procura mantener el código aparte. _jQuery_ ayuda mucho en esto.

JSP, **PHP**, etc, permiten generar HTML, abriendo la puerta a la automatización y al uso de recursos como las bases de datos.

**Frameworks** web permiten para manejar el desarrollo de un site relativamente extenso o complejo.

El modelo de framework **MVC** (Modelo-Vista-Controlador), viene del mundo Smalltalk a la web para separar el desarrollo en esas tres capas.  
En mi opinión, aumenta la inercia del proceso de desarrollo. Expresar una solución web en términos MVC se convierte en un problema adicional.

**Drupal** usa un modelo de framework diferente, ingenioso, permitiendo agregar libremente componentes que pueden colaborar entre sí.  
También requiere algo de tiempo y trabajo aprender a pensar y expresar cualquier solución en sus términos. A cambio, a mi parecer, permite ser mucho más productivo que en cualquiera de las alternativas anteriores.

En general, estos frameworks requieren que aprendamos una nueva versión de lo que ya sabemos hacer en web. A veces, incluso hay que hacer ese reaprendizaje de una versión a otra del mismo framework.

¿No le parece que algo tiene que cambiar?  
¿Habrá alguna forma de hacer dinámica una página estática sin tener que reescribirla? 

Encontrando a **QueryPath**, algo como un puerto de **jQuery** para PHP, que facilita la manipulación de una página, me pareció que podría haber alternativas.

[**uphp**](http://rulokc.freezoka.net/uphp/) es la búsqueda de una forma de desarrollar web en la que el código afecta al contenido pero se manteniene aparte.  
De ese modo, se pueden respetar las páginas estáticas de un site mientras se lo vuelve dinámico.  
Además, se podría usar, tal cual, soluciones HTML/CSS/Javascript que sean independientes del framework.

Quien sabe, quizás tambien se halle una forma de hacer todo eso y además separar la data del contenido de la data HTML.

_*Url archivado: [uphp](https://akcdev.blogspot.com/2011/04/uphp.html)*_
