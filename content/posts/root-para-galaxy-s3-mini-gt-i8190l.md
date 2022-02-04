---
title: 'Root y Link2SD para Galaxy S3 Mini (GT-I8190L)'
date: 2013-12-08T13:38:00.004-05:00
draft: false
url: /2013/12/root-para-galaxy-s3-mini-gt-i8190l
tags: 
- android
- hacking
- blogger
---

[![](https://4.bp.blogspot.com/-8Mxk6SJDKDw/UqS6vtvJVbI/AAAAAAAACVw/hkYOjoMwBLw/s320/Android-Root.png)](https://4.bp.blogspot.com/-8Mxk6SJDKDw/UqS6vtvJVbI/AAAAAAAACVw/hkYOjoMwBLw/s1600/Android-Root.png)

  

Root
----

*   Consideraciones previas:

*   El proceso de rooteo aquí descrito se supone que no es destructivo, pero siempre es recomendable hacer un backup, principalmente de la información más importante.
*   El proceso puede tardar como 10 minutos. Asegurarse que la batería del celular tenga una buena cantidad de carga (yo lo hice con 20% aunque se recomienda 80%).
*   Tener a mano el cable de conexión USB para conectar el celular a la PC (pero no conectarlo hasta que la guía lo indique).
*   Que en el celular esté activado el modo de depuración.
*   Tener activa la conexión a Internet en la PC.
*   Puede ser que si está instalado una versión antigua de Kies, Odin no reconozca al dispositivo. (A mi me pasó, pero el inconveniente es salvable. Desinstalé Kies y los drivers asociados y más bien instalé los drivers usando el mini toolkit.)
*   Ver las guias completas antes de realizar los pasos.
*   Este post es sólo con fines educativos. La responsabilidad de la ejecución es tuya.

*   Ejecutar **Samsung Galaxy S3 Mini Toolkit,** que es un programa que permite automatizar muchas de las cosas que hay que hacer a mano en otros tutoriales. **(**La versión actual 1.3.5 se puede descargar de [https://mega.co.nz/#!CghX0bqT!ST73wkDV07JQ8Of84xISTR6p6rNG42gUAJmGX-PKTwM](https://mega.co.nz/#!CghX0bqT!ST73wkDV07JQ8Of84xISTR6p6rNG42gUAJmGX-PKTwM))
*   Seguir las instrucciones del video [http://www.youtube.com/watch?v=dO2O6HMQirc](http://www.youtube.com/watch?v=dO2O6HMQirc) 

*   En el video no aparece la opción 33 (la versión del toolkit es más antigua), que se parece mucho a la 32. Yo elegí la 32 y resultó bien.
*   En el video no hacen el paso de instalar los drivers. Yo lo hice y luego continué con las demás instrucciones.
*   Habrá un momento en que indicará conectar el celular a la PC. Hacerlo, pero antes de continuar, esperar a que Windows lo reconozca. El toolkit iniciará **Odin** (la herramienta que se usa para instalar una nueva ROM en el celular). Cuando Windows reconoce el celular, en Odin la primera casilla ID:COM debe aparecer en azul. Entonces continuar.

*   Luego del rooteo, en la lista de aplicaciones instaladas aparecerá SuperSU.

### Link2SD

[![](https://1.bp.blogspot.com/-wvfSHW6I-KI/UqS62jkhYII/AAAAAAAACV8/L4gF9iV0kuc/s200/android-sd-card.jpg)](https://1.bp.blogspot.com/-wvfSHW6I-KI/UqS62jkhYII/AAAAAAAACV8/L4gF9iV0kuc/s1600/android-sd-card.jpg)

*   Luego del rooteo, para usar la app **[Link2SD](https://play.google.com/store/apps/details?id=com.buak.Link2SD)** para enlazar las aplicaciones a la memoria **SD externa**, se requiere que además se haga una segunda partición primaria en esa memoria. Para ello se puede seguir la guía [http://forum.xda-developers.com/wiki/SD\_card\_partitioning](http://forum.xda-developers.com/wiki/SD_card_partitioning), que usa el programa Mini Partition Wizard. Una guía alternativa es [http://www.htcmania.com/showthread.php?t=540481](http://www.htcmania.com/showthread.php?t=540481).

*   El programa **Mini Partition Wizard** se puede descargar de [http://download.cnet.com/MiniTool-Partition-Wizard-Home-Edition/3000-2094\_4-10962200.html](http://download.cnet.com/MiniTool-Partition-Wizard-Home-Edition/3000-2094_4-10962200.html)
*   La operación de repartición no se realiza en el celular sino en la PC. Así que hay que entrar a _Configuración, Almacenamiento, Tarjeta de memoria, Retirar la tarjeta de memoria_. Luego, apagar el celular, quitar la tarjeta de memoria (que esta debajo de la batería) y **colocarla en un adaptador** que permita conectarla a la PC.
*   Luego que Windows reconozca la tarjeta SD, formatearla y particionarla siguiendo las instrucciones de alguna de las guías. Para el tamaño de la primera partición, elegí FAT32 y todo el espacio disponible menos 1 GB (mi SD es de 8 GB). Para el tamaño de la segunda partición primaria, elegí Ext4 y 1024 MB.
*   Luego de retirar la memoria de la PC y el adaptador, se puede volver a colocar en el celular. Quizás sea necesario reiniciarlo una vez para asegurarse que lo reconozca adecuadamente.
*   Al ejecutar Link2SD, pedirá autorización de root. Luego de dársela, preguntará por el tipo de partición (Ext4 en mi caso) e indicará reiniciar el celular.

### Referencias

*   [http://akcaprendiendo.blogspot.com/2013/12/root-y-link2sd-para-galaxy-s3-mini-gt.html](http://akcaprendiendo.blogspot.com/2013/12/root-y-link2sd-para-galaxy-s3-mini-gt.html)
*   [http://www.youtube.com/watch?v=dO2O6HMQirc](http://www.youtube.com/watch?v=dO2O6HMQirc)
*   [http://forum.xda-developers.com/wiki/SD\_card\_partitioning](http://forum.xda-developers.com/wiki/SD_card_partitioning)
*   [http://www.htcmania.com/showthread.php?t=540481](http://www.htcmania.com/showthread.php?t=540481)

_*Url archivado: [Root y Link2SD para Galaxy S3 Mini (GT-I8190L)](https://akcdev.blogspot.com/2013/12/root-para-galaxy-s3-mini-gt-i8190l.html)*_
