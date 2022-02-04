---
title: 'Escribiendo aplicaciones para Facebook'
date: 2012-03-14T10:44:00.005-05:00
draft: false
url: /2012/03/escribiendo-aplicaciones-para-facebook
tags: 
- programación
- facebook
- web
- blogger
---

[![](https://4.bp.blogspot.com/-LEoA6cgCUC4/T2C-FYMRfPI/AAAAAAAABxI/t_oCUVhz1Ek/s200/facebook.png)](https://4.bp.blogspot.com/-LEoA6cgCUC4/T2C-FYMRfPI/AAAAAAAABxI/t_oCUVhz1Ek/s1600/facebook.png)

  
Escribiendo aplicaciones para Facebook  
A pesar de la documentación que hay en [https://developers.facebook.com/docs/](https://developers.facebook.com/docs/), necesitaba algo que me diera una perspectiva en el tema. Leyendo un poco en otras fuentes, fui entendiendo la idea.  
  
La idea  
¿Qué es una aplicación para Facebook? Imaginaba que sería algo como un programa, construido con un framework, en un cierto lenguaje y con cierto esquema, que Facebook ejecutaba para los usuarios que lo hubieran jalado de la galería de aplicaciones.  
  
Pero no es así. Se trata de aplicaciones web escritas en el lenguaje y esquema que uno prefiera, corriendo en el hosting que uno prefiera y que uno puede asociar con Facebook siguiendo ciertos esquemas.  
  
En el esquema **_Website_**, la aplicación tiene su propio url, como de costumbre. El usuario accede y la aplicación puede hacer internamente invocaciones a los servicios de Facebook antes de mostrar un resultado al usuario.  
  
En el esquema **_Application_**, la aplicación tiene su propio url, como de costumbre, pero Facebook actúa como proxy, asignándole a la aplicación un url bajo su dominio. El usuario accede al url dentro de Facebook, Facebook pasa los requerimientos al url externo de la aplicación, la aplicación puede hacer internamente invocaciones a los servicios de Facebook antes de devolver un resultado, Facebook recibe ese resultado y lo publica en un iframe.  
  
Referencias  

*   "Facebook Application Development, For Dummies"  
    Jesse Stay, 2011  
    ISBN: 978-0-470-76873-0

_*Url archivado: [Escribiendo aplicaciones para Facebook](https://akcdev.blogspot.com/2012/03/escribiendo-aplicaciones-para-facebook.html)*_
