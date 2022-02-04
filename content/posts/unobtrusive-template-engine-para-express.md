---
title: 'Unobtrusive Template Engine para Express'
date: 2015-12-23T00:22:00.001-05:00
draft: false
url: /2015/12/unobtrusive-template-engine-para-express
tags: 
- nodejs
- javascript
- express
- blogger
---

[![](https://1.bp.blogspot.com/-UcP01Kq0lfI/TiSIJ7jmV1I/AAAAAAAABXk/ACnSY0H_zz8/s1600/free-v.png)](https://1.bp.blogspot.com/-UcP01Kq0lfI/TiSIJ7jmV1I/AAAAAAAABXk/ACnSY0H_zz8/s1600/free-v.png)

  
El uso de los sistemas de templates típicos (como jade, handlebars, jinja, etc), involucra aprender el lenguaje del sistema de templates y procesar el html base para que se acomode a los requerimientos del sistema de template.

  

El proceso se llama templating. El templating para jade es diferente que el de handlebars, o jinja.

  

Si uno usa express con jade, los templates que obtenga no servirán para express con handlebars.

  

Y esa forma de trabajo está bastante extendida. Si uno usa Drupal, los templates que obtenga no servirán para Wordpress. Aún más, si uno usa Drupal 6, los templates que obtenga no servirán para Drupal 7.

  

Todas las horas que se invierten en un templating no se pueden reutilizar si se cambia de framework. Es algo que mucha gente ve como algo natural pero me molesta desde hace algún tiempo :-P

  

  

**[Web frameworks](https://www.slideshare.net/akobashikawa/web-frameworks-7456538 "Web frameworks")** por **[Antonio Kobashikawa Carrasco](https://www.slideshare.net/akobashikawa)**

  

Hace un tiempo, ensayé la idea con php y querypath. También con Wordpress y querypath.  
  
[http://akcideas.blogspot.pe/2011/05/unobstrusive-web-dev.html](http://akcideas.blogspot.pe/2011/05/unobstrusive-web-dev.html)  
  
Esta vez con nodejs-express con cheerio.

  

[https://github.com/akobashikawa/express-unobtrusive-template-engine](https://github.com/akobashikawa/express-unobtrusive-template-engine)  
  

### La visión

La idea es hacer los reemplazos necesarios usando los mecanismos de jquery. Encontrar un modo en que el código base html no se toque.  
  
Imagina que maquetas un site en html5. Puro frontend. Tomas ese conjunto de archivos y los dejas caer en cierto directorio de un framework. Y que el framework sea capaz de usarlo tal cual, sin que tengas que procesarlo. Luego, paulatinamente, unobtrusivamente, vas haciendo los reemplazos dinámicos.  
  
Claro que hay que hace templating de todos modos, pero ya no es en el html, sino en el backend de la vista.  
  
Me parece que sería más productivo desarrollar de ese modo.

_*Url archivado: [Unobtrusive Template Engine para Express](https://akcdev.blogspot.com/2015/12/unobtrusive-template-engine-para-express.html)*_
