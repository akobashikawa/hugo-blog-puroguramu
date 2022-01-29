---
title: 'La falacia de "hacerlo sin frameworks"'
date: 2017-01-13T17:22:00.001-05:00
draft: false
url: /2017/01/la-falacia-de-hacerlo-sin-frameworks
tags: 
- framework
- blogger
---

[![](https://4.bp.blogspot.com/-AyvtiiOQnek/WC_fzkbd53I/AAAAAAAAFk8/sfUNmIqkAlcGXRHUGkflgjaX-s6Q148kwCPcB/s320/wheel_evolution.jpg)](https://4.bp.blogspot.com/-AyvtiiOQnek/WC_fzkbd53I/AAAAAAAAFk8/sfUNmIqkAlcGXRHUGkflgjaX-s6Q148kwCPcB/s1600/wheel_evolution.jpg)

Hay una idea difundida entre muchos desarrolladores acerca de que es mejor no usar un framework en lo posible.  
  
El Framework F tiene las deventajas a, b y c; por lo tanto, si no lo usan, evitarán esas desventajas, concluyen.  
  
Veamos por qué esto es una falacia (un razonamiento errado que parece correcto). Las falacias son peligrosas porque parecen correctas.  
  
  
Un framework es, en esencia, un conjunto de convenciones sobre cómo usar un conjunto de librerías.  
  
Cuando usas un framework, vas notando cómo sus convenciones condicionan el modo en que abordas las tareas y resuelves los problemas. Poco a poco, empiezas a visualizar las soluciones en términos del framework.  
  
Esa pauta que establece el framework puede ser de gran ayuda para mantener orden y estabilidad en un proyecto. Y también para darle continuidad.  
  
Pero también puede ser que las convenciones sean demasiado reguladoras, restrictivas o limitantes. O que haya problemas que sean de solución muy dificil o imposible en términos del framework.  
  
Entonces tenemos:  
  

Framework F

Pros

Contras

m

a

n

b

p

c

  
  
Para analizar qué framework elegir, sería:  
  

Framework F

Framework G

Framework H

Pros

m

sí

sí

sí

n

sí

sí

p

sí

sí

Contras

a

no

no

b

no

no

c

no

no

  
Así que si esos frameworks tienen esas desventajas, no los usemos y así las evitaremos.  
  
  
Suena lógico. Sin embargo, es un error.  
  
  
Lo que realmente están proponiendo es esto:  
  

Framework F

Framework G

Framework H

Framework X

Pros

m

sí

sí

sí

?

n

sí

sí

?

p

sí

sí

?

Contras

a

no

no

?

b

no

no

?

c

no

no

?

  
¿Qué es el Framework X?  
  
Es el framework (propio aunque negado) que se irá definiendo (sobre la marcha).  
  
Las preferencias de uso, las posibilidades y limitaciones, y el contexto de trabajo del equipo de desarrollo, determinarán un conjunto de librerías y cómo se deben usar.  
  
Es decir, un framework.  
  
  
Por eso, lo que realmente están proponiendo los desarrolladores que "evitan frameworks" es:  
  
"No uses un framework conocido (con todas sus ventajas, horas de prueba, comunidad y documentación) y usa mi framework (que aún no existe pero va a ser mejor que todos ellos)"  
  
  
Si aceptas esa propuesta, automáticamente estás asumiendo un proyecto extra que deberá correr en paralelo al que quieres realizar. Porque hacer un buen framework consumirá tiempo y recursos en codificación, documentación y capacitación.

  

No es que te estés ahorrando el costo de usar un framework; estás asumiendo el costo de hacer uno.  
  
"No hemos usado ningún framework, así que no tienes que aprender nada nuevo para empezar".  
  
No es verdad. Verás que tendrás que familiarizarte con el conjunto de funciones y librerías que están usando, la forma en que las llaman y la particular (o peculiar) manera como el proyecto se ha organizado (o ha resultado ser).

  

Si usas un framework conocido, puedes tener más apoyo de la comunidad, documentación, casos de ejemplo, etc. Habrán más personas que ya lo conocen y están disponibles para colaborar contigo.

  

Es cuestión también de saber ver el vaso medio lleno y valorar las virtudes del modelo open source.  
  

### El efecto Dunning-Kruger

Es un efecto psicológico que se observa en todas las personas, de pensar que son más competentes en aquellas cosas en que realmente tienen más limitaciones:  
  
[Why Do Incompetent People Think They're So Great?](https://curiosity.com/topics/why-do-incompetent-people-think-theyre-so-great-curiosity/)  
  
  
¿Estamos siendo afectados por el efecto Dunning-Kruger?  
  

### Usando las buenas partes

Creo que es importante ser claro en lo que se hace, y tratar de mostrar claramente lo que sucede cuando nos damos cuenta que está sucediendo.  
  
Porque solamente podemos construir castillos de verdad usando ladrillos de verdad.  
  
Reinventar la rueda es muy util para desarrollar las habilidades de invención.  
  
Poder hacer un propio framework que sea comparable con los frameworks conocidos es algo admirable.  
  
Pero no es el mejor camino minimizar lo que esos frameworks conocidos son para que así la tarea de competir con ellos resulte más fácil o nuestro trabajo parezca más meritorio.  
  
  
Siempre es posible encontrar algo desfavorable en un framework, algo que no puede hacer tan bien y que quizás nosotros podamos hacer mejor (en un contexto más simple, aisladamente).  
  
Me parece más interesante juzgar los frameworks en función de las cosas favorables. De lo que nos permiten hacer. De los problemas que nos pueden ayudar a resolver.  
  
Porque tampoco podemos construir castillos con ladrillos que no tenemos. Hay que usar lo que sí tenemos.  
  
  
Hay una cita de Addy Osmani como recomendación acerca de los frameworks:  
  
“First do it, then do it right, then do it better.”  
  
Primero usa lo que hay, conócelo realmente. Si encuentras algo que mejorar, corrígelo. Luego intenta hacerlo mejor.

_*Url archivado: [La falacia de "hacerlo sin frameworks"](https://akcdev.blogspot.com/2017/01/la-falacia-de-hacerlo-sin-frameworks.html)*_
