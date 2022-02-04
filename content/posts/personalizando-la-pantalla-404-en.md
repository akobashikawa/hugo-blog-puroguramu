---
title: 'Personalizando la pantalla 404 en Apache'
date: 2010-08-13T15:39:00.001-05:00
draft: false
url: /2010/08/personalizando-la-pantalla-404-en
tags: 
- error
- solución
- problema
- apache
- html
- web
- blogger
---

[![](https://1.bp.blogspot.com/_K2xwnQ4Llso/TGWtYyRGDTI/AAAAAAAABLU/YNdIoSOmytk/s320/custom_404.png)](https://1.bp.blogspot.com/_K2xwnQ4Llso/TGWtYyRGDTI/AAAAAAAABLU/YNdIoSOmytk/s1600/custom_404.png)

Cuando se intenta acceder a una dirección que no se reconoce en el site, el webserver responde con una página de Error 404: Document Not Found.  
  
Es posible personalizar esta página para que sea más informativa o, al menos, más agradable de ver que el mensaje en blanco y negro que viene por default.  
  
En un servidor web Apache , es posible hacerlo modificando la página de error 404 del sistema, o indicando en su archivo de configuración el nombre de otra que preparemos para usar en su lugar.  
  
Sin embargo, hay una opción que me parece mas flexible. Es usar un archivo **.htaccess** en el directorio, indicando cuál será el archivo que se presentara para el error 404.  
  

> Esto requiere que Apache tenga activado el módulo mod\_rewrite y permita el rewrite en ese directorio. Me parece que suele estar configurado de ese modo en la mayoría de hostings.  
>   
> Si se tiene acceso a la configuración de Apache (**/etc/httpd/conf/httpd.conf** en Linux CentOS), debe haber un bloque similar a:  
>   
>   
> <Directory "/var/www/html/mydir">  
>     Options Includes Indexes FollowSymLinks MultiViews  
>     AllowOverride FileInfo  
>     Order allow,deny  
>     Allow from all  
> </Directory&gt  
>   
>   
> Donde mydir es el directorio donde queremos colocar el .htaccess. También puede ser AllowOverride All, que incluye la opción FileInfo.  
>   
> La configuración afecta al directorio y todos sus subdirectorios, a menos que para ellos se indique otra cosa.

  
**.htaccess**  
ErrorDocument 404 /error-docs/HTTP\_NOT\_FOUND.html  
  
Esto indica la página que se presentará cuando ocurra el error 404. La ruta es relativa a la raíz del servidor web, como en un URL. Por ejemplo, la ruta **/error-docs/HTTP\_NOT\_FOUND.html**, puede corresponder al archivo **/var/www/html/error-docs/HTTP\_NOT\_FOUND.html**.  

  
En la página 404.html, ya que puede ser llamada desde cualquier ubicación, los url que se usen deben ser absolutos.  

Páginas de error
----------------

Las principales son:  

**400: Bad request**

Cuando el servidor no entiende la solicitud por un error de sintaxis.

**401: Unauthorized**

Cuando el usuario no ha sido autenticado para acceder.

**403: Forbidden**

El servidor no puede ejecutar la solicitud.

**404: Not Found**

El servidor no puede encontrar la direccion solicitada.

**500: Internal Server Error**

El servidor ha encontrado una situacion inesperada que no le concretar la respuesta.

Esta es una lista más completa que se podría incluir en el .htaccess:  
  
ErrorDocument 400 /error-docs/HTTP\_BAD\_REQUEST.html  
ErrorDocument 401 /error-docs/HTTP\_UNAUTHORIZED.html  
ErrorDocument 403 /error-docs/HTTP\_FORBIDDEN.html  
ErrorDocument 404 /error-docs/HTTP\_NOT\_FOUND.html  
ErrorDocument 405 /error-docs/HTTP\_METHOD\_NOT\_ALLOWED.html  
ErrorDocument 408 /error-docs/HTTP\_REQUEST\_TIME\_OUT.html  
ErrorDocument 410 /error-docs/HTTP\_GONE.html  
ErrorDocument 411 /error-docs/HTTP\_LENGTH\_REQUIRED.html  
ErrorDocument 412 /error-docs/HTTP\_PRECONDITION\_FAILED.html  
ErrorDocument 413 /error-docs/HTTP\_REQUEST\_ENTITY\_TOO\_LARGE.html  
ErrorDocument 414 /error-docs/HTTP\_REQUEST\_URI\_TOO\_LARGE.html  
ErrorDocument 415 /error-docs/HTTP\_UNSUPPORTED\_MEDIA\_TYPE.html  
ErrorDocument 500 /error-docs/HTTP\_INTERNAL\_SERVER\_ERROR.html  
ErrorDocument 501 /error-docs/HTTP\_NOT\_IMPLEMENTED.html  
ErrorDocument 502 /error-docs/HTTP\_BAD\_GATEWAY.html  
ErrorDocument 503 /error-docs/HTTP\_SERVICE\_UNAVAILABLE.html  
ErrorDocument 506 /error-docs/HTTP\_VARIANT\_ALSO\_VARIES.html  

Notas de compatibilidad
-----------------------

Cuando no se define una página de error, el navegador puede presentar su propia versión personalida. Seguramente lo habra notado. Los mensajes de "Página no existe" son diferentes en IE, Firefox, Chrome, etc.  
  
Algo curioso es que Chrome insistira en presentar su propia versión, a menos que la nuestra tenga al menos 512 bytes de tamaño.  
IE7, Firefox 3.6.8 y Safari 5 sí muestran nuestra versión si estuviera disponible.

Referencias
-----------

*   [http://www.codestyle.org/sitemanager/apache/errors-404.shtml](http://www.codestyle.org/sitemanager/apache/errors-404.shtml)
*   [http://www.webreference.com/programming/apache\_errors/](http://www.webreference.com/programming/apache_errors/)
*   [http://www.thesitewizard.com/webdesign/google-chrome.shtml](http://www.thesitewizard.com/webdesign/google-chrome.shtml)

_*Url archivado: [Personalizando la pantalla 404 en Apache](https://akcdev.blogspot.com/2010/08/personalizando-la-pantalla-404-en.html)*_
