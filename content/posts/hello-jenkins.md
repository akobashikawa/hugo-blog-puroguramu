---
title: 'Hello Jenkins'
date: 2018-12-30T23:28:00.005-05:00
draft: false
url: /2018/12/hello-jenkins
tags: 
- ci
- jenkins
- blogger
---

[![](https://3.bp.blogspot.com/-gqXpcP5sZqo/XCmZ2IBbwNI/AAAAAAAASyo/9yEB_0_lgtA5b2b7edrt2jWFImvGcx9YwCLcBGAs/s320/jenkins-ci_512.png)](https://3.bp.blogspot.com/-gqXpcP5sZqo/XCmZ2IBbwNI/AAAAAAAASyo/9yEB_0_lgtA5b2b7edrt2jWFImvGcx9YwCLcBGAs/s1600/jenkins-ci_512.png)

  
En días recientes estuve viendo un poco de _Continuous Integration / Continuous Deployment_ (CI/CD), con **Jenkins**.  
  
La idea que he captado es que Jenkins corre en el servidor donde normalmente ejecutamos a mano los pasos para deployar un proyecto. Luego configuramos las cosas para que Jenkins las haga por nosotros.  
  
Por ejemplo, puedo tener en mi hosting un site estático hello-jenkins, cuyo repositorio está en GitHub. Luego que hago push en el repo desde mi máquina local debo entrar a la consola de mi hosting y hacer pull. Quizás alguna cosa más, como bower o npm, dependiendo de la complejidad del proyecto.  
  
Empezaré con un simple site estático llamado **hello-jenkins**.  
  

*   En mi local, creo el proyecto hello-jenkins
*   En **GitHub**, creo el repositorio [hello-jenkins](https://github.com/akobashikawa/hello-jenkins)
*   En mi local, establezco al repo en GitHub como mi remoto y hago push
*   En mi hosting, clono el repo de GitHub
*   [https://rulokoba.me/~rulo/demos/hello-jenkins/](https://rulokoba.me/~rulo/demos/hello-jenkins/)

Ahora, haré un cambio y un **deploy manual**.

*   En mi local, agrego un title, commit y push
*   En mi hosting, hago pull

*   Lo pesado de esta tarea es cuando no estoy logueado a la consola. Es necesario hacer ssh, ubicar la carpeta y hacer pull.
*   Si Jenkins vive en este servidor, podría hacerlo por mi ante una señal. Por ejemplo, cuando se hace un push en GitHub.

*   [https://rulokoba.me/~rulo/demos/hello-jenkins/](https://rulokoba.me/~rulo/demos/hello-jenkins/)

En el hosting, tengo instalado Jenkins siguiendo la guía de:

*   [How To Install Jenkins on Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-install-jenkins-on-ubuntu-16-04)

*   Jenkins tiene una aplicación web que permite administrarlo a través del browser

*   Además tiene instalado los plugins para Git y GitHub.

En mi Jenkins, creo el job hello-jenkins:

*   Elijo _create new jobs_
*   _Enter an item name_: hello-jenkins
*   Elijo _Freestyle project_
*   OK
*   En la sección de consiguración:

*   Source Code Management

*   Git

*   _Repository URL_: https://github.com/akobashikawa/hello-jenkins.git
*   _Credentials_: none
*   Additional Behaviours

*   Check out to a sub-directory

*   _Local sub-directory for repo_:  
    /home/rulo/public\_html/demos/hello-jenkins/
*   Para que jenkins pueda escribir en este directorio se le puede agregar al grupo del usuario y reiniciar jenkins:

*   $ sudo usermod -a -G rulo jenkins
*   $ sudo systemctl stop jenkins
*   $ sudo systemctl start jenkins

*   Build Triggers

*   GitHub hook trigger for GITScm polling

*   Build (opcional)

*   Execute shell

*   Command

*   echo "hello-jenkins build"

En el repo de GitHub, _Settings_:

*   Webhooks

*   Add webhook

*   _Payload URL_: http://myjenkins\_url/github-webhook/

*   Es importante el trailing / al final

*   _Content type_: application/json
*   Which events would you like to trigger this webhook?

*   \[x\] Let me select individual events.

*   \[x\] Pushes

*   \[x\] Pull requests

*   \[x\] Active
*   Add webhook
*   Es importante que GitHub pueda encontrar a Jenkins ya configurado

Para probar, manualmente:

*   En mi Jenkins, en el projecto hello-jenkins, wlijo Build Now
*   En _Build History_ aparecerá un nuevo item numerado, y le hago click.
*   Elijo _Console Output_ para ver la salida

Para probar el build automático:

*   En mi local, hago un cambio, commit y push al repo
*   En _Build History_ aparecerá un nuevo item numerado, y le hago click.
*   Elijo _Console Output_ para ver la salida

  

_[Post original en https://akcaprendiendo.blogspot.com/2018/12/hello-jenkins.html](https://akcaprendiendo.blogspot.com/2018/12/hello-jenkins.html)_

_*Url archivado: [Hello Jenkins](https://akcdev.blogspot.com/2018/12/hello-jenkins.html)*_
