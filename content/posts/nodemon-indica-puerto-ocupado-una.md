---
title: 'Nodemon indica puerto ocupado: una solución'
date: 2019-11-07T12:06:00.002-05:00
draft: false
url: /2019/11/nodemon-indica-puerto-ocupado-una
tags: 
- nodejs
- nodemon
- express
- blogger
---

Usando nodemon en express:  
  
**package.json**  
```
  ...  
  "scripts": {  
    "start": "node ./bin/www",  
    "dev": "nodemon ./bin/www"  
  },  
  ...  

```  
A veces me pasa que indica que el puerto ya está ocupado. Entonces, procedo a matar el proceso para comenzar otra vez.  
  
```
$ lsof -i:3000  
$ kill 1234  

``````
$ npm run dev
```  
Donde 3000 sería el puerto y 1234 el PID del proceso.  
  
Una forma de aliviar la molestia:  
  
```
$ kill $(lsof -i:3000 -t); npm run dev  
  

```  
Otra forma es usar kill-port y un delay.  
  
```
$ npm install --save-dev kill-port  

```  
**package.json**  
```
  ...  
  "scripts": {  
    "start": "node ./bin/www",  
    "dev": "kill-port 3000 && nodemon \--delay 1 ./bin/www"  
  },  
  ...  

```

_*Url archivado: [Nodemon indica puerto ocupado: una solución](https://akcdev.blogspot.com/2019/11/nodemon-indica-puerto-ocupado-una.html)*_
