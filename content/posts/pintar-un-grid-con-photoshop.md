---
title: 'Pintar un grid con Photoshop'
date: 2011-01-03T10:20:00.002-05:00
draft: false
url: /2011/01/pintar-un-grid-con-photoshop
tags: 
- gráficos
- photoshop
- blogger
---

[![](https://2.bp.blogspot.com/_K2xwnQ4Llso/TSHptmCRWCI/AAAAAAAABPs/h3_1N5t3j4k/s1600/photoshop-grid.png)](https://2.bp.blogspot.com/_K2xwnQ4Llso/TSHptmCRWCI/AAAAAAAABPs/h3_1N5t3j4k/s1600/photoshop-grid.png)

1  
Definir el patrón del grid.  
Por ejemplo, para un grid de 100x100 se puede crear un nuevo documento, de 100x100 pixels. Luego hacer doble click en el layer Background (para desbloquearlo y se llame Layer 0). Después hacer doble click en el layer Layer 0 (para entrar a Layer Style) y allí elegir el estilo Stroke, Position: Center, Size: 1px.  
Finalmente, Menú, Edit, Define pattern..., y dar un nombre, por ejemplo, _Grid100x100_.  
  
2  
Aplicar el patrón.  
Abrir la imagen sobre la que se quiere pintar el grid. Ir a Channels, agregar un nuevo canal. Puede cambiarle el nombre (por default Alpha 1) a algo como _Grid_.  
Seleccionar el canal y rellenarlo con el patrón: Menú, Edit, Fill..., Contents {Use: Pattern, elegir el patrón previamente definido}. Volver a seleccionar todos los canales que se hubieran deseleccionado.  
Volver a Layers y agregar una nueva capa para pintar el grid. Se pintará usando una selección como máscara: Menú, Select, Load selection..., Source {Channel: Grid100x100}. Puede aprovechar y elegir Invert de una vez (para invertir la selección), o hacerlo en un siguiente paso (Menú, Select, Inverse).  
Colorear la seleccion. Una forma es usando ALT+BACKSPACE. Otra forma es Menú, Edit, Fill..., Contents {Use: Color, elegir un color}.  
  
**Referencias**  

*   [How to create a grid quickly and easily with Photoshop](http://www.bolducpress.com/tutorials/how-to-create-a-grid-quickly-and-easily-with-photoshop/)

_*Url archivado: [Pintar un grid con Photoshop](https://akcdev.blogspot.com/2011/01/pintar-un-grid-con-photoshop.html)*_
