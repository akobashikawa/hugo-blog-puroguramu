---
title: 'Copia en Linux convirtiendo symlinks'
date: 2011-06-14T13:34:00.000-05:00
draft: false
url: /2011/06/copia-en-linux-convirtiendo-symlinks
tags: 
- linux
- blogger
---

[![](http://4.bp.blogspot.com/-KmhYf9ZalO4/TUwhyQVJXyI/AAAAAAAABQ8/GpJ-i1hu6wo/s1600/tux-100.png)](http://4.bp.blogspot.com/-KmhYf9ZalO4/TUwhyQVJXyI/AAAAAAAABQ8/GpJ-i1hu6wo/s1600/tux-100.png)

En Linux, para copiar un directorio completo, se puede usar algo como:  
  
```
cp -a origen destino
```  
Si origen tuviera symlinks (enlaces simbólicos), estos se copiarían tal cual.  
  
Si se desea que los symlinks se conviertan en los archivos a los cuales apuntan:  
  
```
cp -aL origen destino
```  
Esto parece que no esta muy documentado. Ojalá le sea de ayuda.

_*Url archivado: [Copia en Linux convirtiendo symlinks](https://akcdev.blogspot.com/2011/06/copia-en-linux-convirtiendo-symlinks.html)*_
