---
title: 'Solucionando problema vista dinámica en blogger'
date: 2013-10-29T12:07:00.003-05:00
draft: false
url: /2013/10/solucionando-problema-vista-dinamica-en
tags: 
- solución
- problema
- blogger
- blogger
---

[![](https://1.bp.blogspot.com/-KN9y9gdNwMA/TCblvBwx54I/AAAAAAAABIY/UwlET9KGn8I/s200/blogger-logo.jpg)](https://1.bp.blogspot.com/-KN9y9gdNwMA/TCblvBwx54I/AAAAAAAABIY/UwlET9KGn8I/s1600/blogger-logo.jpg)

Puede ser que al usar la plantilla de vista dinámica en blogger, hayas notado que el fondo ya no aparece, o que la mayoría de imágenes no se ha cargado.  
  
Esto se debería a que blogger colocó un script para prevenir que la carga de una página demorara demasiado.  
  
Sin embargo, el tiempo asignado por default es muy poco. Y por eso paginas que antes cargaban bien ahora aparecen con aspecto tristón.  
  
Para solucionarlo, ir al administrador del blog, entrar a Plantilla, Editar HTML y buscar al final del documento u código similar al siguiente:  
  
```
<script language="javascript" type="text/javascript">  
  setTimeout(function() {  
    blogger.ui().configure().view();  
  }, 1000);  
</script>  

```  
Observar que he cambiado el 0 que estaba por 1000 milisegundos (1 segundo).  
  
Guardar la plantilla y ver la mejora en la carga.

_*Url archivado: [Solucionando problema vista dinámica en blogger](https://akcdev.blogspot.com/2013/10/solucionando-problema-vista-dinamica-en.html)*_
