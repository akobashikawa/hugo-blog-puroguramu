---
title: 'Cómo obtener las partes de una ruta usando javascript'
date: 2010-11-30T14:27:00.005-05:00
draft: false
url: /2010/11/como-obtener-las-partes-de-una-ruta
tags: 
- javascript
- blogger
---

[![](https://1.bp.blogspot.com/_K2xwnQ4Llso/TPVPigkfQ2I/AAAAAAAABOo/gEH24HFUdLY/s1600/split.png)](https://1.bp.blogspot.com/_K2xwnQ4Llso/TPVPigkfQ2I/AAAAAAAABOo/gEH24HFUdLY/s1600/split.png)

  
Una ruta como http://par1/par2/par3/par4/par5 se puede separar en php usando algo como [explode()](http://www.php.net/manual/es/function.explode.php).  
En javascript, una forma de hacerlo es usando [split()](http://www.w3schools.com/jsref/jsref_split.asp). Por ejemplo:  
  
```
var path = 'http://par1/par2/par3/par4/par5';  
var parts = path.split('/');  
var n = parts.length;  
var par5 = parts\[n-1\];  
var par4 = parts\[n-2\];  
var par3 = parts\[n-3\]; // y así sucesivamente...  

```  

_[Vea el artículo original en DrupaLab](http://drupalab.kobaonline.com/portal/content/como-obtener-partes-ruta-usando-javascript)_

_*Url archivado: [Cómo obtener las partes de una ruta usando javascript](https://akcdev.blogspot.com/2010/11/como-obtener-las-partes-de-una-ruta.html)*_
