---
title: 'Ubuntu Natty Narwhal con Windows 7'
date: 2011-06-01T18:48:00.002-05:00
draft: false
url: /2011/06/ubuntu-natty-narwhal-con-windows-7
tags: 
- windows
- linux
- blogger
---

[![](http://2.bp.blogspot.com/-yEzZU-vUNME/TebOTGXljkI/AAAAAAAABVk/UAosUOEB_NA/s200/Windows-7-Ubuntu-Linux.png)](http://2.bp.blogspot.com/-yEzZU-vUNME/TebOTGXljkI/AAAAAAAABVk/UAosUOEB_NA/s1600/Windows-7-Ubuntu-Linux.png)

Hoy he instalado Ubuntu Natty Narwhal (ubuntu-11.04-desktop-i386.iso) junto a Windows 7, que ya estaba instalado. Aunque no ha sido tan fácil como parecía.  
  
Intro  
La PC de la oficina es una Compaq Presario CQ5310LA PC, con Windows 7 instalado de fábrica. Hace muchos años, en otra oficina, habitualmente usaba RedHat o Suse, pero recientemente la he pasado más con Windows XP y Windows 7.  
  
Cuando necesito hacer alguna tarea en el servidor Linux, abro un terminal con Putty. Si quiero experimentar alguna aplicación Linux, puedo usar VMWare o VirtualBox para instalar allí alguna distribución.  
  
Me gusta mucho la opción de la virtualización con VMWare o VirtualBox pero, si no hay mucha memoria,  todo el sistema se vuelve bastante lento.  
  
Viendo a los amigos de la comunidad Drupal Perú usando Linux y, considerando los temas que me gusta investigar, me animé a dar el salto para volver a usarlo más intensivamente.  
  
Sin embargo, hay algunas cosas de desarrollo web para las que tengo herramientas habituales en Windows. Así que lo tengo a la vuelta para cuando lo necesite, mientras voy desarrollando alternativas.  
  
No tan fácil como parecía  
No es la primera vez que instalo Ubuntu. Incluso antes he hecho una instalación dual con Windows XP. En aquella ocasión aprendí que a veces el sistema de arranque de Windows y el de Linux se cruzan y hay que hacer algunas correcciones luego del proceso.  
  
Esta vez, vi con agrado que había una interfaz incluida en el proceso de instalación para cambiar el tamaño de la partición Windows existente para hacer espacio a la nueva partición para Ubuntu. Además, no requería de ninguna operación previa de defragmentación. Supuese que era una señal de que el proceso sería más facil ahora, pero no fue así.  
  
Puse el instalador en un USB (usando Lili USB Creator) y reinicié el sistema para arrancar desde ahí.  
  
En el proceso de instalación, el reparticionamiento fue casi automático. Indiqué 50 GB para la nueva partición Linux. Luego continuó bien pero, casi al final, falló por alguna razón. Un mensaje de error irrecuperable. Reinicié el proceso.  
  
La segunda vez hice el proceso desde el escritorio del Live CD. Ya no ocurrió el error irrecuperable y la instalación se completó, pero tardó bastante tiempo la descarga de los archivos de actualización y otros. Quizás hubiera dejado esa opción para después. Sin embargo, como estaba en el escritorio, podía navegar mientras esperaba :)  
  
Cuando reinicié, esperaba que apareciera el menú de inicio de Grub (usado para iniciar Linux), pero la pantalla se quedó en negro, con el rectángulo que muestra el monitor cuando no recibe ninguna señal.  
  
Probé reiniciar varias veces, sin resultado. Felizmente hice backup, pensé.  
  
Por si acaso, repetí el proceso de instalación. Para no descargar las actualizaciones, desconecté el cable de red y así fue un poco menos el tiempo. Pero el resultado fue el mismo.  
  
Felizmente, usando el navegador de archivos del Live CD podía comprobar que los archivos de Windows estaban allí. El problema era que se había perdido el arranque.  
  
Hice un disco de rescate en otra máquina que también tiene Windows 7 y seguí el procedimiento de reparar el sector de inicio. Reinicié, pero seguía igual.  
  
Una esperanza  
Entonces, cruzado de brazos, vi como después de casi un minuto, en la pantalla apareció Ubuntu. Al parecer, el sistema si iniciaba, pero con un Grub silente. Sin Grub, ¿cómo escoger la opción de iniciar con Windows?  
  
Investigando, encontré una solución para corregir el inicio perdido de Windows. Consiste en usar el disco de rescate para iniciar una consola y desde allí ejecutar:  
  
```
bootrec /fixmbr  
bootrec /fixboot  

```  
Funcionó y se inició Windows 7 normalmente.  
  
Más o menos  
Ahora, para tener un acceso a Ubuntu iba a intentar tratar con Grub, pero antes probé bajar el utilitario EasyBCD, que había visto mencionaban en los foros.  
  
Allí, modifiqué el menú de inicio, agregando un nuevo item para sistema operativo Linux, tipo de inicio Grub2 (el usado por Ubuntu 11). Salve los cambios y reinicié.  
  
Esta vez, apareció un menú de inicio provisto por Windows. Elegí Ubuntu. La pantalla se puso negra y, luego de un rato, apareció Ubuntu.  
  
Corrigiendo el menú de Grub  
Encontré una solución al problema de la pantalla negra antes de Ubuntu. Al parecer, no se estaba presentando bien el menú de grub. En la consola ejecuté:  
  
```
sudo gedit /etc/default/grub.conf  

```  
Para editar el archivo de configuración de grub. En lugar de gedit también se puede usar otro editor, como nano.  
  
En grub.conf, localizar la línea #GFX640x480 y descomentarla, de modo que queda:  
  
```
GFX640x480  

```  
A continuación:  
  
```
sudo update-grub  

```  
Al reiniciar la máquina, aparece primero el menú de inicio de Windows (el que configuré con ayuda de EasyBCD). Si elijo Ubuntu, aparece el menú de inicio de Grub. Bien.  
  
Restableciendo el arranque de Grub  
Quizás se podría simplificar el pasar primero del menú de inicio de Windows al menú de inicio de Grub.  
  
Se puede conseguir reinstalando el menú de inicio Grub:  
  
```
sudo grub-install /dev/sda  

```  
En mi caso, /dev/sda es el disco donde se coloca el inicio.  
  
Al reiniciar la máquina, aparece primero el menú de inicio de Grub. Si elijo Windows, aparece el menú de inicio de Windows. Tiene sentido.  
  
Para que no aparezca el menú de inicio de Windows, uso EasyBCD para quitar la opcion Ubuntu y además indicar que omita el menú de inicio.  
  
Una vez hecho esto, al reiniciar la máquina, aparece sólamente el menú de inicio de Grub, desde donde se puede elegir Linux o Windows.  
  
En resumen  
Para instalar Ubuntu (11, Natty Narwhal) junto a un Windows 7, ya instalado:  
  

*   No es necesario reparticionar el disco antes de correr el instalador de Ubuntu. Tampoco es necesario defragmentarlo.
*   Ejecutar el instalador de Ubuntu, eligiendo la instalación lado a lado, junto al Windows 7 existente e indicando el tamaño de la partición destinada a Ubuntu. Un mínimo recomendable suele ser 20 GB. Yo elegí 40 GB, pero puede ser tanto como se quiera.
*   Sí, luego de ejecutar la instalación, no se ve ningún menú que permita elegir qué sistema iniciar, aguardar un poco. En mi caso, me parece que luego de 30 segundos, se iniciaba Ubuntu.
*   Para corregir la falta de visualización del menú de inicio de Grub, editar el archivo **/etc/default/grub.conf** y descomentar la linea #GFX640x480.

  
Referencias  
  

*   [http://forums.scotsnewsletter.com/index.php?showtopic=45226](http://forums.scotsnewsletter.com/index.php?showtopic=45226)

_*Url archivado: [Ubuntu Natty Narwhal con Windows 7](https://akcdev.blogspot.com/2011/06/ubuntu-natty-narwhal-con-windows-7.html)*_
