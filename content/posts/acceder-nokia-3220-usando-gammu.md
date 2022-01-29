---
title: 'Acceder a Nokia 3220 usando Gammu'
date: 2011-06-11T22:57:00.002-05:00
draft: false
url: /2011/06/acceder-nokia-3220-usando-gammu
tags: 
- mobile
- linux
- blogger
---

[![](http://1.bp.blogspot.com/-CkYp1y9wqIc/TfQ5MBfR_II/AAAAAAAABWU/wtcG_7xm2rA/s200/nokia-3220b.jpg)](http://1.bp.blogspot.com/-CkYp1y9wqIc/TfQ5MBfR_II/AAAAAAAABWU/wtcG_7xm2rA/s1600/nokia-3220b.jpg)

El Nokia 3220 es un teléfono celular que vengo usando varios años. Ahora, quizás se puede considerar un modelo antiguo, pero puede tomar fotos de 640x480 px que se ven bien.  
  
Para descargar las fotos, uso un cable tipo DKU5 que va del puerto serial del teléfono a un puerto USB de la computadora.  
  
En el lado de la computadora, con Windows, se puede usar el Nokia PC Suite. Me ha funcionado bien con Windows XP. Con Windows 7 parecía no conectar bien, así que lo que hice fue correr Windows XP en un vmware para correr allí el Nokia PC Suite.  
  
Muchas veces he tenido problemas para lograr la conexión. El teléfono suele decir 'Data enhancement not support', aún cuando finalmente la conexión se logre.  
  
Ahora que estoy usando Ubuntu Linux (Natty Narwhal), encontré que se puede usar Gammu/Wammu para acceder al celular.  
  
Instalé Wammu y lo probé. Tiene un wizard que permite identificar el celular conectado. Se logra hacer la conexión, pero no logré encontrar en la interfaz del programa el modo de descargar las fotos.  
  
Entonces encontré el artículo [COMO: Archivos de Nokia 3220 ( u otro ) a Ubuntu](https://lists.ubuntu.com/archives/ubuntu-es/2006-June/016657.html) que me mostró el camino por la consola de comandos.  
  
Primero instale Gammu (yo pensaba que Wammu lo había instalado pero no era así):  
  
```
sudo apt-get install gammu  

```  
Luego, verifico que en ~/.gammurc esté lo siguiente (generado previamente por el wizard de Wammu):  
  
```
\[gammu\]  
port = /dev/ttyUSB0  
connection = dku5fbus  
name = Nokia 3220  

```  
Para comprobar la conexión, ejecuto:  
  
```
gammu --identify  

```  
Obtengo:  
  
```
Device               : /dev/ttyUSB0  
Manufacturer         : Nokia  
Model                : 3220 (RH-49)  
Firmware             : 05.10 I (07-09-05)  
Hardware             : 6203  
...  
Old simlock          : TIM Peru (716 10)  
UEM                  : 400  

```  
Se puede obtener un listado de los archivos (en un formato tipo árbol):  
  
```
gammu --getfilesystem  

```  
O también un listado plano:  
  
```
gammu --getfilesystem -flatall  

```  
Con el listado plano, veo que los archivos de las fotos están en `d:/predefgallery/predefphotos`. Entonces, ejecuto:  
  
```
gammu --getfilefolder d:/predefgallery/predefphotos  

```  
Y logré descargar mis fotos.  
  
Para más ayuda sobre el comando gammu:  
  
```
gammu --help  
gammu --help filesystem  

```  
Al querer eliminar los archivos Image\*.jpg, encontré que no funcionaba `gammu --deletefiles d:/predefgallery/predefphotos/Image*`.  
  
Entonces, ubicado en el directorio donde descargué las fotos, ejecuté este comando:  
  
```
for p in $(ls Image\*); do echo $p; gammu --deletefiles d:/predefgallery/predefphotos/$p; done  

```  
Quizás les sirva de ayuda.  
  
Referencias  
  

*   [COMO: Archivos de Nokia 3220 ( u otro ) a Ubuntu](https://lists.ubuntu.com/archives/ubuntu-es/2006-June/016657.html)

_*Url archivado: [Acceder a Nokia 3220 usando Gammu](https://akcdev.blogspot.com/2011/06/acceder-nokia-3220-usando-gammu.html)*_

---
### Comentarios archivados:

>
> uuuuuuuuuuuu mucho tramite pa sacar unaj fotos pero lo voy a probar jajaja
> \
> [Anónimo](# "noreply@blogger.com") [2012-11-27 18:29]

>
> Lo ideal sería que Nokia PC Suite funcionara bien. Por alguna razón tenía problemas de conexión y esté método puede ser de ayuda en ese caso... o para curiosear ;-)
> \
> [Rulo Kobashikawa](https://www.blogger.com/profile/07020497448167262255 "noreply@blogger.com") [2012-11-27 18:48]

>
> mi pregunta es si se puede usar tarjeta de memoria en el celular
> \
> [Anónimo](# "noreply@blogger.com") [2013-02-02 22:13]

>
> No se puede usar tarjeta de memoria en el nokia 3220a, 3220b ni en el nokia 3200
> \
> [Anónimo](# "noreply@blogger.com") [2013-09-09 10:32]

>
> en el real? no
> \
> [23youtin](https://www.blogger.com/profile/16592928905619145234 "noreply@blogger.com") [2014-02-16 05:54]
