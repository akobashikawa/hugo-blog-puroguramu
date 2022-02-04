---
title: '.htaccess para proteger index.html'
date: 2011-04-27T12:41:00.002-05:00
draft: false
url: /2011/04/htaccess-para-proteger-indexhtml
tags: 
- apache
- html
- blogger
---

[![](https://4.bp.blogspot.com/-mnivdaPjRtA/TbhUfnjv1hI/AAAAAAAABU4/VJK3xW-jwBg/s1600/Lock+file+Icon.jpg)](https://4.bp.blogspot.com/-mnivdaPjRtA/TbhUfnjv1hI/AAAAAAAABU4/VJK3xW-jwBg/s1600/Lock+file+Icon.jpg)

Se puede usar .htaccess para proteger el acceso a un determinado archivo en un directorio. En este caso, se desea proteger el acceso a http://example.com/protegido/  
  
**.htaccess**  
En el directorio que contiene a **index.html**:  
  
```
<FilesMatch index.html>  
AuthUserFile /var/www/.htpasswd  
AuthType Basic  
AuthName "Pagina Privada"  
Require valid-user  
</FilesMatch>  

```  
**.htpasswd**  
`/var/www/.htpasswd` se puede crear usando el comando _htpasswd_:  
  
```
cd /var/www  
htpasswd -c .htpasswd uuu  

```  
Donde _uuu_ es el nombre del usuario al que se quiere dar acceso a ese directorio.  
  
**Files o FilesMatch**  
Inicialmente habia usado **Files** en lugar de **FilesMatch,** perome permitía entrar al directorio omitiendo **index.html** en el url.  
  
Por ejemplo, si el url era:  
  
```
http://example.com/protegido/index.html  

```  
Podía entrar con:  
  
```
http://example.com/protegido/  

```  
En cambio, con **FilesMatch** se protegieron ambos accesos.

_*Url archivado: [.htaccess para proteger index.html](https://akcdev.blogspot.com/2011/04/htaccess-para-proteger-indexhtml.html)*_
