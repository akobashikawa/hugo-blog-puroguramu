---
title: 'XAMPP en Ubuntu'
date: 2011-06-03T16:14:00.003-05:00
draft: false
url: /2011/06/xampp-en-ubuntu
tags: 
- linux
- xampp
- blogger
---

[![](http://4.bp.blogspot.com/-3YKFAHdviag/S1CjewJ-MVI/AAAAAAAAAMg/JTfeebYypaI/s200/20-xampp-logo-trio.jpg)](http://4.bp.blogspot.com/-3YKFAHdviag/S1CjewJ-MVI/AAAAAAAAAMg/JTfeebYypaI/s1600/20-xampp-logo-trio.jpg)

XAMPP empaqueta Apache, MySQL, PHP y otros programas que se suelen usar en programación web.  
  
Instalar y usar XAMPP para desarrollo me ha venido resultando una alternativa más práctica que buscar/instalar/configurar cada uno de sus componentes por separado.  
  
Para instalar XAMPP en Ubuntu se pueden seguir las instrucciones para el caso Linux, que aparecen en el sitio de ApacheFriends: [http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html).  
  
Básicamente, consiste en descargar el tar.gz de la versión que se desea y extraer el contenido a /opt.  
  
En mi caso, se trata de instalar XAMPP 1.7.1, que es la versión compatible con Drupal 6.  

*   Descargo xampp-linux-1.7.1.tar.gz ([http://sourceforge.net/projects/xampp/files/XAMPP%20Linux/1.7.1/](http://sourceforge.net/projects/xampp/files/XAMPP%20Linux/1.7.1/)).
*   Abro una consola de comandos y cambio a usuario root:  
    ```
    sudo -s
    ```
*   Extraigo el contenido del tar.gz a /opt:  
    ```
    tar -xvzf xampp-linux-1.7.1.tar.gz -C /opt
    ```
*   Para iniciar xampp:  
    /opt/lampp/lampp start
*   Para detener xampp:  
    ```
    /opt/lampp/lampp stop
    ```
*   Para establecer contraseñas (que se recomienda por seguridad):  
    ```
    /opt/lampp/lampp security
    ```

Se puede observar que el comando es lampp. Ese era el nombre que ApacheFriends le había puesto. Sin embargo, es xampp para Linux.

  

Panel de Control

Para tener un panel de control similar al que estaba disponible en Windows:

*   En la consola de comandos:  
    ```
    sudo gedit ~/.local/share/applications/xampp-control-panel.desktop
    ```En este caso uso gedit, pero también se pudo haber invocado otro editor de texto, como nano o vi.
*   En el editor de texto:  
      
    ```
    \[Desktop Entry\]  
    Comment=Start and Stop XAMPP  
    Name=XAMPP Control Panel  
    Exec=gksudo python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py  
    Icon\[en\_CA\]=/usr/share/icons/Humanity/devices/24/network-wired.svg  
    Encoding=UTF-8  
    Terminal=false  
    Name\[en\_CA\]=XAMPP Control Panel  
    Comment\[en\_CA\]=Start and Stop XAMPP  
    Type=Application  
    Icon=/usr/share/icons/Humanity/devices/24/network-wired.svg  
    
    ```

  
Después de eso, podrá encontrar una nueva opción en el menú: _Applications/Other/XAMPP Control Panel_.

  

Referencias  

*   [http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)
*   [How To: Add GUI xampp control panel on ubuntu](http://freshtutorial.com/add-gui-xampp-control-panel-ubuntu/)

_*Url archivado: [XAMPP en Ubuntu](https://akcdev.blogspot.com/2011/06/xampp-en-ubuntu.html)*_
