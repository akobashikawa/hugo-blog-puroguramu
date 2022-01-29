---
title: 'Un esquema para desarrollo'
date: 2010-04-18T23:21:00.016-05:00
draft: false
url: /2010/04/un-esquema-para-desarrollo
tags: 
- xp
- desarrollo
- esquema
- tdd
- agil
- framework
- blogger
---

### Lo empírico y lo convencional

He observado que, cuando hay una solicitud para hacer un sistema, mucha gente se esmera por seguir lo mejor posible cierto modelo de desarrollo. Pero se suele perder en el bosque, porque caminar con ahinco no garantiza que la dirección sea la correcta.  
  
Cuando algo va mal, casi siempre es posible culpar a la gente. Que no se aplicó el modelo como debía ser. Cómo rebatir eso. Sin embargo, algo hay que hacer. Consideremos que el modelo de desarrollo pueda no ser tan bueno como pensamos. Y probemos.  
  
En la forma empírica, uno empezaba directamente programando, y adaptando el código poco a poco. Se siente bien recibir el feedback de la computadora con cada paso.  
  
Cuando uno estudia, le enseñan que es mejor determinar cuál es el problema y modelar cuál es la solución, antes de empezar a programar.  
  
Si le preguntan a un desarrollador profesional típico, dirá que es mejor la segunda forma, la forma convencional. Yo no estoy completamente de acuerdo. Ni tampoco completamente en desacuerdo.  
  
La forma convencional está bastante influenciada por la necesidad académica de poder evaluar a los estudiantes. Es más fácil hacerlo cuando explicas de antemano qué es lo que pretendes hacer antes de hacerlo. La solución se puede documentar, evaluar, optimizar, etc.  
  
Esto también le es util al mundo. Cuando una empresa solicita un sistema, la forma convencional permite estimar el costo de antemano. Con esta venia, la forma convencional queda santificada en la currícula. Después de algunos años de ser condicionados haciéndolo de ese modo, también acabamos santificándolo nosotros.  
  
Es un poco difícil cambiar las cosas santificadas, pero a veces hay que considerar los hechos.  
  
En el mundo real, la conocida frase _'el cliente no sabe lo que quiere'_ refleja el hecho de que a menudo es muy difícil precisar el problema de antemano. Y, debido a eso, aún cuando el modelado fuera perfecto, nada garantiza que el producto final sea satisfactorio.  
  
La mayoría de proyectos de desarrollo de software fallan. Se exceden en el tiempo, no satisfacen al cliente, o ambas cosas. Si la forma convencional estuviera en lo cierto, eso significaría que la mayoría de la gente no lo aplica bien, y no creo que ese sea el caso.  
  
Pienso que no es culpa del cliente, ni de quien reune sus requerimientos. Sino que la causa es que no tenemos aún un método que permita precisar de antemano problemas que excedan cierta complejidad.  
  
Cuando los problemas son relativamente sencillos, o han sido ampliamente recorridos, puede funcionar la forma convencional, pero no cuando los requerimientos son imprecisos y deban descubrirse sobre la marcha. Lo cual ocurre en prácticamente todos los desarrollos (quizás deberíamos reflexionar en el desfase académico sobre esta cuestión).  

### La prueba que guía

Cuando uno programa, hace pruebas para estar seguro que lo que se acaba de hacer hace lo que se espera. Es relativamente sencillo probar una función o módulo y más complicado probar un caso y aún toda la aplicación. Sin embargo, es necesario, si se quiere minimizar el número de errores que puedan llegar a la versión que probará el usuario.  
  
Las pruebas unitarias permiten usar la computadora para probar una función. Diseñando y agrupando convenientemente las pruebas se pueden probar módulos, casos y hasta la aplicación completa. Esto hace más llevadero el proceso, hasta el punto en que se pueden usar como guía para el desarrollo.  
  
Usar las pruebas como guía para el desarrollo, o Test Driven Development (TDD), es desarrollar primero la prueba que debe pasar el producto, y recién después el producto.  
  
Las pruebas se van implementando según se van determinando los casos de uso.  
  
La primera vez que se corra la prueba, sin ningún producto desarrollado, aparecerá una señal roja. Entonces el desarrollo se convierte en el juego de descubrir el camino más corto, lo mínimo necesario, para que la señal se vuelva verde. Así, el producto reflejará lo que la prueba requiera. La prueba sirve como guía para el desarrollo.  

### Modelar es optimizar

Con TDD, la optimización se posterga todo lo que sea posible, ya que la optimización prematura fácilmente conduce a compromisos y enredos innecesarios.  
  
Cuando un producto pasa las pruebas, se puede refactorizar con seguridad. Es decir, se puede intentar ya sea cambiar el nombre de una función, extraer un fragmento de código para formar una función, reagrupar funciones en nuevas clases, etc. Si todo va bien, las pruebas continuarán mostrando la señal verde. Y si la señal es roja, no hay problema, podemos usar un sistema de control de versiones para deshacer los cambios y volver al último punto donde todo era verde.  
  
Así, es más natural que el modelado vaya apareciendo en este punto. Si el modelado está bien, las pruebas lo dirán. En TDD, la principal guía del modelado es evitar las repeticiones y los acoples de código. Las repeticiones son código que se nota se puede factorizar (una idea similar al del álgebra, que extrae aparte los términos comunes), usando funciones, clases, o herencia. Los acoples ocurren cuando hay una dependencia innecesaria entre dos fragmentos de código. Es mejor cuando cada fragmento de código se pueda reemplazar sin peligro de efectos inesperados en otra parte.  

### Un esquema para desarrollo

En la forma de desarrollo empírica se sentía bien el feedback que daba la computadora en cada paso. TDD tiene algo de eso.  
  
El modelado previo de la solución, aunque quizás correcto académicamente, no funciona demasiado bien en el mundo real. Y tiene, además, el efecto de contenernos las ganas. No soltamos el corcel hasta que tenemos listo el arado. Pero, entonces, ya no es divertido salir a correr si hay que arrastrar un arado al mismo tiempo. Es mejor ir ligeros desde el principio, aceptar los hechos, ser prácticos, y actuar en consecuencia.  
  
Parece que desarrollar un sistema con requerimientos imprecisos es algo que necesariamente debe resolverse sobre la marcha, en un proceso de prueba y ajuste.  
  
El siguiente es un esquema que toma varias ideas de Scrum y otras metodologías:  
  

*   El proceso es de prueba y ajuste. El equipo de desarrollo y el cliente deben estar abiertos al cambio, a  probar, equivocarse y corregir. El ambiente debe aceptar los errores como parte del proceso.
*   El punto de vista del cliente debe estar presente en el desarrollo. Como a menudo es difícil que pueda participar, se designa un intermediario. Puede ser una persona o un conjunto de personas, pero con una sola cabeza para la comunicación y la asignación de responsabilidades.
*   Se elije cuanto tiempo debe durar la etapa. Es más o menos al azar la primera vez. Entre 2 y 4 semanas.
*   Basado en el punto de vista del cliente, se obtiene un conjunto de requerimientos que podría esperarse estuvieran listos en esa etapa. Es más o menos al azar en la primera etapa. Los requerimientos parten de deseos del cliente. Finalmente cada uno se expresa como algo que cierto rol usa para realizar cierta tarea.  
    Cada requerimiento tiene un por qué, que a su vez tiene una justificación, y así sucesivamente. La cadena se puede seguir hasta un conjunto de principios más o menos estables que constituyen la necesidad que justifica el desarrollo.  
    Conforme avance el desarrollo estos principios y la jerarquía de justificaciones se irá haciendo más clara.  
    Luego, habrán requerimientos que no se admitirán porque no encajan en ese orden y, del mismo modo, podrán descubrirse requerimientos que inicialmente no se consideraron pero que son necesarios.
*   Basado en los requerimientos, el equipo hace una lista general de las tareas que estos requerimientos implicaría. Es una lista libre, donde cada uno puede anotar sin censura. Es además una lista abierta, que admitirá nuevos ingresos en cualquier lugar de la etapa. La lista debe ser visible, de libre acceso y fácil de mantener.
*   Antes de procesar la lista, el equipo reunido hace una lectura rápida de todas las tareas, simplemente para informarse de cuales son, y las agrupa en páginas de cierto tamaño. Esto es más o menos arbitrario. Puede ser un número entre 10 y 30 items por página.
*   Para procesar la lista, se hace un repaso tarea por tarea. Cuando uno o más miembros del equipo sienten que pueden atender una tarea, se pone a trabajar en ella durante el tiempo que consideren conveniente.  
    Si la tarea se completa, se tacha de la lista y se continúa el repaso hasta interesarse en alguna tarea. Si la tarea no se completa, se la vuelve a anotar al final de la última página, luego se tacha la anotación original y se continúa el repaso de tareas a partir de esa posición.  
    Al llegar al final de la página, se vuelve al comienzo.  
    Si se hace un repaso y ninguna tarea pendiente parece interesante de atender, todas ellas se resaltan y se coloca una X en una esquina de la página, antes de pasar a la siguiente página.  
    Al llegar al final de todas las páginas, se vuelve a la primera.  
    Puede ser ninguna de las tareas pendientes, que ahora estan resaltadas, sea interesante, porque no son realmente necesarias en ese momento. Si es así, la X se encierra en un círculo, para facilitar saltearse esas páginas la siguiente vez.  
    Las tareas urgentes se anotan al final de la lista y se procesan en dirección inversa, empezando desde el final.  
    [![](http://2.bp.blogspot.com/_K2xwnQ4Llso/S8vY1vfiNPI/AAAAAAAABEc/Z-UJ7qPLZhI/s320/autofocus.png)](http://2.bp.blogspot.com/_K2xwnQ4Llso/S8vY1vfiNPI/AAAAAAAABEc/Z-UJ7qPLZhI/s1600/autofocus.png)
*   La optimización se retrasa todo lo que sea posible. El código optimizado frecuentemente se hace más difícil de entender y reutilizar. Es conveniente que las abstracciones, simplificaciones, y generalizaciones se hagan lo más tarde posible. Y es en la optimización del modelo donde recién entraría a participar el arquitecto. Viendolo bien, un modelado apriori, como en la forma convencional, en realidad _"contamina"_  la lista de requerimientos del cliente con la lista de requerimientos del arquitecto. En cambio, al hacerlo durante la refactorización del código, se hace sobre cosas que realmente se necesitan.
*   Para saber quién atiende cada tarea, y cuál es el estado actual del proceso, se pueden colocar marcadores removibles sobre los items de la lista.
*   Al inicio de cada semana, el responsable del equipo de desarrollo se reune en privado con cada persona para tener una visión de cómo está cada una y qué está haciendo. Hay cosas que se expresan mejor sin la presión del grupo.
*   Al inicio de cada día, el equipo dedida unos minutos en contar a todos que hicieron ayer, que harán hoy, y si tienen alguna dificultad. Hay cosas que es necesario que todos conozcan.
*   Al final de cada etapa se hace una evaluación de ese periodo. Ver qué cosas funcionaron bien y qué cosas podrían mejorarse.
*   En cada nueva etapa, se ajusta la duración del periodo y el tamaño de las páginas de la lista de tareas. También se borran todas X de las páginas con tareas pendientes, para incorporarlas nuevamente al proceso.

### Cómo funciona

La forma de procesar la lista de tareas está basada en el sistema [Autofocus](http://www.markforster.net/autofocus-index/), de Mark Foster.  
  
La idea de dejar que el equipo atienda las tareas que les resultan interesantes es permitir que se desarrolle un inconsciente colectivo que ayude a determinar cuáles son realmente necesarias.  
  
El sistema funciona como un ambiente que sólo deja sobrevivir aquellas tareas realmente necesarias para determinar el sistema. Es decir, el sistema se determina de modo evolutivo. Por eso, se da la libertad de anotar en la lista lo que sea, porque si no vale la pena hacerlo nadie lo hará, y si es necesario, tarde o temprano sucederá.  
  
No es necesario gastar tiempo discutiendo cuales son las tareas, en qué orden hacerlas y quién las atenderá. El sistema facilita que estas cosas se resuelvan espontáneamente.  
  
Ahora, a probar.  
  
_**Enlaces**:_  

*   _[1-2-3 de porqué fallan los proyectos informáticos](http://www.versioncero.com/articulo/197/1-2-3-de-porque-fallan-los-proyectos-informaticos) _
*   _[Autofocus, Get Everything Done (spanish)](http://www.markforster.net/spanish/)_

_*Url archivado: [Un esquema para desarrollo](https://akcdev.blogspot.com/2010/04/un-esquema-para-desarrollo.html)*_
