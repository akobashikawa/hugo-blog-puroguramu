---
title: 'Usando FiraCode en Atom en Ubuntu'
date: 2016-07-15T14:57:00.000-05:00
draft: false
url: /2016/07/usando-firacode-en-atom-en-ubuntu
tags: 
- linux
- editor
- atom
- blogger
---

[![](https://1.bp.blogspot.com/-HJMDlkyrOHU/V4k_2SGi2mI/AAAAAAAAFHs/u0K3UvlsLQMBq-d37Kd1Scnu6-uOVZfQACLcB/s400/fira_code_logo.png)](https://1.bp.blogspot.com/-HJMDlkyrOHU/V4k_2SGi2mI/AAAAAAAAFHs/u0K3UvlsLQMBq-d37Kd1Scnu6-uOVZfQACLcB/s1600/fira_code_logo.png)

  

[FiraCode](https://github.com/tonsky/FiraCode) es un font que soporta ligaduras para algunos símbolos que se suelen usar en programación, haciéndolos más fáciles de leer.  
  
[https://github.com/tonsky/FiraCode](https://github.com/tonsky/FiraCode)  
  
Para usarlo en Atom (en Ubuntu 14.04):  
  

*   Descargar las fuentes: [https://github.com/tonsky/FiraCode/releases/download/1.102/FiraCode\_1.102.zip](https://github.com/tonsky/FiraCode/releases/download/1.102/FiraCode_1.102.zip)
*   Instalar las fuentes. Un modo es:

*   Copiar las fuentes en ~/.local/share/fonts
*   $ fc-cache -f

*   Usar las fuentes en el editor:

*   Menú, Packages, Settings View, Open
*   Editor Settings, Font Family: Fira Code

*   Declarar el uso de ligaduras:

*   Abrir ~/.atom/styles.less:

```
atom-text-editor {  
  ...  
  text-rendering: optimizeLegibility;  
}  

```

  
Y para prevenir que se hagan ligaduras dentro de cadenas o expresiones regulares:  
  

```
atom-text-editor::shadow .string.quoted,  
atom-text-editor::shadow .string.regexp {  
  -webkit-font-feature-settings: "liga" off, "calt" off;  
}  

```

#### Referencias:

*   [https://github.com/tonsky/FiraCode/wiki/Atom-instructions](https://github.com/tonsky/FiraCode/wiki/Atom-instructions)
*   [https://github.com/tonsky/FiraCode/wiki/Linux-instructions](https://github.com/tonsky/FiraCode/wiki/Linux-instructions)

_*Url archivado: [Usando FiraCode en Atom en Ubuntu](https://akcdev.blogspot.com/2016/07/usando-firacode-en-atom-en-ubuntu.html)*_
