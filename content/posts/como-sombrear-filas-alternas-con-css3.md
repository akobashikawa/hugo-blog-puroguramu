---
title: 'Cómo sombrear filas alternas con CSS3'
date: 2011-04-23T11:47:00.003-05:00
draft: false
url: /2011/04/como-sombrear-filas-alternas-con-css3
tags: 
- css
- blogger
---

A esta forma de presentar filas se le suele llamar cebra.  
  
**Caso Tabla**  

[![](http://2.bp.blogspot.com/-wCaJOl-tDdc/TbMHzuF-gKI/AAAAAAAABUo/hT5OSXrRZaY/s1600/zebra-table.png)](http://2.bp.blogspot.com/-wCaJOl-tDdc/TbMHzuF-gKI/AAAAAAAABUo/hT5OSXrRZaY/s1600/zebra-table.png)

  
**HTML**  
```
<table class="zebra">  
  <thead>  
    <tr>  
      <th>Col0</th>  
      <th>Col1</th>  
      <th>Col2</th>  
    </tr>  
  </thead>  
  <tbody>  
    <tr>  
      <td>Item</td>  
      <td>Item</td>  
      <td>Item</td>  
    </tr>  
    <tr>  
      <td>Item</td>  
      <td>Item</td>  
      <td>Item</td>  
    </tr>  
    <tr>  
      <td>Item</td>  
      <td>Item</td>  
      <td>Item</td>  
    </tr>  
  </tbody>  
</table>  

```  
**CSS**  
```
table.zebra tbody tr:nth-child(2n+1) {  
  background-color: #eef;  
}  

```  
Normalmente, las tablas presentan sus celdas con un borde. Para ocultarlo, se puede usar el atributo html border="0". Sin embargo, también se puede hacer usando estilos, con algo como:  
  
```
table.zebra {  
  border-collapse: collapse;  
  border-spacing: 0;  
}  

```  
**Caso Lista**  

[![](http://2.bp.blogspot.com/-YtxG-MZiw5Y/TbMIAXy9llI/AAAAAAAABUs/5T-rZUZMAKs/s1600/zebra-list.png)](http://2.bp.blogspot.com/-YtxG-MZiw5Y/TbMIAXy9llI/AAAAAAAABUs/5T-rZUZMAKs/s1600/zebra-list.png)

  
**HTML**  
```
<ul class="zebra">  
  <li>Item 1</li>  
  <li>Item 2</li>  
  <li>Item 3</li>  
</ul>  

```  
**CSS**  
```
ul.zebra li:nth-child(2n+1) {  
  background-color: #eef;  
}  

```  
Normalmente, las listas presentan sus filas con un bullet. Para ocultarlo, se puede usar estilos, con algo como:  
  
```
ul.zebra {  
  list-style: none;  
  padding: 0;  
}  

```

_*Url archivado: [Cómo sombrear filas alternas con CSS3](https://akcdev.blogspot.com/2011/04/como-sombrear-filas-alternas-con-css3.html)*_

---
### Comentarios archivados:

>
> Un excelente aporte BOY sigue asi
> \
> [Anónimo](# "noreply@blogger.com") [2013-01-11 13:38]
