---
title: 'Publicar un site en Dropbox'
date: 2013-08-16T16:46:00.001-05:00
draft: false
url: /2013/08/publicar-un-site-en-dropbox
tags: 
- windows
- hosting
- dropbox
- web
- blogger
---

[![](http://2.bp.blogspot.com/-Mg-yj48ko3k/Ug6P6B1JXUI/AAAAAAAACKw/ThcrDaI6mvU/s1600/dropbox-hosting.jpg)](http://2.bp.blogspot.com/-Mg-yj48ko3k/Ug6P6B1JXUI/AAAAAAAACKw/ThcrDaI6mvU/s1600/dropbox-hosting.jpg)

  
Dropbox puede servir como **CDN**, para centralizar bibliotecas de imágenes, scripts y otros recursos estáticos (html, css, js) que usemos con frecuencia.

  

Pero también puede servir para alojar un **site estático**.

Método directo
--------------

*   Colocar el site en el directorio **Public**
*   Obtener el vínculo público del archivo **index.html**

*   En **Windows**, click derecho sobre index.html y elegir **Copiar vínculo público**
*   En **[dropbox.com](https://www.dropbox.com/)**, click derecho sobre index.html y elegir **Copiar vínculo público**

*   Usar el vínculo para acceder al site.  
    Por ejemplo: [https://dl.dropboxusercontent.com/u/7009189/helloworld/index.html](https://dl.dropboxusercontent.com/u/7009189/helloworld/index.html)
*   Tener en cuenta los límites de ancho de banda que aplica Dropbox:

*   [https://www.dropbox.com/help/45/es](https://www.dropbox.com/help/45/es) _(20 GB/día para cuentas gratuitas y 200 GB/día para cuentas premium)_
*   [http://lifehacker.com/5704367/what-are-dropboxs-bandwidth-limits](http://lifehacker.com/5704367/what-are-dropboxs-bandwidth-limits) _(aprox soporta máximo 25 000 visitas diarias)_

Con ayuda
---------

También hay servicios (con planes gratuitos disponibles) que facilitan usar dropbox para hosting:

[![](http://2.bp.blogspot.com/-U6oBF77iN3g/Ug6QNIMZW9I/AAAAAAAACK4/A4SCxNmPqNU/s1600/pancake.png)](http://2.bp.blogspot.com/-U6oBF77iN3g/Ug6QNIMZW9I/AAAAAAAACK4/A4SCxNmPqNU/s1600/pancake.png)

*   [http://pancake.io/](http://pancake.io/)

*   El servicio básico es gratuito.
*   Luego de aceptar vincularlo a dropbox, agrega una carpeta **Pancake.io** a la carpeta de aplicaciones del dropbox. Allí dentro se puede colocar el site. 
*   En el site **pancake.io**, se puede cambiar el subdominio numérico asignado por default a otro más amigable.
*   Ejemplo: [http://rulokoba.pancakeapps.com/helloworld/index.html](http://rulokoba.pancakeapps.com/helloworld/index.html)
*   Permite subir archivos de texto en formato wiki **markdown** que renderiza. Ejemplo: [http://rulokoba.pancakeapps.com/helloworld/index.txt](http://rulokoba.pancakeapps.com/helloworld/index.txt)
*   Más información en [http://docs.pancake.io/docs/basics](http://docs.pancake.io/docs/basics)

*   [http://my.droppages.com](http://my.droppages.com/)

*   El servicio gratuito provee hasta 50 MB.
*   Luego de aceptar vincularlo a dropbox, agrega una carpeta **My.DropPages** a la carpeta de aplicaciones de dropbox.
*   En el site **my.droppages.com** se pueden crear sites con subdominios. Por ejemplo, rulokoba.droppages.com hace aparecer la carpeta rulokoba.droppages.com. Aparentemente, se pueden tener varios subdominios.
*   La estructura del site se divide en _Content_, _Public _y _Template_. En _Content_, el contenido de los archivos se escribe en formato wiki **markdown**.
*   Luego de hacer un cambio local, puede ser necesario entrar a my.droppages.com y pulsar el botón **Publish **para que reflejen los cambios.
*   De [http://droppages.com/themes](http://droppages.com/themes) se pueden descargar temas.
*   Ejemplo: [http://rulokoba.droppages.com/](http://rulokoba.droppages.com/)

*   [http://www.kissr.com/](http://www.kissr.com/)

*   El servicio gratuito permite hasta 50 MB
*   Luego de indicar el nombre del subdominio, y de aceptar vinvularlo a dropbox, agrega una carpeta **KISSr** a la carpeta de aplicaciones de dropbox. Dentro van las carpetas de los dominios. Por ejemplo, para rulokoba.kissr.com se crea rulokoba.kissr.com.
*   En el site www.kissr.com se pueden crear más sites con subdominios.
*   Ejemplo: [http://rulokoba.kissr.com](http://rulokoba.kissr.com/)
*   El servicio se apoya además en Amazon Web Services.

Referencias
-----------

*   [http://lifehacker.com/5860139/host-web-pages-for-free-within-dropbox-with-droppages-or-pancakeio](http://lifehacker.com/5860139/host-web-pages-for-free-within-dropbox-with-droppages-or-pancakeio)

_*Url archivado: [Publicar un site en Dropbox](https://akcdev.blogspot.com/2013/08/publicar-un-site-en-dropbox.html)*_
