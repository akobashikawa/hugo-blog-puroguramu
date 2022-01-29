---
title: 'Git: Un Cuento de Tres árboles'
date: 2014-06-07T12:00:00.001-05:00
draft: false
url: /2014/06/git-un-cuento-de-tres-arboles
tags: 
- programación
- git
- agil
- blogger
---

[![](http://1.bp.blogspot.com/-a7cNsbirwBg/T2y7Uc63f_I/AAAAAAAAByI/eiWBgq8ucVI/s1600/git-logo.png)](http://1.bp.blogspot.com/-a7cNsbirwBg/T2y7Uc63f_I/AAAAAAAAByI/eiWBgq8ucVI/s1600/git-logo.png)

Hoy vi una presentación muy iluminadora sobre git, Un Cuento de Tres árboles, por Scott Chacon:  
  

*   [http://www.slideshare.net/startechconf/scott-chacon-cuento-de-tres-rboles](http://www.slideshare.net/startechconf/scott-chacon-cuento-de-tres-rboles)
*   [http://vimeo.com/38958167](http://vimeo.com/38958167)

ARCHIVOS: Es el árbol donde hacemos nuestros cambios

STAGE: Es el árbol intermedio, nuestro futuro commit

HEAD: Es el árbol del commit más reciente

### Hacer

vim file.txt

  creo file.txt en ARCHIVOS

  

git add file.txt

  agrega file.txt al STAGE

  

git commit

  crea un nuevo commit con lo que esté en STAGE y lo hace HEAD

### Deshacer

git reset --soft HEAD~

  deshace el último movimiento del HEAD

  

git reset HEAD~

  deshace el último movimiento del HEAD y copia el commit apuntado al STAGE

  

git reset --hard HEAD~

  deshace el último movimiento del HEAD, copia el commit apuntado al STAGE y también a ARCHIVOS

### Diferencias

git diff

  muestra las diferencias de ARCHIVOS con STAGE

  

git diff HEAD

  muestra las diferencias de ARCHIVOS con HEAD

  

git diff --cached

  muestra las diferencias de STAGE con HEAD

### Ver

cat file.txt

  muestra el contenido del archivo en ARCHIVOS

  

git show :0:file.txt

  muestra el contenido del archivo en STAGE

  

git show HEAD:file.txt

  muestra el contenido del archivo en HEAD  
  
_**Fuente original:** [http://akcaprendiendo.blogspot.com/2014/06/git-un-cuento-de-tres-arboles.html](http://akcaprendiendo.blogspot.com/2014/06/git-un-cuento-de-tres-arboles.html)_

_*Url archivado: [Git: Un Cuento de Tres árboles](https://akcdev.blogspot.com/2014/06/git-un-cuento-de-tres-arboles.html)*_
