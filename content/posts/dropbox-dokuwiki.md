---
title: 'Dropbox + Dokuwiki'
date: 2013-02-27T19:06:00.004-05:00
draft: false
url: /2013/02/dropbox-dokuwiki
tags: 
- idea
- desarrollo
- blogger
---

Dropbox + Dokuwiki
------------------

[![](https://1.bp.blogspot.com/-HzLKuQcM4o8/US6Y83HobSI/AAAAAAAACCI/YdEHTY6mV4o/s1600/dropbox-dokuwiki.jpg)](https://1.bp.blogspot.com/-HzLKuQcM4o8/US6Y83HobSI/AAAAAAAACCI/YdEHTY6mV4o/s1600/dropbox-dokuwiki.jpg)

Se dice que quienes no recuerdan el pasado están condenados a repetirlo. Por eso es bastante útil conocer algo de historia. Por eso también es útil llevar un diario personal o, en la vida profesional, algún tipo de bitácora.

  

Al poco tiempo de haber hecho algo, se tiende a olvidar los detalles. Con el tiempo, se van olvidando más aspectos. Es más fácil y eficiente recordar con ayuda de nuestra bitácora, que volver a realizar la investigación, las pruebas, y el desarrollo.

  

Una bitácora se puede llevar en papel. Pero puede ser mas sencillo realizar búsquedas en un medio digital.

  

Una alternativa podría ser algo como Google Docs. Es como un documento que puede ser tan largo como se quiera. Un problema es que mientras más largo sea el documento, más difícil es de manejarlo, por lo que se tiene de dividir la bitácora en partes más pequeñas, quizás por meses. Pero un problema mayor es que si la conexión de Internet falla, quedamos sin acceso a ella, en particular a nuestras notas sobre qué hacer cuando hay problemas de red (-\_-)'

  

Otra alternativa es usar un wiki, que permite que la información crezca de manera más orgánica. Hay muchas ofertas. Las que son online, tendrían también el problema del difícil acceso cuando falla la conexión a Internet.

  

Entonces quedan las que son para instalar uno mismo, en el localhost. Luego, está el problema de tener el mismo contenido de computadora en computadora si, por ejemplo, usamos a veces la del trabajo, otras veces la de la casa, y otras una portátil. Hacer esa sincronización se vuelve tediosa si involucra base de datos; es mucho más sencillo copiar y pegar archivos que exportar e importar tablas. Así, es más fácil usar un wiki como dokuwiki, cuyo contenido se almacena en archivos de texto simple, que mediawiki, que almacena en base de datos.

  

Finalmente, la sincronización se puede automatizar usando dropbox. Lo que suelo hacer es crear dentro del directorio web un enlace simbólico a un subdirectorio de mi carpeta dropbox. Por ejemplo, htdocs/dropbox/ apuntando hacia Dropbox/htdocs/. Si instalo dokuwiki en dropbox/dokuwiki, aparecerá en todas las computadoras donde tenga dropbox (además del acceso online), y se mantendra sincronizado automáticamente. Genial!

  

Confieso que este razonamiento no llegó a mi en el mismo orden en que lo estoy contando. Durante mucho tiempo usé un wiki en un hosting, haciendo backups locales. Luego usé unos años Google Docs, desechando muchas veces la idea de volver a los wikis porque quería ahorrarme el costo de mantener un hosting (y un hosting gratuito suele tener la presión de ingresar cada mes para que la cuenta se mantenga viva). Un día, me animé a instalar dokuwiki en mi dropbox de desarrollo y... eureka, me dí cuenta que era una buena idea (^\_^).

  

Ojalá le sirva de ayuda a alguien más también.

_*Url archivado: [Dropbox + Dokuwiki](https://akcdev.blogspot.com/2013/02/dropbox-dokuwiki.html)*_
