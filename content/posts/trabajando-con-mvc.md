---
title: 'Trabajando con MVC'
date: 2009-11-12T16:49:00.005-05:00
draft: false
url: /2009/11/trabajando-con-mvc
tags: 
- mvc
- programación
- php
- web
- blogger
---

[![](https://1.bp.blogspot.com/_K2xwnQ4Llso/SvyGhDAupyI/AAAAAAAAAIE/BMymWRYXVuo/s320/zen_piedras.jpg)](https://1.bp.blogspot.com/_K2xwnQ4Llso/SvyGhDAupyI/AAAAAAAAAIE/BMymWRYXVuo/s1600-h/zen_piedras.jpg)  

Lo que suelo hacer es ir como el cangrejo, de atrás para adelante:  

*   Hago una vista estática, con datos en duro. Lo pruebo.  
    
*   Ubico los datos que podrían ser dinámicos y uso variables y lógica de vista para generar los datos en duro. Todo eso en la misma vista. Lo pruebo, debe funcionar igual que antes.  
    
*   La lógica de vista queda en la vista, pero paso al controlador la asignación de valores en duro a las variables requeridas por la vista. Lo pruebo, debe funcionar igual que antes.
*   Paso a un modelo la generación de los datos en duro requeridos por el controlador para enviar a la vista. Lo pruebo, debe funcionar igual que antes.
*   Creo un sistema de tablas de donde el modelo pueda extraer los datos que he venido usando en duro. Lo pruebo, debe funcionar como antes.

  
En cada paso, me inclino por la solución más natural y simple disponible. Evito considerar requerimientos que _podrían_ ser buenos para el futuro o para otro caso. De ese modo la solución tiene lo que se necesita y nada más. Evito compromisos innecesarios y disminuyo las probabilidades de efectos secundarios.  
  
Luego que algo funciona, trato de eliminar duplicaciones, y luego optimizar. Es mejor postergar la optimización lo más que se pueda, ya que optimizar frecuentemente _ensucia_ el código con trucos y técnicas que no dejan ver bien la lógica de la solución.  
  
Programar código directamente optimizado es una trampa, una ilusión. Hace más lento el desarrollo y complica transitar cada escalón. Cuando algo falla, está todo tan enredado que prefieres descolgarte por la baranda que revisar la escalera.  
  
Es mejor programar por niveles de complejidad, dejando la optimización para el final. Como cuando se construye una casa; los acabados no se ponen hasta el final. De otro modo los constructores gastarían energía y tiempo extra en cuidar un mobiliario y accesorios que les estorba el paso, y que encima nadie puede usar bien.  
  

Breve crítica sobre el uso del idiomas y variables con prefijos  

  
Reconozco que para resolver muchos tipos de problemas, así como para organizar las cosas suele ser más sencillo pensar de atrás hacia adelante, como en el inglés (me parece que no por nada los lenguajes de programación están en inglés). De afuera hacia adentro. De lo general a lo particular. La organización de directorios, nombres, etc se hace más clara y más compatible con otras organizaciones, que si se fuerza a usar español sólo porque sí.  
  
Sin embargo, si mis conceptos están en español, las variables directamente relacionadas con ellos también aparecerán en español (por ejemplo los nombres de las tablas, modelos, controladores), pero todas las demás variables internas (como los contadores), prefijos, sufijos, etc mantienen el estandar de un desarrollo en inglés. No es práctico traducir el nombre de las entidades, porque frecuentemente habrán conversaciones sobre ellas y carga el desarrollo llevar un tabla de equivalencias y pensar con esas equivalencias encima. Cuantos más ligeros, mejor.  
  
Así, uso producto\_precio en lugar de precio\_producto, entidad\_caracteristica en lugar de caracteristica\_entidad.  
  
Además, uso setPrecio(), getProducto(), etc, porque es más corto que establecerPrecio(), obtenerProducto(), etc. Hay IDEs, como Eclipse, que tienen generadores de getters y setters.  
  
Esta forma práctica de usar el idioma no tiene que ver con el respeto a la lengua materna o lo que recomiende la RAE para hablar. Eso es otro asunto. Lo importante es que el desarrollo sea claro, práctico, el mantenimiento fácil, y que el programa funcione.  
  
Por otro lado, me parece innecesario el uso de prefijos sólo para señalar que _cierta variable pertenece a tal módulo asociado a tal tabla de la base de datos del proyecto tal_. Quizás puedan ayudar a ubicar la variable dentro del contexto del proyecto, pero es poca ganancia comparado con el lastre que significará usar esas variables en el día a día. Es mejor usar variables nombradas lo más naturalmente y simple que se pueda.  
  
Además, siguiendo un orden natural y claro no se necesitará señalar '_que cierta variable pertenece a tal módulo asociado a tal tabla de la base de datos del proyecto tal_'; todo eso se podrá deducir por contexto.  
  
Claro que todo esto no es algo rígido. Son simplemente pautas que trato de seguir y que voy corrigiendo conforme veo más casos, me equivoco y aprendo.

_*Url archivado: [Trabajando con MVC](https://akcdev.blogspot.com/2009/11/trabajando-con-mvc.html)*_
