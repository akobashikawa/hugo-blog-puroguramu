---
title: 'Acceder a un Server en Virtualbox desde el Host'
date: 2011-06-07T11:51:00.002-05:00
draft: false
url: /2011/06/acceder-un-server-en-virtualbox-desde
tags: 
- virtuallización
- windows
- linux
- blogger
---

[![](http://2.bp.blogspot.com/-yEzZU-vUNME/TebOTGXljkI/AAAAAAAABVk/UAosUOEB_NA/s200/Windows-7-Ubuntu-Linux.png)](http://2.bp.blogspot.com/-yEzZU-vUNME/TebOTGXljkI/AAAAAAAABVk/UAosUOEB_NA/s1600/Windows-7-Ubuntu-Linux.png)

**Virtualbox** es una aplicación que permite instalar un sistema operativo dentro de otro. Por ejemplo, puedo instalar Ubuntu Linux dentro de Windows 7. En el caso que describo a continuación, está instalado **Windows XP** dentro de **Ubuntu Linux** (Natty Narwhal).  
  
Por qué  
Al requerir un entorno de desarrollo Drupal que sea portable, la solución que encontré fue usar **XamppLite portable** (disponible para Windows) en un USB.  
  
Como trabajar directamente en el USB me parece muy lento, copio el directorio de xampplite al disco duro y trabajo allí. Luego, al final del día, sincronizo esa copia con el USB.  
  
Como todo el estado de la base de datos MySQL está en los archivos generados, al copiarlos todas las bases de datos, tablas y cambios se reflejan idénticamente.  
  
Al volver a trabajar en Linux, me interesó encontrar un modo de levantar el xampplite. Intenté con Wine y, aunque arranca el panel de control de xampp, no se puede iniciar el servidor apache. Entonces, lo hice con Virtualbox.  
  
Instalé Virtualbox 4.0.8 para Ubuntu y allí instalé Windows XP.  
  
De modo que, en la jerga de la virtualización, Ubuntu es el _**Host**_ y Windows XP es el _**Guest**_.  
  
Pude correr xampplite y funcionaba apache. Pero no encontraba el modo de acceder al servicio web del Guest desde el Host.  
  
Usando VBoxManage  
No logré encontrar en la interfaz de Virtualbox un modo de configurar eso.  
  
Después de navegar un poco en Internet, encontré en Sitepoint el artículo [Build Your Own Dev Server with VirtualBox](http://blogs.sitepoint.com/build-your-own-dev-server-with-virtualbox/). Allí, la solución consiste en editar a mano el archivo XML de la configuración de la máquina virtual.  
  
Si uno revisa ese archivo (VirtualBox.xml) puede encontrar la advertencia de no editarlo a mano. Así que indagué un poco más para ver si había otro modo y lo encontré en el artículo [How to access a server running in a VirtualBox guest](http://www.salixos.org/wiki/index.php/How_to_access_a_server_running_in_a_VirtualBox_guest), que indica cómo hacer los cambios usando el comando VBoxManage.  
  
Primero hay que apagar la máquina virtual. Los cambios se harán efectivos al reiniciarla.  
  
Para listar las máquinas virtuales:  
  
```
VBoxManage list vms  

```  
Hay que establecer varios _**extradata**_ en el Guest "Windows XP":  
  
```
VBoxManage setextradata "Windows XP" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/apache/HostPort" 8888  
VBoxManage setextradata "Windows XP" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/apache/GuestPort" 80  
VBoxManage setextradata "Windows XP" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/apache/Protocol" TCP  

```  
Para verificar:  
  
```
VBoxManage getextradata "Windows XP" enumerate  

```  
Si hubiera que eliminar alguno, bastaría con darle un valor en blanco. Por ejemplo:  
  
```
VBoxManage setextradata "Windows XP" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/apache/HostPort" 8888  

```  
A continuación inicié el Guest, y el servidor apache que contiene.  
  
En el Host pude acceder al servicio web entrando a:  
  
```
http://localhost:8888  

```  
Referencias  

*   [Build Your Own Dev Server with VirtualBox](http://blogs.sitepoint.com/build-your-own-dev-server-with-virtualbox/)
*   [How\_to\_access\_a\_server\_running\_in\_a\_VirtualBox\_guest](http://www.salixos.org/wiki/index.php/How_to_access_a_server_running_in_a_VirtualBox_guest)

_*Url archivado: [Acceder a un Server en Virtualbox desde el Host](https://akcdev.blogspot.com/2011/06/acceder-un-server-en-virtualbox-desde.html)*_

---
### Comentarios archivados:

>
> Excelente tu post pero me sirvió medias, te explico:  
hice todo lo que explicas aqui pero igual no puedo acceder al localhost del guest...  
que configuracion de red hay que tener en el VM.  
ya deshabilite el firewall en windows y nada  
que otra cosa puedo hacer  
saludos
> \
> [Unknown](https://www.blogger.com/profile/07035887741753533463 "noreply@blogger.com") [2012-03-10 17:45]

>
> Gracias. Lo que se me ocurre es que repitas los pasos haciendo las comprobaciones que puedas. También podrías verificar que el host (linux) no tenga algún firewall que esté interfiriendo.
> \
> [Rulo Kobashikawa](https://www.blogger.com/profile/07020497448167262255 "noreply@blogger.com") [2012-03-12 11:44]

>
> Buen post.. Yo ando buscando lo inverso a esto.. Es decir, acceder al localhost del host (linux) desde el guest (w7).. Tenés idea si se puede?
> \
> [ramiro](https://www.blogger.com/profile/16561326428368436100 "noreply@blogger.com") [2014-08-11 22:23]
