---
title: 'Resolviendo Mac actualizada a Yosemite: Inicio estancado'
date: 2014-11-02T00:00:00.002-05:00
draft: false
url: /2014/11/resolviendo-mac-actualizada-yosemite
tags: 
- apple
- inicio
- solución
- problema
- mac
- blogger
---

[![](http://3.bp.blogspot.com/-WXzWj6EhwHo/VFW6IyR6qvI/AAAAAAAACio/YeyeCnAW3tw/s1600/Mavericks-vs-Yosemite_thumb800.jpg)](http://3.bp.blogspot.com/-WXzWj6EhwHo/VFW6IyR6qvI/AAAAAAAACio/YeyeCnAW3tw/s1600/Mavericks-vs-Yosemite_thumb800.jpg)

De Mavericks a Yosemite
-----------------------

Recientemente actualicé el sistema de la Mac, de _Mavericks_ a _Yosemite_.  
  
Fue un proceso largo. Más largo de lo que esperaba. Lo inicié en el trabajo e incluso reinicié la computadora un par de veces a mitad de un proceso porque parecía que no había progreso. Un amigo fue quien me aclaró que era un proceso largo, que tuviera paciencia.  
  
El proceso terminó varias horas después en mi casa.  

Primeras impresiones
--------------------

Yosemite se ve bien, con su efecto de pavonado transparente. Lo iconos del docker, algo más planos, pero con matices. Es un look que me parece más cercano a Ubuntu  Linux que al _Metro_ de Microsoft. Antes Mac daba la pauta y los demás la imitaban, ahora, como que no necesariamente.  

Problema
--------

Bueno, resulta que un día, la Mac se iba poniendo cada vez más lenta. A pesar de que el monitor de recursos indicara que había memoria. Reinicié y seguí trabajando pero luego de un rato se repitió la situación. Volví a reiniciar y esta vez fue diferente: la barra de progreso que aparece debajo de la manzanita no pasaba de la mitad. Luego de esperar un rato decidí reiniciarla. Hice varios reinicios sin lograr pasar de ese punto.  
  
Investigando en la otra computadora (Windows 7), encontré que los problemas con _Yosemite_ no eran escasos, principalmente para los que habían llegado actualizando desde _Mavericks_.  
  
Encontré que presionando Command+R luego del sonido que indica el inicio del sistema, se entra en modo de recuperación. Allí, hay un juego de utilidades para restaurar un backup, reinstalar el sistema, buscar ayuda, verificar los discos, etc. También hay un terminal.  
  
Primero, opté por verificar el disco. Se hallaron algunas inconsistencias (habrá sido por mis interrupciones en la actualización?) que luego indiqué corregir. Después, reinicié, pero igual seguía estancado el inicio.  

Reinstalando
------------

Volví al modo de recuperación y decidí indicar que reinstalara el sistema. Parecía que la computadora intentaba conectarse a algún lugar y no lo lograba. Insistí, sin resultado. Seguí entonces el consejo de una [página](http://osxdaily.com/2014/10/25/fix-wi-fi-problems-os-x-yosemite/), que tenía que ver con la conexión a red. Entré al terminal y ejecuté el par de comandos:  
  
\# launchctl unload -w /System/Library/LaunchDaemons/com.apple.discoveryd.plist  
\# launchctl load -w /System/Library/LaunchDaemons/com.apple.discoveryd.plist  
  
Luego de eso, indiqué reinstalar el sistema y esta vez si conectó y se realizó el proceso. Demoró toda la noche.  
  
La mañana del día siguiente, entré al renovado Yosemite y me fue bien durante todo el día.  
  
Pero hoy, al retomar la computadora, de pronto parecía que los procesos dejaban de responder, incluso el terminal y el monitor de recursos, como antes de la reinstalación. Reinicié la computadora y llegué otra vez al inicio estancado.  
  
Volví al modo de recuperación, pero esta vez fui al terminal y ejecuté el par de comandos:  
  
\# launchctl unload -w /System/Library/LaunchDaemons/com.apple.discoveryd.plist  
\# launchctl load -w /System/Library/LaunchDaemons/com.apple.discoveryd.plist  
  
Luego, al reiniciar, el inicio se realizó normalmente.  
  
Así que, aparentemente, hay un problema con el manejo de los recursos de red. Si tienes un problema similar, ojalá que estos comandos también te ayuden.  
  
Para más información, esta es la página que encontré:  
  
[http://osxdaily.com/2014/10/25/fix-wi-fi-problems-os-x-yosemite/](http://osxdaily.com/2014/10/25/fix-wi-fi-problems-os-x-yosemite/)

_*Url archivado: [Resolviendo Mac actualizada a Yosemite: Inicio estancado](https://akcdev.blogspot.com/2014/11/resolviendo-mac-actualizada-yosemite.html)*_
