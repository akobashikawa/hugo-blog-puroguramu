---
title: 'Resolviendo keys para Putty SSH a Hostmonster'
date: 2011-02-17T01:32:00.004-05:00
draft: false
url: /2011/02/resolviendo-keys-para-putty-ssh
tags: 
- ssh
- blogger
---

[![](https://2.bp.blogspot.com/-K27t373uf-0/TVzEPyXZT1I/AAAAAAAABRQ/XoSLwFOuDCU/s200/success-blogging-keys.jpg)](https://2.bp.blogspot.com/-K27t373uf-0/TVzEPyXZT1I/AAAAAAAABRQ/XoSLwFOuDCU/s1600/success-blogging-keys.jpg)

Hoy he pasado algunas horas resolviendo este tema.  
  
**ssh** genera dos llaves (por ejemplo **_id\_dsa_** -la privada-, e **_id\_dsa.pub_** -la pública-).  
  
Se pueden generar con alguno de los comandos:  
  
```
ssh-keygen -t **dsa**  
  
ssh-keygen -t **rsa**  

```  
Según el tipo que se desee.  
  
**Hostmonster** también tiene un generador de llaves (al parecer ssh) que puede producir archivos similares.  
  
Uno puede producir llaves de diverso tipo (dsa, rsa), con o sin password.  
  
```
\[ssh\]----> id\_dsa     (llave privada)  
       +-> id\_dsa.pub (llave pública)  
  
\[ssh\]----> id\_rsa     (llave privada)  
       +-> id\_rsa.pub (llave pública)  

```  
Los nombres pueden ser id\_dsa, id\_rsa, u otro cualquiera. Por ejemplo, yo estuve practicando con _kobaonli\_id\_dsa_, _hp\_id\_dsa_.  
  
**Putty** es un programa que permite hacer conexiones SSH usando estas llaves (_Connection/SSH/Auth_).  
Pero no puede usar las llaves privadas así generadas, requiere que antes sean convertidas a **.ppk**, con un programa como **puttygen**.  
  
Puttygen tiene la opción _Conversions/Import_ que permite importar una llave privada generada con ssh (u OpenSSH) y generar el **.ppk** correspondiente.  
Sin embargo, tuve problemas para que puttygen (versión 0.60) reconociera llaves privadas que tuvieran password, así que generé llaves sin password.  
  
```
\[ssh\]----> id\_dsa ----\[puttygen\]----> id\_dsa.ppk  
       +-> id\_dsa.pub  
  
\[ssh\]----> id\_rsa ----\[puttygen\]----> id\_rsa.ppk  
       +-> id\_rsa.pub  

```  
Así que, en resúmen:  
  
**A) Usando llaves locales**  
  
\- Usé **ssh-keygen -t dsa** para crear **_hp\_id\_dsa/hp\_id\_dsa.pub_**, sin password.  
\- Usé **puttygen** para importar **_hp\_id\_dsa_** y crear **_hp\_id\_dsa.ppk_**, sin password.  
\- En **Hostmonster**, _CPanel, SSH/Shell Access, Manage SSH Keys_, importé **_hp\_id\_dsa/hp\_id\_dsa.pub_** y luego en _Manage Authorization_ autoricé su uso.  
\- Indiqué a **putty** que usara **_hp\_id\_dsa.ppk_** para el _SSH/Auth_.  
\- Me pude conectar a **Hostmonster** usando las llaves **_hp\_id\_dsa\[.ppk\]/hp\_id\_dsa.pub_**  
  
```
\[ssh\]----> hp\_id\_dsa ----\[puttygen\]----> hp\_id\_dsa.ppk  
       +-> hp\_id\_dsa.pub  
           |  
           v  
          \[hostmonster\]  

```  
**B) Usando llaves remotas**  
  
\- En **Hostmonster**, _CPanel, SSH/Shell Access, Manage SSH Keys_, creé **_kobaonli\_id\_dsa/kobaonli\_id\_dsa.pub_**, sin password. Descargué la llave privada **_kobaonli\_id\_dsa_** a mi **PC**.  
\- Usé **puttygen** para importar **_kobaonli\_id\_dsa_** y crear **_kobaonli\_id\_dsa.ppk_**, sin password.  
\- Indiqué a **putty** que usara **_kobaonli\_id\_dsa.ppk_** para el _SSH/Auth_.  
\- Me pude conectar a **Hostmonster** usando las llaves **_kobaonli\_id\_dsa\[.ppk\]/kobaonli\_id\_dsa.pub_**  
  
```
\[hostmonster\]----> hp\_id\_dsa ---->\[pc\]----\[puttygen\]----> hp\_id\_dsa.ppk  
               +-> hp\_id\_dsa.pub  

```  
**Referencias**  

*   _[Hostmonster Helpdesk: SSH Access - Generating a Public/Private Key](https://www.hostmonster.com/cgi/help/555)_
*   _Crédito de la imágen: [https://internetmarketingstrategydiva.com/wp-content/uploads/2009/12/success-blogging-keys.jpg](https://internetmarketingstrategydiva.com/wp-content/uploads/2009/12/success-blogging-keys.jpg)_

_*Url archivado: [Resolviendo keys para Putty SSH a Hostmonster](https://akcdev.blogspot.com/2011/02/resolviendo-keys-para-putty-ssh.html)*_
