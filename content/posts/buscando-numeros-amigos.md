---
title: 'Buscando números amigos'
date: 2015-06-29T23:49:00.004-05:00
draft: false
url: /2015/06/buscando-numeros-amigos
tags: 
- matemáticas
- blogger
---

Leyendo _"La fórmula preferida del profesor"_, de Yoko Ogawa, encontré el concepto de **números amigos**. Quizás ya lo había oído antes, hace tiempo. Esta vez, se me ocurrió que podría explorar algunas inquietudes con ayuda de la programación.  
  
Un **número natural** (es decir, entero positivo) siempre se puede dividir sin dejar resto entre sí mismo y entre uno. 12 se puede dividir exactamente entre 12 y entre 1, como cualquier número natural.  
  
Además, la mayoría de números (aparentemente) se puede dividir exactamente entre otros números menores. 12 se puede dividir también entre 2, 3, 4, y 6.  
  
Los **divisores** de un número son todos los números menores entre los que se puede dividir exactamente. Los divisores de 12 serían 1, 2, 3, 4, y 6.  
  
Los números 220 y 284, que aparecen en la novela, son amigos porque la suma de los divisores de uno resulta en el valor del otro:  
  
220: 1 + 2 + 4 + 5 + 10 + 11 + 20 + 22 + 44 + 55 + 110 = 284  
284: 1 + 2 + 4 + 71 + 142 = 220  
  

> Se dice que números amigos son extremadamente infrecuentes. Que matemáticos como Fermat y Descartes solo llegaron a encontrar un par, cada uno.

### Programando

Pruebo crear un programa en javascript que muestre los divisores, la suma de los divisores, y luego haga lo mismo con esa suma, resaltando un OK si es igual al número:

  

See the Pen <a href='http://codepen.io/akobashikawa/pen/VLyEPB/'>Números amigos</a> by Rulo Kobashikawa (<a href='http://codepen.io/akobashikawa'>@akobashikawa</a>) on <a href='http://codepen.io'>CodePen</a>. Se pueden hallar los siguientes pares:  

*   1, 1
*   6, 6
*   28, 28
*   220, 284

Si ampliamos el límite más allá de 300, van apareciendo:

*   496, 496
*   1184, 1210
*   2620, 2924

Los amigos de mis amigos
------------------------

  
Para los números amigos, noto este esquema:  
  
a -(sumDiv)-> b -(sumDiv)-> a  
  
¿Qué tal si flexibilizamos un poco la amistad, y que los amigos de mis amigos puedan ser mis amigos?:  
  
a -(sumDiv)-> b -(sumDiv)-> c -(sumDiv)-> d -(sumDiv)-> e -(sumDiv)-> a  
  
Eso sería un grupo de amigos: a, b, c, d, e  

### Programando

Este programa muestra la serie de suma de divisores del número previo, hasta que se alcance una repetición. Entonces muestra OK.  
  
See the Pen <a href='http://codepen.io/akobashikawa/pen/mJpzvN/'>Números amigos de amigos</a> by Rulo Kobashikawa (<a href='http://codepen.io/akobashikawa'>@akobashikawa</a>) on <a href='http://codepen.io'>CodePen</a>. No conseguí encontrar ningún grupo con más de dos miembros.  
  
Sin embargo, noté que hay números con series largas, que a veces ascienden un poco, antes de converger hacia 1:  
  

*   30: 42  54  66  78  90  144  259  45  33  15  9  4  3  1
*   42: 54  66  78  90  144  259  45  33  15  9  4  3  1
*   54: 66  78  90  144  259  45  33  15  9  4  3  1
*   60: 108  172  136  134  70  74  40  50  43  1
*   66: 78  90  144  259  45  33  15  9  4  3  1
*   102: 114  126  186  198  270  450  759  393  135  105  87  33  15  9  4  3  1
*   114: 126  186  198  270  450  759  393  135  105  87  33  15  9  4  3  1
*   120: 240  504  1056  1968  3240  7650  14112  32571  27333  12161  1
*   126: 186  198  270  450  759  393  135  105  87  33  15  9  4  3  1
*   132: 204  300  568  512  511  81  40  50  43  1
*   174: 186  198  270  450  759  393  135  105  87  33  15  9  4  3  1

  
También aparecieron números con series divergentes:  
  

*   138: 150  222  234  312  528  960  2088  3762  5598  6570  10746  13254  13830  19434  20886  21606  25098  26742  26754  40446...
*   150: 222  234  312  528  960  2088  3762  5598  6570  10746  13254  13830  19434  20886  21606  25098  26742  26754  40446  63234...
*   168: 312  528  960  2088  3762  5598  6570  10746  13254  13830  19434  20886  21606  25098  26742  26754  40446  63234  77406  110754...
*   180: 366  378  582  594  846  1026  1374  1386  2358  2790  4698  6192  11540  12736  12664  11096  11104  10820  11944  10466...
*   210: 366  378  582  594  846  1026  1374  1386  2358  2790  4698  6192  11540  12736  12664  11096  11104  10820  11944  10466...

  
Es como si hubieran ciertos números disparadores: 138, 150, 168, 180, 210, 222, 234, ...  

Preguntas
---------

¿Por qué algunas series divergen?  
¿Habrá alguna aplicación para los números con series de suma de divisores divergentes?

_*Url archivado: [Buscando números amigos](https://akcdev.blogspot.com/2015/06/buscando-numeros-amigos.html)*_
