---
title: 'Gource para verte mejor'
date: 2014-12-01T18:11:00.001-05:00
draft: false
url: /2014/12/gource-para-verte-mejor
tags: 
- git
- blogger
---

  
  
Gource es una herramienta de google para visualizar como video la evolución de un repositorio.  
  
Lo he probado en una Mac, instalado previamente gource y ffmpeg via Homebrew.  
```
  
brew install gource  
brew install ffmpeg  

```  
Colocarse en el directorio del repo y ejecutar:  
  
```
gource \-1280x720  \-o \-  | ffmpeg \-y \-r 60  \-f image2pipe \-vcodec ppm \-i \-  \-vcodec libx264 \-preset ultrafast \-pix\_fmt yuv420p \-crf 1  \-threads 0  \-bf 0 gource.mp4
```  
Para más información: [https://code.google.com/p/gource/wiki/Videos](https://code.google.com/p/gource/wiki/Videos)

_*Url archivado: [Gource para verte mejor](https://akcdev.blogspot.com/2014/12/gource-para-verte-mejor.html)*_
