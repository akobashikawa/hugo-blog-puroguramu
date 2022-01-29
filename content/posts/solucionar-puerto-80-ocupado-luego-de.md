---
title: 'Solucionar puerto 80 ocupado luego de Webmatrix'
date: 2011-10-04T16:12:00.002-05:00
draft: false
url: /2011/10/solucionar-puerto-80-ocupado-luego-de
tags: 
- windows
- solución
- problema
- web
- xampp
- blogger
---

[![](http://1.bp.blogspot.com/-YoQvafbtfsc/TJRBQ9wcVvI/AAAAAAAABNU/OgvJYz_5BEs/s200/windows7_01.jpg)](http://1.bp.blogspot.com/-YoQvafbtfsc/TJRBQ9wcVvI/AAAAAAAABNU/OgvJYz_5BEs/s1600/windows7_01.jpg)

Resolver esto me ha tomado un tiempo. Espero le resulte de ayuda a alguien.  
  
Luego lo desinstalar Webmatrix (La versión 1.0 me parece, en Windows 7), encontré que XAMPP no podía usar el puerto 80 como antes.  
  
Con la idea de averiguar qué proceso lo ocupa, ejecuto en la consola de comandos, como administrador:  
  
```
netstat -anb
```  
pero aparece que no hay información disponible sobre el proceso que ocupa el puerto 80.  
  
Usando la utilidad tcpview (de Sysinternals), veo que el proceso es el mismo System, con PID 4.  
  
Hago telnet localhost 80 y veo que quién está atendiendo es **Microsoft-HTTPAPI/2.0**  
  
Reviso en el Panel de Control, Herramientas Administrativas, Servicios, y desactivo **"Servicio Agente remoto para Microsoft Web Deploy 2.0."**  
  
Eso era. Al parecer un issue de Webmatrix. Ahora XAMPP ya puede iniciar en el puerto 80.  
  
Referencias  

*   [Port 80 is being used by SYSTEM (PID 4), what is that?](http://stackoverflow.com/questions/1430141/port-80-is-being-used-by-system-pid-4-what-is-that)

_*Url archivado: [Solucionar puerto 80 ocupado luego de Webmatrix](https://akcdev.blogspot.com/2011/10/solucionar-puerto-80-ocupado-luego-de.html)*_

---
### Comentarios archivados:

>
> Me ha servido de mucha ayuda, instale Web Matrix y no me dejaba entrar a localhost con Apache...  
  
Muchas Gracias :)
> \
> [Unknown](https://www.blogger.com/profile/15416698486836819516 "noreply@blogger.com") [2012-01-28 13:07]

>
> Qué bueno. Buena suerte!
> \
> [Rulo Kobashikawa](https://www.blogger.com/profile/07020497448167262255 "noreply@blogger.com") [2012-01-28 18:58]

>
> muchas gracias me sirvio, lo que pasa es que normalmente uso XAMPP para un servidor apache y por razones de practica tuve que instalar iss y dejo de responder mi servidor apache a pesar de que a iss le asigne otro puerto, muchas gracias otra vez.
> \
> [Anónimo](# "noreply@blogger.com") [2012-02-20 22:08]

>
> Gracias a mi también me sirvió :)
> \
> [Anónimo](# "noreply@blogger.com") [2012-04-16 18:21]

>
> graciasssss, me salvaste!!!!
> \
> [Anónimo](# "noreply@blogger.com") [2012-04-29 15:01]

>
> Muchas gracias, esto estaba buscando, Instalé WebMatrix para probar ciertas cosas, y no pude seguir entrando al servidor Apache. Gran aporte. Muchas gracias de nuevo.
> \
> [Dafz Pacheco](https://www.blogger.com/profile/06245392773446786826 "noreply@blogger.com") [2012-06-05 11:19]

>
> Sí, es un problema ese efecto del WebMatrix.
> \
> [Rulo Kobashikawa](https://www.blogger.com/profile/07020497448167262255 "noreply@blogger.com") [2012-06-05 12:48]

>
> it works!!
> \
> [davidh](# "noreply@blogger.com") [2012-06-12 21:08]

>
> like Apache :)
> \
> [Rulo Kobashikawa](https://www.blogger.com/profile/07020497448167262255 "noreply@blogger.com") [2012-06-13 10:15]

>
> haha gracias, ahora mas que nunca volví a odiar a microsoft XD
> \
> [Anónimo](# "noreply@blogger.com") [2012-07-16 16:41]

>
> PORFINNNN ALGUIEN QUE DIGA COMO ES LA VUELTA.... EXCELENTE TE DOY 5 PUNTOS
> \
> [Anónimo](# "noreply@blogger.com") [2013-03-03 23:03]

>
> Ok,pero solo funciona Apache,mas no MySQL :s se queda asi : "Attempting to start MySQL service..."
> \
> [Unknown](https://www.blogger.com/profile/04158484638400538540 "noreply@blogger.com") [2013-09-05 11:25]

>
> Muchas gracias, después de mirar en 50 páginas o más, por fin me has dado la solución.  
No tengo Webmatrix ni se lo que es, solo intenté instalar Ruby on rails, me petó y a partir de ahí el apache me daba el siguiente error:  
  
Port 80 in use by ""C:\\Archivos de programa\\IIS\\Microsoft Web Deploy\\MsDepSvc.exe"  
  
Gracias, por el aporte!
> \
> [Anónimo](# "noreply@blogger.com") [2014-04-05 05:58]

>
> Me alegra. Que bueno que también fue de ayuda para ese caso. Gracias también por compartirlo.
> \
> [Rulo Kobashikawa](https://www.blogger.com/profile/07020497448167262255 "noreply@blogger.com") [2014-04-05 12:17]

>
> Muchas Gracias, bastante útil, estuve en una batalla hasta que encontré tu blog
> \
> [Anónimo](# "noreply@blogger.com") [2014-05-13 10:12]

>
> En algunos casos este servicio no aparece en la lista, si es el caso de alguien, ejecutar CMD e ingresar estos comandos  
sc stop "MsDepSvc"  
sc config "MsDepSvc" start= disabled  
Espero k le sirva a alguien. Saludos. David
> \
> [Anónimo](# "noreply@blogger.com") [2015-01-26 02:39]

>
> Muchas gracias instale Webmatrix por que me parecieron interesantes algunas funciones, pero no me dejaba trabajar con wamp.
> \
> [Unknown](https://www.blogger.com/profile/00095848801327845302 "noreply@blogger.com") [2015-07-23 15:06]
