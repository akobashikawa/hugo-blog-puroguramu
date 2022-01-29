---
title: 'Test de internet con ping en NodeJS'
date: 2017-12-13T12:29:00.000-05:00
draft: false
url: /2017/12/test-de-internet-con-ping-en-nodejs
tags: 
- ping
- nodejs
- internet
- blogger
---

[![](https://4.bp.blogspot.com/-kwC-zmPAsUU/WjFjQaCxE3I/AAAAAAAALQQ/bT24eeffRrEU7Ri-iWUjFKNpHIu4tHv1wCLcBGAs/s200/Ping-Tester-Pro-Full-9.52-for-APK-android-and-windows-300x300.jpg)](https://4.bp.blogspot.com/-kwC-zmPAsUU/WjFjQaCxE3I/AAAAAAAALQQ/bT24eeffRrEU7Ri-iWUjFKNpHIu4tHv1wCLcBGAs/s1600/Ping-Tester-Pro-Full-9.52-for-APK-android-and-windows-300x300.jpg)

  
En estos días he tenido intermitencias en el servicio de internet.  
  
Mi forma de comprobarlo es entrar en una consola y hacer ping a un host, como google.com, y ver si está ok o no.  
  
```
$ ping google.com -t  
  

```  
El -t permite que el ping se haga indefinidamente, hasta que se presione CTR + C.  
  
Sin embargo, quería una forma de mostrar los cambios de estado, a qué hora ocurrían y cuánto duraban.  
  
Programé esta solución usando nodejs:  
  
[GitHub Gist: Internet test with ping in NodeJS](https://gist.github.com/akobashikawa/1e6d906bc9d44f630206994874ab2fd4)  
  
```
const ping = require('ping');  
  
let host = '8.8.8.8';  
  
if (process.argv\[2\]) {  
  host = process.argv\[2\];  
} else {  
  console.log("Syntax: \\nnode ping-test-ifchanges-host host");  
}  
  
console.log("Testing host: " + host);  
  
let isAlivePrev = false;  
let nowPrev = new Date();  
  
function doPing() {  
  ping.sys.probe(host, isAlive => {  
    if (isAlive !== isAlivePrev) {  
      let now = new Date();  
      let diff = (now.getTime() - nowPrev.getTime())/1000;  
      let timestamp = now.toISOString() + ' after: ' + diff + ' s';  
      console.log("\\n"   
        + host + ': '   
        + (isAlive ? ' OK' : ' KO')   
        + ' ' + timestamp);  
      isAlivePrev = isAlive;  
      nowPrev = now;  
    } else {  
      process.stdout.write('.');  
    }  
  });  
}  
  
setInterval(doPing, 1000);  

```  
Para correrlo en consola:  
  
```
$ node ping-test-ifchanges-host google.com
```

  

[![](https://1.bp.blogspot.com/-PKqBxakWlZg/WjFpxkmJJhI/AAAAAAAALQg/5Ixn6sZh-dwnPeqz__9Xku4b-Bz9bGyjwCLcBGAs/s320/Screenshot%2B2017-12-13%2B12.51.42.png)](https://1.bp.blogspot.com/-PKqBxakWlZg/WjFpxkmJJhI/AAAAAAAALQg/5Ixn6sZh-dwnPeqz__9Xku4b-Bz9bGyjwCLcBGAs/s1600/Screenshot%2B2017-12-13%2B12.51.42.png)

### Idea

_setInterval()_ establece un llamado, cada 1000 ms, a _doPing()_, que hace un ping al host que se haya indicado y revisa si hay un cambio de estado.

  

Si hay un cambio de estado, anota el tiempo y muestra las diferencias respecto al tiempo anterior.

  

Si no hay cambio de estado, imprime simplemente un punto.

_*Url archivado: [Test de internet con ping en NodeJS](https://akcdev.blogspot.com/2017/12/test-de-internet-con-ping-en-nodejs.html)*_
