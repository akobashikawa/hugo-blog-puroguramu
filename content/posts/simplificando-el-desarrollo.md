---
title: 'Simplificando el desarrollo'
date: 2017-05-30T00:31:00.000-05:00
draft: false
url: /2017/05/simplificando-el-desarrollo
tags: 
- blogger
---

Webpack, Babel, TypeScript, Gulp, Sass, Stylus, Pug, son algunas de las cosas que se ven en el desarrollo frontend hoy en día.  
  
Pug (Jade) permite escribir una especie de html sin brackets, que se ve más limpio y legible, y luego es traducido a **html**.  
  
Sass y Stylus hacen algo parecido con el **css**.  
  
CoffeeScript lo hacía con el **javascript**. Pero parece que va cayendo en deshuso, frente a TypeScript y ES6.  
  
Pug te permite escribir html de manera más clara y sencilla y está bien.  
  
Styles te permite escribir css de manera más clara y sencilla y está bien.  
  
CofeeScript te permite escribir javascript de manera más clara y sencilla y también está bien.  
  
Está bien que produzcas html, css o javascript de la manera que te resulte más cómoda y fácil de mantener.  
  
Sospecho que muchos programadores provenientes de otras canteras, resintieron tanto las incomodidades de los brackets, y puntos y comas, que usaron sus potentes habilidades para construir herramientas que les recordaran sus lenguajes preferidos.  
  
Además, herramientas como Gulp, Babel y Webpack pueden automatizar el proceso de traducción.  
  
Pero entonces comenzó a complicarse la cosa.  
  
Si miramos las cosas desde una perspectiva más amplia, lo que ha sucedido es que se ha creado una capa adicional entre el programador y el código. Una capa de pre procesado.  
  
¿Qué pasa cualdo alguien más quiere participar en el desarrollo de un proyecto como este? Esta persona conoce todo lo necesario para actuar en la capa del código html/css/javascript.  
  
\-- Pero no, un momento, no puedes hacer eso.  
  
\-- ¿Por qué no?  
  
\-- Porque yo escribo en mi hermoso pug/stylus/coffeescript para producir ese horrible html/css/javascript y no se me ocurre cómo hacerlo en sentido inverso para que tus cambios actualicen los míos.  
  
\-- Bueno, me voy a ayudar a otro proyecto.  
  
¿Y para qué publicas un proyecto en GitHub, como open source, y en inglés, si no es para facilitar que otras personas puedan colaborar contigo para evolucionar una idea que te apasiona?  
  
Entonces, no tiene mucho sentido restringir esa facilidad con herramientas que no todo el mundo quiere usar, aunque tú las adores.  
  
Lo que debería haber en tu proyecto compartido es cosas que sean fáciles de compartir: html, css y javascript. Producidos con las herramientas que gustes; pug, sublime, atom, notepad o dreamweaver. Pero, así como no puedes exigir que alguien use dreamweaver, sublime o atom para poder participar en tu proyecto open source, tampoco deberías exigir que usen tal o cual pre procesador.  
  
**El efecto de encarecer las cosas**  
  
Imagina que tienes una cita con una chica que te gusta. Por alguna razón, lo comentas en casa, a tu abuela. Ella se opone, por varias razones importantes:  
  
\-- No sabe cocinar; ¿cómo te va a atender después?  
  
\-- Pero, abue...  
  
\-- Además es demasiado flaca; con esas caderas sufrirá mucho para tener hijos  
  
\-- ¡Es sólo una cita, abuela!  
  
Si sales con alguien pensando en si se casarán, ves todo con otros ojos. Hasta los defectos más pequeños se convierten en gigantes cuando los proyectas sobre la pantalla de un futuro de deberás soportar todos los días.  
  
La abuela piensa así porque en su época, donde vivía, una cita era algo muy importante y costosa, pagada con el dinero que la familia ahorraba con esfuerzo, así que no podías estar en plan de "salir para ir conociéndonos".  
  
  
Algo así aparece en el proceso de desarrollo cuando un proceso es caro de hacer.  
  
Antes, con un simple editor de texto y el navegador, podías moverte rápidamente entre el html y los resultados, probando diversas librerías, plugins, etc, con mucha agilidad. Como ir en bicicleta.  
  
Ahora, es un camión. Si quieres probar y jugar con una librería, un plugin, etc. ya no puedes hacerlo directamente, como antes. Debes traducir mentalmente el html de la documentación del plugin, y calcular tu código para que produzca el html que se requiere. Son dos lenguajes en la cabeza y un paso extra para depurar. Es como caminar con ayuda de un espejo.  
  
Así que ya no tienes citas por diversión. Todo se vuelve más serio.  
  
Cómo el builder establece de antemano dónde irá cada cosa hasta el fin de los tiempos, con ese mal ejemplo la gente empieza a sentirse presionada a hacer el código limpio directamente. De pronto, la elaboración progresiva de soluciones, la refactorización y la restructuración de directorios quedan al margen de la ley, porque son más caros.  
  
Además, la gente empieza a usar Gulp y Webpack como herramientas con las que pueden instaurar un régimen de código opinionado ("así es cómo se deben hacer las cosas, tontos").  
  
Y todo empezó con el afán de trabajar más cómodos. De buenas intenciones está hecho el camino al infierno... como reza el dicho.  
  
  
Creo que es importante mantener un punto de vista amplio acerca de las cosas que hacemos en desarrollo. Del mismo modo que un máximo en cada división de una empresa no garantiza un máximo de la empresa en conjunto, una mejora en un aspecto individual no garantiza que todo el proceso de desarrollo será mejor. Los máximos locales no garantizan máximos globales. Producir html rápidamente no garantiza que mantenerlo será igual de rápido. Es mejor un enfoque holístico.  
  
Creo que una buena referencia para tomar decisiones es considerar el número de pasos, capas y herramientas que significa corregir un bug, o introducir un cambio. Un problema se puede resolver de muchas maneras. Es posible usar un cañón para matar moscas. Pero es una buena idea empezar con las soluciones más simples primero.  
  
Y, construir las cosas de modo que no obstruya los siguientes pasos. Evitar los compromisos innecesarios y mantener el camino libre y fresco para avanzar progresivamente. Ya que el viaje es el camino.  
  

_Transcrito de [http://rulokoba.blogspot.pe/2017/05/simplificando-el-desarrollo.html](http://rulokoba.blogspot.pe/2017/05/simplificando-el-desarrollo.html)_

_*Url archivado: [Simplificando el desarrollo](https://akcdev.blogspot.com/2017/05/simplificando-el-desarrollo.html)*_
