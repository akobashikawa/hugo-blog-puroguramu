---
title: 'Generación modular de HTML'
date: 2011-07-08T15:39:00.004-05:00
draft: false
url: /2011/07/generacion-modular-de-html
tags: 
- html
- framework
- web
- blogger
---

Actualmente, cuando desarrolla un sitio usando cierto framework, no lo puede modificar con otro. Si está metido en esto, puede parecer obvio y hasta natural. Pero, si lo vemos en perspectiva, es algo así como una limitación por diseño. Algo que se podría mejorar.  
  
Sites estáticos y dinámicos  
Aunque el objetivo final es enviar html al navegador, en el desarrollo de sites dinamicos el paso intermedio es crear un conjunto de archivos que generen el html que se desea.  
  
Cuando se trata de sites estáticos es más simple. Uno coloca los archivos en el directorio web y el servidor web los envía al navegador tal cual. Esos archivos son html, css, javascript, o imágenes que el desarrollador puede modificar con la libertad de elegir entre muchas herramientas para eso.  
  
Cuando se trata de sites dinámicos las cosas se suelen complicar. En general, primero se plasma el diseño en un site estático, que luego es desmantelado para ver el modo de generarlo. Finalmente, se obtiene el site dinámico, que actúa como un **generador total** del html que se desea.  
  
Ese suele se el enfoque más usado. Practicamente siempre que use C, Java, PHP, Ruby, Python, o lo que sea, lo que construye es siempre un **generador total** de html.  
  
Frameworks exclusivos  

[![](https://1.bp.blogspot.com/-ZFfl-lfhfaA/Tht63DV_zMI/AAAAAAAABXc/ntK3Ds6R2pU/s200/generador-total-html.png)](https://1.bp.blogspot.com/-ZFfl-lfhfaA/Tht63DV_zMI/AAAAAAAABXc/ntK3Ds6R2pU/s1600/generador-total-html.png)

El enfoque de la generación total tiene el problema de tender a soluciones monolíticas, con sus vicios asociados.  
  
Si quiere modificar el site, tiene que modificar el generador, y tiene que entender el framework-que-todo-lo-hace.  
  
Cuando un framework mejora, esa nueva versión no le sirve para el site que hizo con la versión antigua y tendría que reescribir el site bajo los nuevos términos.  
  
Si otro framework implementa una característica que le gustaría, tendrá que esperar hasta que sea implementada, otra vez, en los términos del framework que usted usa.  
  
Un montón de trabajo repetido.  
  
Frameworks inclusivos  

[![](https://2.bp.blogspot.com/-vehqqtlfaAc/Tht6-C29-7I/AAAAAAAABXg/Ql6oLmYpE_4/s200/generacion-parcial-html.png)](https://2.bp.blogspot.com/-vehqqtlfaAc/Tht6-C29-7I/AAAAAAAABXg/Ql6oLmYpE_4/s1600/generacion-parcial-html.png)

Una alternativa podría ser hacer **generadores modulares**. En lugar de generar el html de toda la página, un generador modular sólo produce el html de cierta región específica.  
  
Para indicar dónde colocar el html dinámico, habrían algunas alternativas:  
  

*   Que la página use javascript, obtenga el resultado y lo coloque.
*   Que la página use un tag especial que se reemplace por el contenido dinámico.
*   Que el servidor ubique los lugares dónde hacer el reemplazo y los haga.

  
La primera alternativa es relativamente asequible con lo que ya tenemos. Para las otras, habría que hacer un framework que se encargue de hacer los reemplazos adecuados (por ejemplo uphp).  
  
Ya mismo podríamos empezar a desarrollar sites de ese modo. Una ventaja grande de usar generadores modulares, es que no importa en que lenguaje de programación se hacen, ni que framework usan, ni que versión del framework. Simplemente se usan. Podría usar generadores modulares escritos en C, Java, PHP, Python y Ruby... todos juntos!

_*Url archivado: [Generación modular de HTML](https://akcdev.blogspot.com/2011/07/generacion-modular-de-html.html)*_
