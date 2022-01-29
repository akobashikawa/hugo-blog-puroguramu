---
title: 'El Principio de la Máquina Mínima'
date: 2016-11-01T13:01:00.002-05:00
draft: false
url: /2016/11/el-principio-de-la-maquina-minima
tags: 
- ideas
- desarrollo
- blogger
---

El desarrollo de un sistema es una serie problemas que se van resolviendo.  
  
Puede haber varias maneras de resolver un problema. Podemos hacer uso de herramientas. El equivalente en software de martillos o cinceles.  
  
El conjunto de todas las herramientas que usamos es parte de nuestro sistema de construcción. Aún sin proponérnoslo, el uso de herramientas determina siempre un framework de desarrollo.  
  
Como en todo framework, a cambio de la ayuda que nos da, habrá limitaciones y convenciones que tenemos que seguir. Habrá cosas que un martillo nos permitirá hacer y otras que no.  
  
Podemos visualizar al framework como una gran máquina, compuesta por todas las herramientas y las convenciones que determinan.  
  
Una máquina puede ser muy útil. Pero tiene un costo adquirirla o construirla. Un costo dominar su uso. Y también un costo de operación.  
  
Una máquina complicada tiene un gran costo de operación.  
  
A veces usar una herramienta puede constituir un problema por sí mismo. Como cuando se maneja una gran herramienta en una obra.  
  
Una **máquina mínima** sería el framework menos complicado que hace lo que necesitamos que se haga en un contexto determinado.  
  
Puede ser que una grúa también se pueda usar para clavar un clavo. O una piedra. Pero un martillo es el menos complicado de los tres. Cuesta más que una piedra, pero es más confiable y requiere menos esfuerzo. Puede que una grúa también pueda clavar un clavo, además de levantar los materiales de construcción de la casa que construimos, pero es mucho más costosa, espaciosa, requiere ser encendida y una gran pericia para lograrlo.  
  
El contexto es importante.  
  
Puede ser que para clavar un clavo un martillo esté bien. Pero si necesitamos algo más masivo, tal vez notemos que podríamos usar un martillo neumático. En ese otro contexto, usar el martillo neumático puede ser menos complicado.  
  
El principio de la máquina mínima es simplemente evitar el desperdicio de usar ambientes de desarrollo con características que excedan lo que realmente se necesita.  
  
Así, usar un ambiente similar al de producción, conectado a motores de bases de datos, optimmizadores y caches, para desarrollar los templates, es utilizar potencia y complejidad innecesaria. Podría bastar con un servidor web simple con servicio ficticio de datos, incluso datos en hardcode. Para esa etapa, en ese contexto, es suficiente.  
  
El ambiente que sirve muy bien para desarrollar backend no necesariamente es el mejor para desarrollar frontend.  
  

El mito del framework zero
--------------------------

A veces alguien propone no usar ningún framework. Después de todo, no tenemos que preocuparnos de aprender a usar un framework si este no existe en primer lugar, ¿no es así? Terminan de desarrollar un sistema y dicen "no he usado ningún framework".  
  
Pero si analizamos su trabajo, encontraremos un conjunto de módulos, herramientas, convenciones y patrones de uso. No habrá sido bautizado, pero eso es un framework.  
  
Entonces, ¿siempre hay un framework?. Así es.  
  
La cuestión se reduce a si es tuyo o de alguien más.  
  
Es mejor que sea mío, después de todo, tengo así el control absoluto de mi proyecto y no tengo que aprender nada más, ¿no es así?  
  
Como sabes, hay muchas peculiaridades que tener en cuenta a la hora de resolver un problema para el mundo real. Diferencias entre navegadores, inconsistencias en los lenguajes, cosas que no funcionan como se supone que deberían funcionar. Y suelen ser criaturas elusivas, que no se muestran frente al desarrollador sino que les gusta saltar frente a la cara del usuario.  
  
Puede ser que seas un desarrollador genial. El mejor del mundo. Pero, ¿tienes realmente todas esas horas hombre para atender los issues que provienen del uso de tu software?, ¿tienes el tiempo para documentarlo detalladamente?. Quizás sea buena idea volverlo un proyecto abierto y aceptar la ayuda de la comunidad. Con organización, promoción, trabajo y algo de tiempo quizás lleguemos a obtener... algo parecido a uno de los frameworks que podríamos haber elegido al inicio? Pero, está bien, ¿no?, después de todo ¡tenemos un nuevo framework!.  
  
¿Era el problema principal que querías resolver? ¿Era realmente necesario?  
  
Usar un framework propio otorga no solo un gran poder, sino una gran responsabilidad.  
  
En estos tiempos es fácil retroceder ante la primera dificultad y tratar de hacer todo desde cero, puro, como a mi me gusta. Es la ilusión de que si construyes la herramienta perfecta, lo que constuyas con esa herramienta también lo será. Pero son dos cuestiones completamente diferentes. Puedes ser bueno haciendo herramientas, pero eso no garantiza que harás una buena mesa.  
  
Un buen consejo es no caer en la parálisis del perfeccionismo. Usar primero lo que ya hay. Luego corrige lo que puedas. Luego mejora lo que puedas.  
  

Los bundlers
------------

Un bundler, como webpack, puede ayudar mucho a la hora de construir los bundles que se suelen requerir para desplegar una aplicación.  
  
En la etapa de despliegue.  
  
Sin embargo, hay flujos de trabajo que fuerzan a usar el bundler en la etapa de desarrollo.  
  
Eso le agrega complejidad al trabajo. Puede ser una máquina mínima para el contexto de despliegue, pero no lo es para el contexto de desarrollo.  
  

Transpiladores
--------------

Un transpilador permite usar una sintaxis más cómoda en la fuente. Luego de la transpilación se obtendrá un resultado que se puede usar en el despliegue.

  

Puede ser que para la parte de desarrollo se obtenga menos complejidad. Pero es a cambio de mayor complejidad para compartir código, mantenerlo y depurarlo.

  

¿Realmente te está permitiendo el transpilador tener un flujo de trabajo más simple y ser más productivo? 

  

A veces, se critica alguna librería por su tamaño. Cuando usas transpiladores quizas la fuente sea pequeña, pero el resultado puede ser más grande que lo normal y menos optimizable.

  

A veces es simplemente la ilusión de que usar lo mejor producirá lo mejor.

  

Es importante tener en cuenta el contexto y buscar la simplicidad de manera más holística.

_*Url archivado: [El Principio de la Máquina Mínima](https://akcdev.blogspot.com/2016/11/el-principio-de-la-maquina-minima.html)*_
