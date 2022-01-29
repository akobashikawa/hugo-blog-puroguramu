---
title: 'Resolviendo Soporte Drag para Flexslider'
date: 2012-09-24T15:13:00.002-05:00
draft: false
url: /2012/09/resolviendo-soporte-drag-para-flexslider
tags: 
- jquery
- programación
- solución
- javascript
- web
- blogger
---

[![](http://1.bp.blogspot.com/-ioXM9g4eFMA/UGC-mwcEBfI/AAAAAAAAB-c/LOhfFiqtrqg/s200/touch-icon.png)](http://1.bp.blogspot.com/-ioXM9g4eFMA/UGC-mwcEBfI/AAAAAAAAB-c/LOhfFiqtrqg/s1600/touch-icon.png)

Es posible usar el plugin [jquery.event.drag](http://threedubmedia.com/code/event/drag/) para proveer soporte para drag a **[Flexslider](http://flexslider.woothemes.com/)** (es decir que permita arrastrar los sliders con el ratón en el desktop, de modo similar a como permite hacerlo en un dispositivo tipo touch):  
  
\- Usando el plugin jquery.event.drag (http://threedubmedia.com/code/event/drag/)  
\- En jquery.flexslider.js, copio el bloque que da soporte a mousewheel y lo uso como base para el soporte para drag:  
```
...  
// MOUSEWHEEL:  
if (vars.mousewheel) {  
  slider.bind('mousewheel', function(event, delta, deltaX, deltaY) {  
    event.preventDefault();  
    var target = (delta < 0) ? slider.getTarget('next') : slider.getTarget('prev');  
    slider.flexAnimate(target, vars.pauseOnAction);  
  });  
}  
// DRAG:  
if (vars.drag) {  
  slider.bind('drag', function(event, delta) {  
    event.preventDefault();  
    var target = (delta.deltaX < 0) ? slider.getTarget('next') : slider.getTarget('prev');  
    slider.flexAnimate(target, vars.pauseOnAction);  
  });  
}  
...  

```  
\- También agrego 'drag' en los defaults de flexslider:  
```
...  
$.flexslider.defaults = {  
  ...  
  mousewheel: false,  
  drag: false,  
...  

```  
\- Entonces, en el script, se puede usar 'drag: true' cuando se requiera:  
  
```
$('.flexslider').flexslider({  
  animation: 'slide',  
  slideshow: false,  
  drag: true  
});  

```  
_Referencia:  [Request: add mouse dragging for desktop users](https://github.com/woothemes/FlexSlider/issues/214)_

_*Url archivado: [Resolviendo Soporte Drag para Flexslider](https://akcdev.blogspot.com/2012/09/resolviendo-soporte-drag-para-flexslider.html)*_
