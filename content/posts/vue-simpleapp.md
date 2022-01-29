---
title: 'Vue Simple App: Sin webpack'
date: 2019-09-29T02:15:00.002-05:00
draft: false
url: /2019/09/vue-simpleapp
tags: 
- vuex
- vuetify
- javascript
- vue
- router
- blogger
---

_Vue, Router, Vuex y Vuetify, pero sin webpack_

  

[![](https://1.bp.blogspot.com/-O5CHmMzmBPQ/XZBac_jKhAI/AAAAAAAAb3Y/42U51CB6iww139a50xNT5hIwR5VVhWiCQCLcBGAsYHQ/s320/vuejs.png)](https://1.bp.blogspot.com/-O5CHmMzmBPQ/XZBac_jKhAI/AAAAAAAAb3Y/42U51CB6iww139a50xNT5hIwR5VVhWiCQCLcBGAsYHQ/s1600/vuejs.png)

_\[Actualizado el 2019/11/05: "Carga dinámica"\]_  
  
Tal vez no tenga ninguna razón técnica importante para preferir prescindir de **webpack** al desarrollar una aplicación web.  
  
Tal vez sea solamente nostalgia por los viejos tiempos, donde simplemente importabas librerías en la página y la magia podía aparecer.  
  
Tal vez no sea mala idea tener esa capa extra que cargar en el viaje, y aceptarla a cambio de los caramelos que nos regala.  
  
Pero a mi me molesta un poco.  
  
Preferiría no tener que usarla si puedo evitarlo.  
  
Siento que hay que tener cuidado cuando algo aumenta la complejidad. Mayor velocidad o comodidad pueden ser justificaciones. Pero hay que estar atentos a no limitar la diversidad de opciones.  
Una de las cosas que me gusta de **Vue** es que puedo empezar muy simple, importando la librería en la página. Y luego, si el problema lo amerita, ir escalando la solución hacia algo más y más complejo. Es como empezar descalzo si quiero, o con sandalias, e ir cambiando según lo amerite el terreno.  
  
La mayoría de tutoriales parece estar de acuerdo en que usar **_vue create_** es la opción más práctica. Sin embargo, algo que descubrí es que también se puede llegar a elaborar soluciones relativamente complejas sin usar un transpilador.  
  
Esta es una guía en un proceso de desarrollo simple que nos permita usar **Vue**, **Router**, **Vuex** y **Vuetify**, sin necesitar la complejidad extra de webpack.  

HTML5
-----

Un lugar simple donde empezar.  
  
HTML5: [https://codepen.io/akobashikawa/pen/NWKVazJ](https://codepen.io/akobashikawa/pen/NWKVazJ)  

HTML5 + Vue
-----------

Importar vue y desarrollar un script en la misma página.  
  
HTML5 + Vue: [https://codepen.io/akobashikawa/pen/aborLgW](https://codepen.io/akobashikawa/pen/aborLgW)  

HTML5 + Vue + Router
--------------------

Importar Vue Router para organizar la navegación.  
  
Eso también nos empuja a organizar el contenido en componentes, si es que no lo hemos hecho ya.  
HTML5 + Vue + Router: [https://codepen.io/akobashikawa/pen/qBWGVEp](https://codepen.io/akobashikawa/pen/qBWGVEp)  

HTML5 + Vue + Router + Vuex
---------------------------

Importar Vuex para compartir un estado general entre los componentes.  
HTML5 + Vue + Router + Vuex: [https://codepen.io/akobashikawa/pen/pozmdby](https://codepen.io/akobashikawa/pen/pozmdby)  

HTML5 + Vue + Router + Vuex + Vuetify
-------------------------------------

Para darle un look de app con Material Design.

  

HTML5 + Vue + Router + Vuex + Vuetify: [https://codepen.io/akobashikawa/pen/bGbyYod](https://codepen.io/akobashikawa/pen/bGbyYod)  

Módulos
-------

Cuando más componentes van apareciendo y el largo del archivo va haciendo complicada la edición, parece una señal para sacar el código javascript a otro archivo.

  

Javascript soporta _import_. Pero hay que usarla dentro de un _**módulo**_.

  

[https://github.com/akobashikawa/vue-simple-app](https://github.com/akobashikawa/vue-simple-app)  
  

Carga dinámica
--------------

Algo que ocurre con los módulos declarados normalmente, es que se carga toda la estructura de dependencias desde el inicio.

  

Para prevenirlo, y que cada módulo se pueda cargar cuando se necesita y no antes, se puede usar la técnica de declarar el componente como resultado de una función:

  

Antes:  
```
`import Counter from './Counter.js';`  

```Después:  
```
const Counter = () => import('./Counter.js');
```

  

Conclusión
----------

Es posible desarrollar vue apps de relativa complejidad sin necesidad de usar webpack.

  

Me parece que este esquema puede simplificar el inicio de un proyecto. Aún cuando la versión para producción pueda requerir webpack para las optimizaciones, se podría usar esto durante el desarrollo.

  

¿Qué ventajas o desventajas ves hacerlo de este modo?, ¿te parece que puede facilitar la depuración?, ¿crees que en el futuro los navegadores carguen los scripts de un modo que no sea necesario empaquetarlos como actualmente?

_*Url archivado: [Vue Simple App: Sin webpack](https://akcdev.blogspot.com/2019/09/vue-simpleapp.html)*_
