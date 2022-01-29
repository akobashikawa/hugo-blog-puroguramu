---
title: 'Resolviendo el virus que crea acceso directo intermediario en memorias y discos portátiles'
date: 2013-08-27T12:31:00.001-05:00
draft: false
url: /2013/08/resolviendo-el-virus-que-crea-acceso
tags: 
- solución
- portátil
- drive
- disco
- archivos
- usb
- blogger
---

En días pasados, conecté mi disco duro portátil en una computadora y noté que todos los archivos desaparecían de su directorio raíz y en su lugar aparecía un acceso directo.  
  
Haciendo click en el acceso, se podía acceder a los archivos. Era como si hubiera aparecido un nivel más.  
  
Viendo en la ruta mostrada por el navegador de archivos, aparecía un directorio de nombre vacío conteniendo todo lo demás.  
  
En algunas computadoras con antivirus, aparecía una alerta al intentar ejecutar el acceso.  
  
Buscando en Internet no encontré ninguna referencia al problema.  
  
Felizmente, revisando un poco el disco, encontré que era posible deshacer el cambio manualmente. Así que aquí está el procedimiento por si ayuda a alguien más (ayer tuve el mismo problema luego de usar mi usb en en una computadora pública):  
  

*   Realizar el procedimiento en una computadora limpia, con antivirus. Es decir que no haya ocasionado el problema que describí.
*   En el explorador de archivos, entrar al menú (tecla Alt), y entrar Herramientas, Opciones de Carpeta. Activar ver los archivos ocultos y también ver archivos del sistema (que normalmente están desactivados).
*   Conectar el disco o usb infectado. Podrá ver varios archivos de nombres raros, incluyendo el acceso directo. Pero también uno de nombre aparentemente en blanco.
*   Ingresar a ese directorio de nombre en blanco para verificar que están nuestros archivos.
*   En este punto se pueden hacer varias cosas. Como copiar todos nuestros archivos a otra unidad, formatear el drive infectado y luego copiar otra vez nuestros archivos.
*   Una opción más rápida es eliminar todos los archivos de nombres raros, incluyendo el acceso directo, y dejando sólamente el directorio de nombre en blanco. En el directorio en blanco, también eliminar los archivos raros que notara en su interior (como desktop.ini, en mi caso). Luego, mover todos los archivos del directorio en blanco al directorio raíz. Finalmente, eliminar el directorio en blanco.  
    Son más pasos, pero mover archivos consume menos tiempo que copiarlos a otro drive y traerlos de vuelta.

_*Url archivado: [Resolviendo el virus que crea acceso directo intermediario en memorias y discos portátiles](https://akcdev.blogspot.com/2013/08/resolviendo-el-virus-que-crea-acceso.html)*_
