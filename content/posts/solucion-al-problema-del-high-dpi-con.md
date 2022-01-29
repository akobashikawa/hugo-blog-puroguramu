---
title: 'Solución al problema del high DPI con Freeplane en Windows 10'
date: 2017-05-10T13:44:00.003-05:00
draft: false
url: /2017/05/solucion-al-problema-del-high-dpi-con
tags: 
- windows
- blogger
---

En una computadora corriendo **Windows 10** con pantalla con **high DPI** (de **muy alta resolución**, por ejemplo, 4K), algunos programas (como Photoshop CS6, GimpShop, Inkscape y Freeplane), muestran los menús o botones de un tamaño diminuto, casi ilegible.  
  

[![](https://4.bp.blogspot.com/-dUe3BCrQsDQ/WRNeC-tGV9I/AAAAAAAAG9Y/iUZ9a2WZGcAlPYbmQasv26nv7qS-zxkuACLcB/s400/freeplane-hdpi-problem-before.png)](https://4.bp.blogspot.com/-dUe3BCrQsDQ/WRNeC-tGV9I/AAAAAAAAG9Y/iUZ9a2WZGcAlPYbmQasv26nv7qS-zxkuACLcB/s1600/freeplane-hdpi-problem-before.png)

Freeplane es una de las aplicaciones que muestra botones diminutos  
en panallas con high HDPI

  
  
Para **Inkscape **funcionó bien el truco de declarar un .manifest: [http://www.danantonielli.com/adobe-app-scaling-on-high-dpi-displays-fix/](http://www.danantonielli.com/adobe-app-scaling-on-high-dpi-displays-fix/)  
  
Quizás porque **Freeplane **es un programa que corre bajo **Java**, el truco del manifest no funcionaba. Finalmente, pude solucionarlo entrando a las propiedades del ejecutable freeplane.exe: _Compatibility, Override high DPI scalaing behavior. Scaling performing by: **System**_  
  

[![](https://3.bp.blogspot.com/-h0vQb36rwNA/WRNIzYaEdjI/AAAAAAAAG9I/Cgz2YrX7S2II1sCnHN_41hoGNUjvrSqmwCLcB/s640/freeplane-hdpi-properties.png)](https://3.bp.blogspot.com/-h0vQb36rwNA/WRNIzYaEdjI/AAAAAAAAG9I/Cgz2YrX7S2II1sCnHN_41hoGNUjvrSqmwCLcB/s1600/freeplane-hdpi-properties.png)

Propiedades de freeplane.exe

Luego del cambio, los botones aparecen con un tamaño adecuado:  

  

[![](https://2.bp.blogspot.com/-TBY_dihNd5g/WRNerFPiPAI/AAAAAAAAG9g/G_4GJqY2ywkpBDOH1qdB5Gefs6_elyMIwCLcB/s400/freeplane-hdpi-problem-after.png)](https://2.bp.blogspot.com/-TBY_dihNd5g/WRNerFPiPAI/AAAAAAAAG9g/G_4GJqY2ywkpBDOH1qdB5Gefs6_elyMIwCLcB/s1600/freeplane-hdpi-problem-after.png)

Luego de indicar que el escalamiento high DPI será  
manejado por el sistema

  
Sabiendo esto, comprobé con **Inkscape** (sin ningun .manifest) que también funcionaba. Así, este método es una alternativa más simple al de ener que crear el .manifest.

_*Url archivado: [Solución al problema del high DPI con Freeplane en Windows 10](https://akcdev.blogspot.com/2017/05/solucion-al-problema-del-high-dpi-con.html)*_
