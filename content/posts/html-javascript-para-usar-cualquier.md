---
title: 'HTML + Javascript para usar cualquier framework'
date: 2011-10-05T18:04:00.000-05:00
draft: false
url: /2011/10/html-javascript-para-usar-cualquier
tags: 
- framework
- web
- blogger
---

Todo o nada  
Para hacer una aplicación web, se suele optar por alguna de las siguientes alternativas:  
  
a) Usar completamente un framework propio.  
b) Usar completamente un framework estándar.  
  
La alternativa a) significa volver a implementar muchas de las cosas que ya se han resuelto en otros frameworks.  
  
La alternativa b) significa depender completamente de lo que esté implementado en el framework elegido.  
  
Pero pienso que hay otra alternativa. Una que no use la palabra _completamente_.  
  
Imagine all the people  
Imagine que no tiene que volver a escribir su aplicación web en otro lenguaje simplemente para usar algunas de las cosas que ofrece cierto framework escrito en ese lenguaje.  
  
Imagine que no tiene que volver a escribir su aplicación web simplemente para usar algunas de las cosas que ofrece la siguiente versión del framework.  
  
Imagine un framework en el que pudiera usar cualquier cosa que ya se hubiera implementado en otro framework, sin necesidad de volver a escribirlo.  
  
Imagine que todos los frameworks pudieran trabajar juntos y usted pudiera escoger de esa feria de componentes los que mejor se adaptaran para cada cosa que necesitara. Todas las versiones y todos los lenguajes.  
  
Cómo hacerlo  
Se me ocurre al menos una manera.  
  
Que el contenido dinámico se construya usando Javascript. Usando técnicas AJAX, se puede hacer una solicitud a cierto URL, con los parámetros que se requieran. En ese URL, un servidor procesa la solicitud, usando el framework y lenguaje de programación que sea, y devuelve una respuesta JSON. Con la respuesta, se construye la vista de la respuesta.  
  
Pensando sobre eso, noto que en el modelo cliente-servidor del HTML, se obliga a que el navegador reemplace _completamente_ el contenido de la página con la respuesta. Otra vez esa palabrita.  
  
Quizás sería interesante extender la especificación HTML para admitir reemplazos parciales. AJAX es el testimonio de que eso se necesita. Flash también lo implementa (llamándolo _carga dinámica_).  
  
Por el momento, la manera de hacer eso es con ayuda de Javascript (y alguna biblioteca como jQuery).  
  
MVC  
Un patrón de muy difundido en los frameworks actuales es MVC (modelo-vista-controlador).  
  
Básicamente, se piensan las soluciones en términos de tres tipos de componentes: controladores, modelos y vistas.  
  
Un controlador recibe la solicitud, determina qué hacer, utilizando los modelos necesarios y pasa los resultados a una vista.  
  
Algunos dicen que la idea principal es que los diseñadores no se vean obligados a programar ni los programadores a diseñar. Pero, como nadie lo ha logrado (para hacer cualquier template se combina diseño con programación), pienso que se trata más de una cuestión de orden.  
  
Si se usa Javascript para carga dinámica, lo que ocurre es que lo que devuelven las vistas puede ser usado no sólo para reemplazos totales, sino también para reemplazos parciales.  
  
¿Por qué no se hace?  
Eso mismo me pregunto.  
  
He ido desarrollando estas ideas luego de observar como la comunidad Drupal está rehaciendo los módulos que funcionaban bien en Drupal 6 para que funcionen en Drupal 7. Es un riesgo. Se habla que algunos proyectos, como Perl, han perdido comunidad por hacer maniobras como esa.  
  
Ya se ha iniciado la carrera hacia Drupal 8... llegado el momento, ¿volverán a reescribir los módulos?... ¿y así, sucesivamente?  
  
Me parece que debe haber un camino mejor.  
  
¿Qué le parece?

_*Url archivado: [HTML + Javascript para usar cualquier framework](https://akcdev.blogspot.com/2011/10/html-javascript-para-usar-cualquier.html)*_
