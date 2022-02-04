---
title: 'NodeJS en DigitalOcean'
date: 2015-11-29T10:55:00.000-05:00
draft: false
url: /2015/11/nodejs-en-digitalocean
tags: 
- nodejs
- blogger
---

[![](https://3.bp.blogspot.com/-8AkhLuEUlyo/VlsdFFC-kEI/AAAAAAAADyI/q5eZqfdJ8wI/s320/nodejs.png)](https://3.bp.blogspot.com/-8AkhLuEUlyo/VlsdFFC-kEI/AAAAAAAADyI/q5eZqfdJ8wI/s1600/nodejs.png)

  
Vengo aprendiendo NodeJS desde hace unos meses.  
  
Actualmente, tengo voy creando aplicaciones sencillas con Express (un framework para Node) y Angular.  
  
Esas aplicaciones suelen funcionar bien en mi localhost:3000, que es la dirección por default de los proyectos en Express.  
  
Recientemente, tuve la necesidad de deployar una de esas aplicaciones en un hosting y eso me ayudó a completar esa parte del cuadro.  
  

DigitalOcean
------------

[![](https://2.bp.blogspot.com/-VCHjD8mxrh0/VlsdKVSC2fI/AAAAAAAADyQ/bxP0va6uXtE/s320/DO_Logo_Vertical_Blue-75e0d68b.png)](https://www.digitalocean.com/)

  

  

https://www.digitalocean.com/

  
Permite crear droplets donde puedes instalar el sistema operativo de tu preferencia y allí dentro lo que desees, como harías con tu propio servidor. Puedes instalar tantos droplets como desees. Hay un pago mensual, dependiendo de tu consumo de recursos, pero me parece que es uno de los más económicos en su rubro.

Linux Ubuntu
------------

Puede ser cualquier variante de Linux. En mi caso, elegí instalar un droplet con Ubuntu 14.04.3 LTS (trusty). Una vez creado el droplet, te envían el password del root por email.  
  
Luego seguí la guía [Initial Server Setup with Ubuntu 14.04](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-14-04)

NodeJS
------

Instalé node vía NVM, que permite usar varias versiones de node en simultáneo.

  

[How To Install Node.js with NVM (Node Version Manager) on a VPS](https://www.digitalocean.com/community/tutorials/how-to-install-node-js-with-nvm-node-version-manager-on-a-vps)

  
Por ejemplo, para instalar la versión más estable:  
  
$ nvm install stable  
$ nvm use stable  

Express
-------

Express puede ser agregado como un módulo más a una aplicación web. Hay varios módulos y que se pueden ir agregando paulatinamente para facilitar el paso de parámetros en los request, las sesiones, el debug, etc. El esquema de trabajo también se puede adaptar a las preferencias personales.

  

Sin embargo, Express Generator puede construir un esquema base típico para ahorrarnos algo de tiempo.

  

$ npm install -g express express-generator

$ express --git myexpress

  

La aplicación corre en el puerto 3000 por default:

  

$ npm start

  

O también:

  

$ node ./bin/www

  

http://localhost:3000

  

### Nodemon

Durante el desarrollo puede ser práctico usar nodemon para que el servidor se reinicie cuando detecte algún cambio en los archivos de la aplicación:

  

$ npm install -g nodemon

$ nodemon start

### Nunjucks

El sistema de templates por default es **jade**, pero hay alternativas como **nunjucks**:

  

[https://github.com/akobashikawa/express-nunjucks](https://github.com/akobashikawa/express-nunjucks)

PM2
---

PM2 permite correr la aplicación como un servicio, monitorear su estado, detenerla, reiniciarla, etc.  
  
$ pm2 start ./bin/www  
  
Las opciones de inicio de la aplicación se pueden colocar en un archivo **processes.json**:  
  

```
{  
  "apps" : \[{  
    "name"        : "myexpress",  
    "script"      : "./bin/www",  
    "log\_date\_format"  : "YYYY-MM-DD HH:mm Z"  
  }\]  
}  

```

  

$ pm2 start processes.json

Nginx
-----

Aunque es posible hacer que una aplicación node corra en el puerto 80, hay una alternativa y es la de usar Nginx como proxy reverso para que la aplicación node siga usando el puerto 3000 pero pueda ser accedida a través del puerto 80.  
  
**/etc/nginx/sites-available/default**

  
```
server {  
    listen 80;  
  
    server\_name rulo.me;  
  
    location /myexpress/ {  
        proxy\_pass http://rulo.me:3000/;  
        proxy\_redirect off;  
        proxy\_http\_version 1.1;  
        proxy\_buffering off;  
        proxy\_set\_header X-Real-IP $remote\_addr;  
        proxy\_set\_header X-Forwarded-For $proxy\_add\_x\_forwarded\_for;  
        proxy\_set\_header Host $host;  
        proxy\_set\_header X-NginX-Proxy true;  
    }  
  
   location /app-two/ {  
        proxy\_pass http://rulo.me:3010/;  
        proxy\_redirect off;  
        proxy\_http\_version 1.1;  
        proxy\_buffering off;  
        proxy\_set\_header X-Real-IP $remote\_addr;  
        proxy\_set\_header X-Forwarded-For $proxy\_add\_x\_forwarded\_for;  
        proxy\_set\_header Host $host;  
        proxy\_set\_header X-NginX-Proxy true;  
    }  
  
    location ~ ^/(images/|img/|javascript/|js/|css/|stylesheets/|flash/|media/|static/|robots.txt|humans.txt|favicon.ico) {  
        root /home/rulo/www/expressdemo/public;  
        access\_log off;  
        expires max;  
    }  
  
}  

```  
La idea es que se solicita al servidor web nginx algo como **http://midominio.com/myexpress/**, entonces él revisa en su mapeo previamente configurado que ese url le corresponde a la aplicación que se ejecuta en el puerto **3000** (que se llama **myexpress**, pero podría ser otro nombre también) y procede a servirla. Para el usuario parece que se estuviera accediendo a la applicación directamente a través del puerto 80.  
  
Esta estrategia permite tener varias aplicaciones corriendo en diferentes puertos que pueden ser accedidas a través de urls adecuadas, por ejemplo **cualquiernombre:3010** a través de **http://midominio.com/app-two**

_*Url archivado: [NodeJS en DigitalOcean](https://akcdev.blogspot.com/2015/11/nodejs-en-digitalocean.html)*_
