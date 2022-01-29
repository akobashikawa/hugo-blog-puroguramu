---
title: 'En el Dojo'
date: 2012-01-20T00:52:00.001-05:00
draft: false
url: /2012/01/en-el-dojo
tags: 
- zen
- programación
- tdd
- agil
- blogger
---

[![](http://4.bp.blogspot.com/-0RvQY1w4nQ8/TxkAwHGWU_I/AAAAAAAABvI/yPAe3BjgpDc/s320/dojo_port.jpg)](http://4.bp.blogspot.com/-0RvQY1w4nQ8/TxkAwHGWU_I/AAAAAAAABvI/yPAe3BjgpDc/s1600/dojo_port.jpg)

Hoy asistí a un dojo de programación. Me ha parecido una experiencia muy enriquecedora.  
  
Un dojo de programación trata de seguir la idea de un dojo de artes marciales en cuanto a formar un ambiente donde podamos ejercitarnos fuera de la contienda real (que viene a ser el día a día con los proyectos que desarrollamos).  
  
La práctica se trató esta vez de usar TDD y una especie de Pair Programming para resolver el problema de convertir números arábigos, los que usamos normalmente, a la notación romana.  
  
TDD son las iniciales de Test Driven Development, Desarrollo Guiado por Pruebas. Pablo Tortorella, quien nos guiaba, dijo que le parecía mejor pensar en Desarrollo Guiado por Ejemplos, ya que una prueba es en realidad un caso particular que ponemos como ejemplo para que el programa que hacemos lo intente resolver. Un ambiente de pruebas toma la prueba y la lleva a cabo a ver si el programa la pasa. Entonces, en TDD: 1) definimos una prueba simple 2) corremos la prueba (incluso sin tener ningún programa; es importante ver que falla) 3) se enfoca uno en implementar en el programa lo mínimo necesario hasta lograr pasar la prueba 4) si se nota que algo puede refactorizarse (simplificar, eliminar duplicaciones o dependencias innecesarias), hacerlo, luego pasar al paso 1) e ir repitiendo el ciclo, con pasitos de bebe, dejando que el programa evolucione hasta el nivel que deseemos.  
  
Para alguien habituado a programar al estilo tradicional, donde se pretende resolver todo el problema en la fase de diseño, antes incluso de empezar a programar, puede costar un poco enfocarse en pequeños pasos y no intentar codificar toda la solución de una vez. Pero el estilo tradicional realmente tiene problemas. Precisamente en respuesta a esos problemas surgieron cosas como la eXtreme Programming, TDD y Agile.  
  
En el caso del problema de la conversión a números romanos, probablemente uno imagine ahora, sin necesidad de programar, una manera de resolver el problema y podría programarla en un rato. Pero, deténgase y trate de hacerlo en pequeños pasos, ideando una prueba simple y trivial cada vez, para ver a dónde va conduciendo.  
  
Con el dojo me di cuenta que, conforme avanzan las iteraciones, van apareciendo patrones que van sugiriendo la solución. El tiempo de la práctica se acabó, pero creo que eventualmente llegaríamos a solucionar el problema.  
  
Camino de regreso, recordaba la forma en que el código iba proponiéndose y refactorizándose. Había cierto algoritmo en eso. Me pregunto si sería posible programar a una computadora para que halle esa solución evolutiva usando TDD. Quizás sí. Entonces, me pregunto si sería posible que una computadora, o un conjunto de computadoras, realizando pequeños pasos de bebe, resolviendo casos triviales, puedan resolver cualquier tipo de problema de programación, simplemente por evolución, usando TDD. Me pregunto si será ese el futuro.  
  

_Crédito de la imagen: [CIO Dojo](http://ciodojo.com/about/)_

_*Url archivado: [En el Dojo](https://akcdev.blogspot.com/2012/01/en-el-dojo.html)*_
