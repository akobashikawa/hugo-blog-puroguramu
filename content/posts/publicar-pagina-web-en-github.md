---
title: 'Publicar página web en GitHub'
date: 2012-05-28T17:16:00.000-05:00
draft: false
url: /2012/05/publicar-pagina-web-en-github
tags: 
- html
- git
- web
- blogger
---

[![](https://1.bp.blogspot.com/-a7cNsbirwBg/T2y7Uc63f_I/AAAAAAAAByI/eiWBgq8ucVI/s200/git-logo.png)](https://1.bp.blogspot.com/-a7cNsbirwBg/T2y7Uc63f_I/AAAAAAAAByI/eiWBgq8ucVI/s1600/git-logo.png)

Es posible usar GitHub para publicar una página web estática.  
  
Por ejemplo, para un portafolio. A continuación, como empezar con el index.html.  
  

*   Siendo usuario de GitHub, crear el repositorio portafolio. Elegir que cree el README.
*   Clonar el repositorio: git clone git@github.com:myusername/portafolio.git
*   Crear el branch gh-pages: git checkout -b gh-pages
*   Crear index.html y agregarlo: git add .
*   Commit: git commit -am "created index.html"
*   Push: git push origin gh-pages
*   Revisar http://myusername.github.com/portafolio/

_*Url archivado: [Publicar página web en GitHub](https://akcdev.blogspot.com/2012/05/publicar-pagina-web-en-github.html)*_
