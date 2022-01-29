---
title: 'CSS: Checkbox hack para controles personalizados'
date: 2017-12-04T13:55:00.003-05:00
draft: false
url: /2017/12/css-checkbox-hack-para-controles
tags: 
- css
- html
- hacking
- blogger
---

¿Cómo aplicar un estilo como respuesta a un click, usando sólamente CSS?  
  
Se puede hacer con el **_checkbox hack_**.  
  

### Principio

*   Un label asociado a un input puede recibir el click por él

*   Puede haber varios labels para un mismo input
*   Ocultando el input (difícil de personalizar), queda el label para contener un control más fácil de personalizar

*   La pseudoclass _:checked_ permite ubicar un checkbox seleccionado
*   El selector _aaa + bbb_ permite seleccionar un _bbb _que esté (declarado) inmediatamente después de un aaa

### Patrón 1

[![](https://3.bp.blogspot.com/-1Gscr40pDfs/WiWSdmH8IyI/AAAAAAAALCc/wDZCeY5tKOoLsX38vt26PkTPBrnbu59LACLcBGAs/s320/checkbox-hack-1.png)](https://3.bp.blogspot.com/-1Gscr40pDfs/WiWSdmH8IyI/AAAAAAAALCc/wDZCeY5tKOoLsX38vt26PkTPBrnbu59LACLcBGAs/s1600/checkbox-hack-1.png)

HTML:  
```
<input id="checkbox-control" type="checkbox">  
<label for="checkbox-control">Control</label>  

```  
CSS:  
```
#checkbox-control:checked \+ label {...}  

```

### Patrón 2

[![](https://1.bp.blogspot.com/-hPSUeMr2WFM/WiWMt7-8ndI/AAAAAAAALCM/lFX-v5fXxGwlLiq_4OG9aS5r3I1xWQaAQCLcBGAs/s320/checkbox-hack.png)](https://1.bp.blogspot.com/-hPSUeMr2WFM/WiWMt7-8ndI/AAAAAAAALCM/lFX-v5fXxGwlLiq_4OG9aS5r3I1xWQaAQCLcBGAs/s1600/checkbox-hack.png)

HTML:  
```
<label for="checkbox-control">Control</label>  
<input id="checkbox-control" type="checkbox">  
<div class="target">Target</div>  

```  
CSS:  
```
#checkbox-control:checked \+ .target {...} 
```

### Patrón 3

[![](https://2.bp.blogspot.com/-qCdTTUl_qKU/WiWSmvSD1zI/AAAAAAAALCg/sxRtmHl5eSwVuhr0AnkBUccjd--961jcACLcBGAs/s400/checkbox-hack-3.png)](https://2.bp.blogspot.com/-qCdTTUl_qKU/WiWSmvSD1zI/AAAAAAAALCg/sxRtmHl5eSwVuhr0AnkBUccjd--961jcACLcBGAs/s1600/checkbox-hack-3.png)

HTML:  
```
<input id="checkbox-control" type="checkbox">  
<label for="checkbox-control">Control</label>  
<div class="target">Target</div>  

```  
CSS:  
```
#checkbox-control:checked \+ label {...}  
#checkbox-control:checked \+ label + .target {...}  

```

### Ideas de aplicación

*   Checkbox personalizado

*   Toggle

*   Tabs
*   Dropdown menu
*   Dot control para slider
*   Árbol desplegable

_Ver unos ejemplos en [A check studio](https://codepen.io/akobashikawa/pen/WXmdGp/), en [CodePen](https://codepen.io/)_

  

### Referencias

*   Stuff you can do with the “Checkbox Hack”  
    [https://css-tricks.com/the-checkbox-hack/](https://css-tricks.com/the-checkbox-hack/)
*   :checked  
    [https://css-tricks.com/almanac/selectors/c/checked/](https://css-tricks.com/almanac/selectors/c/checked/)
*   CSS Selector Reference  
    [https://www.w3schools.com/cssref/css\_selectors.asp](https://www.w3schools.com/cssref/css_selectors.asp)

_*Url archivado: [CSS: Checkbox hack para controles personalizados](https://akcdev.blogspot.com/2017/12/css-checkbox-hack-para-controles.html)*_
