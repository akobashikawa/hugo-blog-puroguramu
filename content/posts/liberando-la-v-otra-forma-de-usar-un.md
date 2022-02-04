---
title: 'Liberando la V, otra forma de usar un framework MVC'
date: 2011-07-18T14:24:00.007-05:00
draft: false
url: /2011/07/liberando-la-v-otra-forma-de-usar-un
tags: 
- desarrollo
- framework
- blogger
---

[![](https://4.bp.blogspot.com/-UcP01Kq0lfI/TiSIJ7jmV1I/AAAAAAAABXk/ACnSY0H_zz8/s1600/free-v.png)](https://4.bp.blogspot.com/-UcP01Kq0lfI/TiSIJ7jmV1I/AAAAAAAABXk/ACnSY0H_zz8/s1600/free-v.png)

En el esquema MVC, se tienen _modelos_ que proveen datos, y _controladores_ que toman los datos y los procesan de algún modo antes de enviar el resultado a la _vista_.  
  
En web, los framework MVC tratan de seguir este esquema para organizar el trabajo. En teoría, parte del equipo se puede enfocar en los modelos, otro en los controladores y otro en las vistas.  
  
Al margen de si en la práctica realmente se cumple esto, es notable un problema: los modelos, vistas y controladores desarrollados determinan finalmente un API no estándar que termina "enjaulando" el producto final. Si decide actualizar el framework a la siguiente versión, encontrará que puede acarrear para el site un trabajo similar a volverlo a hacer. Aún más difícil es pasar un site de un framework a otro.  
  
Esto genera algunos vicios. Si otro framework implementa cierta característica ventajosa, no lo podemos usar; tenemos que esperar hasta que algo similar sea implementado en el que usamos. Esa característica debe ser expresada **otra vez**, en los términos de nuestro framework.  
  
En mi opinión, esto ocurre porque la página web ha sido forzada a encajar en el esquema MVC sobrescribiendo sus características estándar por otras propietarias, definidas por su sistema de templates particular.  
  
Sí, aunque el framework sea open source, en este caso se está comportando como un ente propietario. Y eso es lo que provoca esta limitación de libertad.  
  
Para tener más libertad, libere la vista. Puede desarrollar su sitio web de modo que las vistas sean HTML estándar y las partes dinámicas carguen con javascript (AJAX) los datos obtenidos de invocar algún framework.  
  
Por ejemplo. Si uso **Drupal** como framework, puedo tener un subdirectorio **drupal** dentro de mi site, e invocar con javascript a algo como **drupal/action.json**, cuyo resultado reflejo en la página.  
  
No hay problema con las páginas del site mientras no cambie el modo de invocar la accion. Si luego cambio la versión de drupal, no seria necesario cambiar las vistas.  
  
Si, en lugar de usar **drupal** como nombre del subdirectorio, hubiera usado algo como **framework**, y colocara dentro acciones que se invocaran del mismo modo, entonces, podría usar cualquier framework, con tal que siguiera el protocolo esperado por las vistas.  
  
Esta forma de trabajar puede permitir funcionar un sitio dinámico que use muchos frameworks diferentes en simultaneo. Uno para el login, otro para los listados, otro para comunicaciones, etc. El que mejor haga lo que queremos. También facilita la actualización de los frameworks a versiones superiores.  
  
Usar javascript para esto me parece un camino relativamente asequible en este momento. Pero si alguien no desea usar javascript para eso, podría usar un framework unobstrusivo (que respete la integridad de las páginas), como **[uphp](http://sourceforge.net/projects/uphp/),** para hacer el trabajo de reemplazo. uphp usa **querypath** para ubicar un elemento en la página (al estilo **jquery**, pero con **php)**, y reemplazarlo por algún resultado; todo eso en el lado del servidor.  
  
En este otro modo, no son las vistas las que invocan las acciones, sino los controladores que se disponen en el framework unobstrusivo (o uframework, para abreviar). El uframework podria invocar a otros frameworks para hacer los reemplazos de los resultados en las ubicaciones pertinentes en la vista. Igual, se podría usar varios frameworks a la vez.  
  
La idea principal es que la vista salga de la jaula del framework, se respete su integridad, tal como es, y sea independiente de los motores que se usen para generar el contenido dinámico.

_*Url archivado: [Liberando la V, otra forma de usar un framework MVC](https://akcdev.blogspot.com/2011/07/liberando-la-v-otra-forma-de-usar-un.html)*_
