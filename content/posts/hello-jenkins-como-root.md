---
title: 'Hello Jenkins: Como root'
date: 2018-12-31T14:59:00.002-05:00
draft: false
url: /2018/12/hello-jenkins-como-root
tags: 
- ci
- jenkins
- blogger
---

En el post [Hello Jenkins](https://akcaprendiendo.blogspot.com/2018/12/hello-jenkins.html), exploré cómo podría automatizar el deploy de un site estático simple con ayuda de Jenkins.  
  
Este site estático está alojado en mi directorio web personal ~/public\_html. Para que Jenkins pudiera hacer pull allí, fue necesario que tuviera derechos sobre los archivos de ese directorio, así que opté por agregarlo a mi grupo de usuario.  
  
Ahora exploro cómo sería si quisiera que Jenkins pudiera hacer pull en el directorio web /var/www.  
  
En mi Jenkins, proyecto hello-jenkins, Configuration, Source Code Management:  
  

*   En **Aditional Behaviours**, pruebo agregar:

*   **Chek out to a sub-directory**

*   Local sub-directory for repo:  
    /var/www/html/demos/hello-jenkins/

Una prueba muestra un error de acceso al directorio. Probé agregar jenkins al grupo sudo y tambien visudo, pero no pude solucionarlo.

  

Opto por agregar el siguiente script en **Build**:

*   echo "hello-jenkins build"
*   cd /var/www/html/demos/hello-jenkins
*   sudo git pull

Hago la prueba y funciona como se espera. Se hace pull al hello-jenkins en mi directorio personal public\_html/ y tambien en el directorio web /var/www/.  
  
  

_[Post original en https://akcaprendiendo.blogspot.com/2018/12/hello-jenkins-como-root.html](https://akcaprendiendo.blogspot.com/2018/12/hello-jenkins-como-root.html)_

_*Url archivado: [Hello Jenkins: Como root](https://akcdev.blogspot.com/2018/12/hello-jenkins-como-root.html)*_
