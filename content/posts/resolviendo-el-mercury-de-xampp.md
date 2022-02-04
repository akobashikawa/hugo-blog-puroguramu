---
title: 'Resolviendo el Mercury de XAMPP'
date: 2010-01-23T09:41:00.003-05:00
draft: false
url: /2010/01/resolviendo-el-mercury-de-xampp
tags: 
- email
- windows
- programación
- solución
- problema
- mercury
- web
- xampp
- blogger
---

[![](https://4.bp.blogspot.com/_K2xwnQ4Llso/S1CjewJ-MVI/AAAAAAAAAMg/nJ5WtSvKaNo/s320/20-xampp-logo-trio.jpg)](https://4.bp.blogspot.com/_K2xwnQ4Llso/S1CjewJ-MVI/AAAAAAAAAMg/nJ5WtSvKaNo/s1600-h/20-xampp-logo-trio.jpg)

XAMPP es un conveniente paquete que contiene Apache, PHP, MySQL y otros programas para facilitar la instalación y uso de un entorno de desarrollo PHP. Lo vengo usando satisfactoriamente desde hace varios meses. Sin embargo, me enfrasqué en un problema cuando necesité usar el Mercury que trae incluido para enviar emails. Aparentemente no funcionaba. Buscando y navegando mucho por internet, encontré estas páginas que me ayudaron a resolver el problema:  

*   [Configure Mercury mail transport system for external mail sending](http://www.zoe.vc/2008/mercury-mail-transport-system-fur-externe-mail-konfigurieren/) 
*   [New To Mercury, Cant Seem To Send Mail](http://community.pmail.com/forums/thread/20766.aspx)

El primer enlace da una secuencia detallada de pasos. Muchos comentan que les funcionó muy bien, pero yo tuve un problema. Veía que las ventanas de los varios monitores que muestra Mercury decían offline, y un comando "telnet localhost 25" ejecutado en la consola me devolvía "Could not open connection to the host, on port 25".  
Entonces, encontré el segundo enlace, donde un forista comentaba que los mensajes de offline se debían a un bug del módulo MercuryX y se debía deshabilitar. Así lo hice y, al reiniciar, el administrador de Mercury funcionó :-D, se enviaron los mensajes de prueba que tenía atascados e incluso pude hacer una prueba usando el telnet.  
  
Resúmen de pasos  
  

> [![](https://1.bp.blogspot.com/_K2xwnQ4Llso/S1CjoSHduyI/AAAAAAAAAMo/v-kiMviDEMM/s320/mercury-logo.jpg)](https://1.bp.blogspot.com/_K2xwnQ4Llso/S1CjoSHduyI/AAAAAAAAAMo/v-kiMviDEMM/s1600-h/mercury-logo.jpg)La idea del relay es usar un servidor SMTP externo, como el de GMail, para que Mercury envíe el correo a través de él. En teoría sería posible también usar un SMTP en localhost, pero como algunos proveedores no permiten que sus usuarios envíen correo de ese modo, el uso del relay parece más general.

En el archivo xampp/php/php.ini, ubicar las líneas correspondientes a \[mail function\] y editarlas para que quede algo como:  
  
```
\[mail function\]  
; For Win32 only.  
; http://php.net/smtp  
SMTP = localhost  
; http://php.net/smtp-port  
smtp\_port = 25  
  
; For Win32 only.  
; http://php.net/sendmail-from  
sendmail\_from = postmaster@localhost  

```  
A continuación, configurar Mercury. En el administrador de Mercury (que se abre al pulsar su botón Admin en el panel de control de XAMPP), entrar a las opción de menú indicadas por cada título y realizar los cambios que se indican:  
  

**Configuration/Protocol modules...**

  

[![](https://1.bp.blogspot.com/_K2xwnQ4Llso/S1Cc5Rih0dI/AAAAAAAAALo/XnyfNoMDLSk/s320/mercury_conf_03.png)](https://1.bp.blogspot.com/_K2xwnQ4Llso/S1Cc5Rih0dI/AAAAAAAAALo/XnyfNoMDLSk/s1600-h/mercury_conf_03.png)

Note que se han desahabilitado MercuryE y MercuryX, y se ha habilitado Mercury C.  
  
  
Luego de desactivar/activar módulos es necesario reiniciar Mercury (salir del administrador y volver a entrar).

  
  

**Configuration/Mercury core module...**

  

[![](https://3.bp.blogspot.com/_K2xwnQ4Llso/S1CdAEgwaYI/AAAAAAAAALw/yaYmjDYl-UE/s320/mercury_conf_01.png)](https://3.bp.blogspot.com/_K2xwnQ4Llso/S1CdAEgwaYI/AAAAAAAAALw/yaYmjDYl-UE/s1600-h/mercury_conf_01.png)

 [![](https://2.bp.blogspot.com/_K2xwnQ4Llso/S1CdFUOKADI/AAAAAAAAAL4/1ndhK1WXB64/s320/mercury_conf_02.png)](https://2.bp.blogspot.com/_K2xwnQ4Llso/S1CdFUOKADI/AAAAAAAAAL4/1ndhK1WXB64/s1600-h/mercury_conf_02.png)

  

**Configuration/MercuryS SMTP server**

  

[![](https://1.bp.blogspot.com/_K2xwnQ4Llso/S1CdLy5HtzI/AAAAAAAAAMA/IHC1N3Pk5Ro/s320/mercury_conf_04.png)](https://1.bp.blogspot.com/_K2xwnQ4Llso/S1CdLy5HtzI/AAAAAAAAAMA/IHC1N3Pk5Ro/s1600-h/mercury_conf_04.png)

El nombre en "Announce..." puede ser cualquiera. El IP es el del localhost (la página dice que usar el IP de la intranet, 192.168.x.x, no le funcionó).

  

 [![](https://2.bp.blogspot.com/_K2xwnQ4Llso/S1CdavxBiWI/AAAAAAAAAMI/hAScuWTkCiE/s320/mercury_conf_05.png)](https://2.bp.blogspot.com/_K2xwnQ4Llso/S1CdavxBiWI/AAAAAAAAAMI/hAScuWTkCiE/s1600-h/mercury_conf_05.png)

Aquí se modifica la restricción para que se permita conexiones en el rango 127.0.0.1-127.0.0.1

Pero el punto más importante es desmarcar la casilla "Do not permit SMTP relaying of non-local-email"

  

**Configuration/MercuryC SMTP client**

  

[![](https://2.bp.blogspot.com/_K2xwnQ4Llso/S1Cdgj6VPTI/AAAAAAAAAMQ/KYvseGp8-AY/s400/mercury_conf_06.png)](https://2.bp.blogspot.com/_K2xwnQ4Llso/S1Cdgj6VPTI/AAAAAAAAAMQ/KYvseGp8-AY/s1600-h/mercury_conf_06.png)

Aquí indico que se use el SMTP server de gmail, según las recomendaciones de su página y usando el puerto 587 para SSL con STARTTLS. Si es su caso, verifique que el nombre de usuario incluya @gmail.com

  

**Configuration/Manage local users**

  

[![](https://2.bp.blogspot.com/_K2xwnQ4Llso/S1Cdmo1tHfI/AAAAAAAAAMY/ZhLMFfbkZ74/s320/mercury_conf_07.png)](https://2.bp.blogspot.com/_K2xwnQ4Llso/S1Cdmo1tHfI/AAAAAAAAAMY/ZhLMFfbkZ74/s1600-h/mercury_conf_07.png)

Se agrega el usuario postmaster, con privilegio de administrador.

_*Url archivado: [Resolviendo el Mercury de XAMPP](https://akcdev.blogspot.com/2010/01/resolviendo-el-mercury-de-xampp.html)*_

---
### Comentarios archivados:

>
> Probé esta configuración con Windows 7 Home Basic, XAMPP 1.7.1 y funcionaba un rato sí y otras obtenía un mensaje de servicio no disponible. Tanto usando un script PHP como telnet.  
  
Finalmente, estoy usando FreeSMTP en lugar del Mercury Mail y parece que la vida es más simple :)  
Pueden descargarlo de http://www.softstack.com/freesmtp.html
> \
> [Rulo Kobashikawa](https://www.blogger.com/profile/07020497448167262255 "noreply@blogger.com") [2010-04-27 17:31]

>
> Compañero, para serle sincero, soy de esas personas que nunca responden los post de los blogs.  
  
Pero este me ha ayudado como ningun otro.  
  
Solo quiero rescatar algo, y es que, al principio, cuando se desactivan/activan los modulos, se debe REINICIAR el Mercury para que los cambios surtan efecto...  
  
Despues de eso, el manual es PERFECTO amigo, muchas gracias.
> \
> [Unknown](https://www.blogger.com/profile/18197354480414523983 "noreply@blogger.com") [2010-07-25 11:06]

>
> Que bueno que te fue de ayuda, me alegra. Gracias también por la observación, ya la agregué al artículo.
> \
> [Rulo Kobashikawa](https://www.blogger.com/profile/07020497448167262255 "noreply@blogger.com") [2010-07-27 00:08]

>
> Excelente post me ayudo a resolver mi problema que tenia gracias!!!! saludos
> \
> [Unknown](https://www.blogger.com/profile/14610218691619395432 "noreply@blogger.com") [2010-08-03 17:57]

>
> Gracias hermano
> \
> [Anónimo](# "noreply@blogger.com") [2010-08-04 22:32]

>
> Muchísimas gracias!  
Me estaba volviendo loco para que funcione mail(); desde el localhost  
  
Recomendadísimo
> \
> [Anónimo](# "noreply@blogger.com") [2010-08-23 15:32]

>
> esta dos tres
> \
> [Anónimo](# "noreply@blogger.com") [2010-09-22 15:57]

>
> gracias funciono
> \
> [Anónimo](# "noreply@blogger.com") [2010-10-13 09:59]

>
> Gracias hermano, la verdad ya me iba a rendir con Mercury, entre para probar el FreeSMTP, sin embargo, probé por última vez con este tutorial (ya había probado más de 50 yo creo, todos con la misma carrera del php.ini y el firewall), pero este me solucionó todo. El problema eran los modulos que había que desactivar el Mercury E y el X. ¡¡¡GRACIAS!!!
> \
> [Anónimo](# "noreply@blogger.com") [2010-10-30 01:43]

>
> GRACIAS. Lo mismo que los anteriores. Tu sí has acertado. Las 50 cosas que había probado anteriormente, no.
> \
> [Anónimo](# "noreply@blogger.com") [2010-12-27 19:24]

>
> Muchas Gracias, habiado intentado inicialmente con el tutorial  
http://goliatenterrado.es/2009/03/03/configurar-el-mercury32-del-xampp-para-enviar-correos-externos/  
  
Pero no funcionó y lo combine con este aporte y ahora funciona a la perfeccion, muchisimas gracias  
  
Que gran aporte...
> \
> [Anónimo](# "noreply@blogger.com") [2011-01-28 22:31]

>
> gracias hermano me me funcionó a la perfección, pero tengo una duda como uso el Mercury con un dominio propio en vez de gmail por ejemplo
> \
> [David Reyes](https://www.blogger.com/profile/12663275647666124534 "noreply@blogger.com") [2011-02-01 14:49]

>
> Buena pregunta. No he resuelto ese caso aún. Si lo resuelvo, tratare de publicarlo también.
> \
> [Rulo Kobashikawa](https://www.blogger.com/profile/07020497448167262255 "noreply@blogger.com") [2011-02-01 18:14]

>
> excelente! ahora toca resolver lo del dominio propio, como ser los que se sacan gratuitos del tipo dyn-dns.org o no-ip.org  
muchas gracias ;)
> \
> [Guille](http://www.retornandoalinicio.com.ar "noreply@blogger.com") [2011-02-15 11:22]

>
> No puedo leer los mails con el outlook del office, solo con el express. Alguien sabe como solucionar esto por favor?
> \
> [FER](# "noreply@blogger.com") [2011-02-21 15:21]

>
> gracias!! había algo que me fallaba y lo he repasado como explicas y me funciona bien
> \
> [Anónimo](# "noreply@blogger.com") [2011-03-15 13:53]

>
> Hola.  
Me funciono para enviar correos a hotmail y demas usando como puente los datos de gmail.  
  
PERO  
  
cuando uso otro servidor, por ej, uno de JUST HOST falla la identificiacion.  
  
Alguna sugerencia???
> \
> [Smith](http://smith.com "noreply@blogger.com") [2011-05-25 19:55]

>
> Hoy he encontrado que también se puede usar el módulo smtp (SMTP Authentication Support).  
  
Para más información:  
http://drupal.org/project/smtp  
  
http://shutterfreak.net/blogs/olivier-biot/2010-06-24/configuring-smtp-server-sending-mail-drupal
> \
> [Rulo Kobashikawa](https://www.blogger.com/profile/07020497448167262255 "noreply@blogger.com") [2011-06-15 17:02]

>
> Amigo te juro TE AGRADEZCO TU POST... Habia intentado muchas soluciones para enviar correos por localhost, y esta me funciono...  
  
Muchas, muchas gracias...
> \
> [babualbo](# "noreply@blogger.com") [2011-07-07 00:06]

>
> Que bueno que les sea de ayuda. Muchas gracias también por sus comentarios.
> \
> [Rulo Kobashikawa](https://www.blogger.com/profile/07020497448167262255 "noreply@blogger.com") [2011-07-07 12:44]

>
> Genial el tutorial...muchas gracias por la ayuda que nos brindaste!!!
> \
> [Issac Leyva](https://www.blogger.com/profile/01529084957319499853 "noreply@blogger.com") [2011-07-21 13:34]

>
> Muchísimas gracias por la info. Me fue de gran ayuda.
> \
> [Posteandote](http://posteandote.blogspot.com "noreply@blogger.com") [2012-02-07 04:04]

>
> Hice todos los pasos y no me funciono. Tengo 2 correos pendientes y ya me empiezo a frustar. No tengo casi ningun conocimiento en el area informatica y por eso necesito guia.  
  
En Mercury S SMTP server  
Logging  
\- session logging  
  
Este campo me aparece vacio. Supuse que como dice "session logging" busca la carpeta de session, asi que puse ahí mi direccion en C de la carpeta session:  
  
c:\\\\xamp\\mercurymail\\sessions\\mercurys  
  
En Mercury C SMTP server  
  
General  
  
General log file y Session logging directory tambien me aparecen vacios.  
En Log file atine a colocar la carpeta de logs de mercuryc : "c:\\\\....logs\\mercuryc"  
Y en session logging directory lo mismo pern en sesion  
"c:\\\\...sessions\\mercuryc  
  
  
Todos los otros pasos los he seguido, pero aún nada.  
Gracias por la respuesta.
> \
> [Ninguno](https://www.blogger.com/profile/10369438106994578145 "noreply@blogger.com") [2012-02-16 09:30]

>
> Muchas Gracias, funciona perfectamente.  
  
Saludos!!
> \
> [Salvador](http://dynmaster.com "noreply@blogger.com") [2012-02-19 13:59]

>
> Excelente información!!! si se pudieran dar puntos de daria de una escala de 0-10 los 10+2 waaa MUCHAS GRACIAS POR EL APORTE =D ahora a trabajarle cn eso de gmail.. pero el trabajo duro tu ya no los simplificaste
> \
> [KarMaQ](https://www.blogger.com/profile/17226918638415351071 "noreply@blogger.com") [2012-03-17 20:58]

>
> Amigo, funciona a la perfección desde ya mis felicitaciones y muchas gracias por el tutorial
> \
> [Anónimo](# "noreply@blogger.com") [2012-04-02 10:48]

>
> Que tal antes que nada felicidades por el tutorial pero tengo un problema en parte de XAMPP 1.7 estado de los servicios el de SMTP Server esta como desactivado ¿no sabes como podria activarlo?  
  
Gracias
> \
> [Anónimo](# "noreply@blogger.com") [2012-05-24 11:36]

>
> No estoy seguro de entender la pregunta... has probado entrar a Configuration/Protocol modules y activar el módulo SMTP Server?
> \
> [Rulo Kobashikawa](https://www.blogger.com/profile/07020497448167262255 "noreply@blogger.com") [2012-05-24 15:55]

>
> Hola, muchas gracias por tu aporte, es muy bueno...  
  
Yo tengo un problema al enviar un correo electrónico, en Mercury SMTP Client (relay version) me aparece:  
FAILED  
ERROR FF SERVICING QUEUE JOB  
  
Esto se debe cuando envío el correo electrónico y lo pone en cola, pero nunca me manda el correo, no se si me puedes ayuda?  
  
Gracias de ante mano!!!  
Leandro
> \
> [Anónimo](# "noreply@blogger.com") [2012-06-28 16:04]

>
> Hola!  
  
Gracias por el aporte, está muy bueno el tutorial..  
  
Una duda, lo hice tal cual lo tienes y el mail me lo envía perfecto desde el mercury (con Ctrl N) pero cuando quiero enviar con un script de php con la función mail:  
  
  
  
me pone que se envió, pero no llega nada, ni a los no deseados ni nada.. No me marca ningún error, está mal mi script?
> \
> [Anónimo](# "noreply@blogger.com") [2012-10-08 14:39]

>
> Hola, no aparece el código de tu script en tu mensaje...  
Pero diría que, además de verificar el código (y que esté activado mostrar los mensajes de error), verifiques en php.ini el bloque \[mail function\]
> \
> [Rulo Kobashikawa](https://www.blogger.com/profile/07020497448167262255 "noreply@blogger.com") [2012-10-10 12:11]

>
> Me pasa lo mismo encontraste alguna solución?
> \
> [Anónimo](# "noreply@blogger.com") [2013-01-15 23:54]

>
> Pues a mi me va a medias.  
Desde Mercury si puedo enviar correos pero desde el codigo php no puedo hacerlo.  
Alguien me podria ayudar?
> \
> [UnNombre](https://www.blogger.com/profile/05711835973761995346 "noreply@blogger.com") [2013-06-10 04:29]

>
> Hola a mi no me acepta los cambios de activar/desactivar los módulos de Mercury acepto los cambios y reinicio Mercury y los módulos se vuelven a activar como estaban inicialmente haber si me puedes ayudar con esto tengo la versión 4.6 de Mercury.
> \
> [NAYDELIN](https://www.blogger.com/profile/00328698894877959576 "noreply@blogger.com") [2013-07-21 19:21]

>
> Estoy en las mismas.
> \
> [Unknown](https://www.blogger.com/profile/08137952470709971804 "noreply@blogger.com") [2014-04-04 20:39]

>
> ayuda por favor soy novato y tengo este error  
Error: Mercury shutdown unexpectedly.  
10:06:00 p.m. \[mercury\] This may be due to a blocked port, missing dependencies,  
10:06:00 p.m. \[mercury\] improper privileges, a crash, or a shutdown by another method.  
10:06:00 p.m. \[mercury\] Press the Logs button to view error logs and check  
10:06:00 p.m. \[mercury\] the Windows Event Viewer for more clues  
10:06:00 p.m. \[mercury\] If you need more help, copy and post this  
10:06:00 p.m. \[mercury\] entire log window on the forums
> \
> [Anónimo](# "noreply@blogger.com") [2014-07-13 22:09]
