---
title: 'Cómo definir un selector CSS que requiera dos clases'
date: 2011-04-07T17:24:00.002-05:00
draft: false
url: /2011/04/como-definir-un-selector-css-que
tags: 
- css
- blogger
---

[![](https://2.bp.blogspot.com/-Ohce1BBDLOc/TZ45nfTCbfI/AAAAAAAABUc/WaAacOnK-QQ/s1600/css-icon.png)](http://2.bp.blogspot.com/-Ohce1BBDLOc/TZ45nfTCbfI/AAAAAAAABUc/WaAacOnK-QQ/s1600/css-icon.png)

  

El problema que tenía involucraba bloques similares a:  
  
**proyectos-vista\_1**  
```
<div class="view view-proyectos view-display-id-page\_1">  
  ...  
</div>  

```  
**proyectos-vista\_2**  
```
<div class="view view-proyectos view-display-id-page\_2">  
  ...  
</div>  

```  
**noticias-vista\_1**  
```
<div class="view view-noticias view-display-id-page\_1">  
  ...  
</div>  

```  
**noticias-vista\_2**  
```
<div class="view view-noticias view-display-id-page\_2">  
  ...  
</div>  

```  
Necesitaba aplicar un estilo únicamente al bloque proyectos-vista\_1. Podría ser más fácil si éste tuviera un id, pero no lo tenía (así lo construye Drupal, en este caso).  
  
La solución la encontré en [este artículo](http://www.bennadel.com/blog/680-Defining-A-CSS-Selector-That-Requires-A-Multi-Class-Union.htm). Consiste en usar un selector como:  
  
```
.view-proyectos.view-display-id-page\_1 {  
  ...  
}  

```  
Qué sencillo. No me lo imaginaba :-) Ojalá te sirva de ayuda tambien.  
  
**Referencia**  
[Defining A CSS Selector That Requires A Multi-Class Union](http://www.bennadel.com/blog/680-Defining-A-CSS-Selector-That-Requires-A-Multi-Class-Union.htm)

_*Url archivado: [Cómo definir un selector CSS que requiera dos clases](https://akcdev.blogspot.com/2011/04/como-definir-un-selector-css-que.html)*_

---
### Comentarios archivados:

>
> Muchas gracias... lo estaba buscando hace mucho!!!
> \
> [Unknown](https://www.blogger.com/profile/13695390368698127638 "noreply@blogger.com") [2013-08-08 09:44]
