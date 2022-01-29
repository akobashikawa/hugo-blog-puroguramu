---
title: 'Un background con inline css es contenido funcional'
date: 2014-04-24T18:10:00.003-05:00
draft: false
url: /2014/04/se-prefiere-que-en-el-html-este-el
tags: 
- css
- html
- blogger
---

Se prefiere que en el HTML esté el contenido y en el CSS la presentación.  
  
De ese modo, viven independientes. Es posible cambiar el .css por otro y dar un aspecto totalmente nuevo a la página.  
  
Una imagen en background se considera presentación. No le corresponde un tag ni un nodo de texto. Pero quizás se pueda hablar de **contenido funcional**.  
  
Una imagen que es contenido:  
  
**index.html**  
```
<div class="foto"> <img src="imagen.jpeg" /> </div>  

```  
Si ahora pusiera la imagen como background definido en CSS:  
  
**style.css**  
```
.foto {  
 background: url('imagen.jpg') no-repeat;  
}  

```  
**index.html**  
```
<div class="foto"> </div>  

```  
Al hacer eso, imagen.jpg deja de ser contenido y pasa a ser presentación.  
  
Pero, si el css no estuviera en un archivo aparte, sino inline:  
  
**index.html**  
```
<div class="foto" style="background: url('imagen.jpg') no-repeat;"> </div>  

```  
Entonces, imagen.jpg se podría considerar como contenido.  
  
Cierto que está definido usando CSS, pero es inline, está pegado al HTML y en el flujo de trabajo se puede tratar de modo similar a un img. Es como si fuera contenido.  
  
Estas serían formas de definir contenido de manera no tradicional:  

*   Usando **background** en inline css
*   Usando un **inline script**  
    ```
    <div class="texto"><script>document.write('Hola Mundo!');</script></div>
    ```

_*Url archivado: [Un background con inline css es contenido funcional](https://akcdev.blogspot.com/2014/04/se-prefiere-que-en-el-html-este-el.html)*_
