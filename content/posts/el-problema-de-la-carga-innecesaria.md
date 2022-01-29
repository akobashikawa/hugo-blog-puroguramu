---
title: 'El problema de la sobrecarga innecesaria'
date: 2017-08-28T19:16:00.000-05:00
draft: false
url: /2017/08/el-problema-de-la-carga-innecesaria
tags: 
- frontend
- desarrollo
- web
- blogger
---

[![](https://2.bp.blogspot.com/-VDZpVty9PW4/WaSyK8ez88I/AAAAAAAAH5o/2gjdRaBeoUA_GdiLzqjNV41nrlE5S0xAgCLcBGAs/s320/overload.jpg)](https://2.bp.blogspot.com/-VDZpVty9PW4/WaSyK8ez88I/AAAAAAAAH5o/2gjdRaBeoUA_GdiLzqjNV41nrlE5S0xAgCLcBGAs/s1600/overload.jpg)

Problemas reales
----------------

Pienso que resolver problemas es una cuestión de prueba y error.  
  
Que no es como te lo enseñan en la escuela, donde aprendes a copiar soluciones de los libros de texto.  
  
Resolver un problema es como andar a tientas por una habitación a oscuras, tratando de llegar a la puerta.  
  
Lo que te dan los libros de texto son como escenarios prefabricados de juegos con finales conocidos. Llenos de cosas que los maestros han puesto y con rutas de solución que ellos ya conocen.  
  
En los problemas reales, puede haber más de una ruta de solución. O ninguna.  
  
También encontraras montones de cosas que te sirven mezcladas con cosas innecesarias. Y necesitarás aprender a notar cuál es cuál.  
  
Enfrentarte a problemas reales despierta cierto sentido. Aprendes a escuchar al problema. Aprendes a buscar dentro de ti. Aprendes a construir caminos.  

Patrones
--------

Conforme vas resolviendo problemas, te das cuenta que se repiten ciertos patrones para solucionarlos.  
  
Identificar estos patrones ayuda a catalogar las soluciones y facilitar su reutilización.  
  
Por ejemplo:  

*   **_Qué tal si divido el problema en partes_**. Si varias de esas partes me son familiares, podría avanzar por allí.
*   **_Qué tal si solo considero algunos detalles_** (eso se llama abstracción). A lo mejor veo más claro en esa versión simplicada.

Ayuda dividir el trabajo web en partes separadas.  
  
También ayuda quitar de en medio una problemática innecesaria.

MVC
---

Modelo-Vista-Controlador es un patrón de desarrollo web que divide el trabajo en tres areas:

*   Vista: la interfaz de usuario, HTML, CSS, Javascript
*   Modelo: los datos que la Vista mostrará
*   Controlador: el que orquesta las actuaciones de la Vista y el Modelo

Se trata del patrón _Qué tal si divido el problema en partes_. La idea es concentrarse en cierto aspecto del desarrollo para simplificar el trabajo.

Componentes
-----------

El desarrollo de un site o una aplicación web, no es una tarea definida. Es un problema cuyas tareas hay que ir descubriendo en el camino, durante sucesivas iteraciones. No es ir de la A a la Z y ya. Es ir por las letras de un mensaje desconocido, fallando y acertando mientras se va haciendo más claro.

  

Para iterar con agilidad, necesitamos poder hacer cambios con facilidad.

  

¿Ayuda MVC en esto?

  

MVC ayuda a enfocarse en cierto aspecto del problema y a organizar todas las cosas en esas tres grandes areas. Pero esa virtud también tiene su inconveniente. La navegación por el mar de las posibilidades se vuelve muy, muy pesada. Cierto que sabemos donde queda cada cosa y eso es muy bueno. Pero, por otro lado, la implementación de cada idea se vuelve engorrosa.

  

Imaginamos las cosas naturalmente como componentes, pero en MVC cada solución o variante que imaginemos tiene que ser dividida en tres partes antes de poder implementarlas. Es un ejercicio constante de traducción entre lo que imaginas y lo que haces para producirlo.

  

Está bien, pero quizás podría ser mejor.

  

Entran los componentes.

  

¿Qué tal si dividimos las cosas no por areas M, V, C, sino por funcionalidades, por componentes?

  

Es parecido a decir, que tal si en lugar de tener carpetas css, js, images, tenemos varias carpetas home, contact, menu, header, product, etc, cada una representando una funcionalidad o conteniendo otras carpetas de funcionalidades.

Confusiones papistas
--------------------

_Más papista que el Papa_, dice un refrán. En algunos proyectos hay personas que adoptan esta actitud de defender algo como cierto porque sí, porque así es.

  

Gente que toma MVC como una biblia o estresa al equipo que obvia una ceremonia del scrum.

  

Lo importante es honrar el por qué de las cosas. MVC busca claridad. Scrum busca bienestar del equipo.

  

¿Los componenentes podrían hacerlo mejor? ¿Podríamos sentirnos menos estresados? Probemos.

El problema en el Frontend
--------------------------

Este es más o menos el flujo de trabajo que se sigue al desarrollar web:

1.  **Se propone un diseño gráfico base**  
    Algunos insisten en querer tener todo resuelto en este punto, pero es crear falsas expectativas y sufrimiento innecesario.  
    Es importante que el cliente entienda que el desarrollo es iterativo (hablando de eso, también es importante que el equipo de desarrollo lo entienda ^^).
2.  **El diseño gráfico se maqueta con HTML, CSS y Javascript**  
    Los datos son hardcodeados.  
    Algunos insisten en querer maquetar directamente sobre un framework, pero es crear lastre mental innecesario, además de amarrar la maqueta a ese ambiente.
3.  **La maqueta es vuelta template, según el framework que se va a usar**  
    Los datos son mockupeados. Es decir provisto por endpoints que devuelven data hardcodeada.  
    Algunos insisten en hacer endpoints reales de una vez, pero también es crear lastre mental innecesario tratar de enfrentar más de un problema a la vez.
4.  **La aplicación es provista de datos reales**  
    Ya que las anteriores etapas han resuelto una cosa a la vez, se reduce bastante el número de posibilidades de error en este punto.
5.  **El cliente quiere un cambio**  
    Procedemos a iterar.

Aquí es donde se presenta el problema. En la atención de los cambios.  
  
Como las revisiones ya se están haciendo con datos reales, las circunstancias presionan para no ir al paso 1, sino iterar sobre el paso 4.  
  
No se actualiza la propuesta gráfica, ni la maqueta en puro HTML. Se percibe como demasiado engorroso. Se hacen los cambios directamente sobre el template con toda la infraestructura corriendo.  
  
Paradójicamente, eso no es más rápido, ni más seguro.  
  
Para hacer cualquier cambio en el template, con la infraestructura corriendo, tienes todo un ecosistema de base de datos, modelos y controladores funcionando... innecesariamente.  
  
Resolver un cambio en un template es un problema más complicado porque tienes que cargarte mentalmente de todas las convenciones y protocolos del framework, y de todas las circunstancias y problemas que otras areas estén atravesando (que la configuración del entorno ha variado, que _por ahora_ no uses este endpoint sino este otro, que hay un servicio que se ha caído y _debemos esperar_, etc, etc).  
  
En cambio, hacer los cambios sobre la maqueta es un problema aislado, más sencillo y rápido de resolver.  
  
Creo que es mejor resolver los problemas en la maqueta y luego recién llevar esa solución al template.  
  
Si el paso de convertir una maqueta a template no fuera manual sino automático (o si no existiera), creo que sería más sencillo y rápido hacer cambios de UI.

  

[juno-cheerio](https://github.com/akobashikawa/juno-cheerio) y [unophp](https://github.com/akobashikawa/unophp) han sido algunas iniciativas personales para automatizar el paso 3. La idea de unophp se puede adaptar incluso para WordPress.

  

Pero por ahora, tenemos este problema en Frontend: cómo atender con más facilidad los cambios que se requieren durante las iteraciones del proyecto.

Antipatrón
----------

Yo diría que es un antipatrón que el frontend requiera que todo el motor del proyecto, con su base de datos, endpoints, etc, deba estar corriendo para hacer sus cambios.

  

Es complejidad innecesaria para esa tarea.

  

Entiendo que en Integración Contínua se prueban las cosas sobre infraestructuras reales corriendo. Es porque necesitan hacer pruebas en ese nivel. Pero hacer el desarrollo en ese mismo nivel no me parece lo más optimo.  
  
Sería mejor poder aislar esa parte a voluntad, poder crear un entorno donde no exista otra complejidad más allá de lo que quieres resolver, hacer el cambio, y luego, mágicamente, incorporarlo al proyecto completo.

_*Url archivado: [El problema de la sobrecarga innecesaria](https://akcdev.blogspot.com/2017/08/el-problema-de-la-carga-innecesaria.html)*_
