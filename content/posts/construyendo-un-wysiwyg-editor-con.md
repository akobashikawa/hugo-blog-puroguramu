---
title: 'Construyendo un Wysiwyg Editor con jQuery'
date: 2011-10-28T18:00:00.000-05:00
draft: false
url: /2011/10/construyendo-un-wysiwyg-editor-con
tags: 
- jquery
- javascript
- web
- blogger
---

[![](http://4.bp.blogspot.com/-1HqO8qW939Q/TJPfxG0QArI/AAAAAAAABNM/gcxnjPQOroM/s1600/jquery-logo.png)](http://4.bp.blogspot.com/-1HqO8qW939Q/TJPfxG0QArI/AAAAAAAABNM/gcxnjPQOroM/s1600/jquery-logo.png)

En HTML, normalmente un textarea no es wysiwyg, pero existen plugins javascript, como [CKEditor](http://ckeditor.com/), [NicEdit](http://nicedit.com/), entre otros, que ayudan a que lo sea. Se instala el plugin, se configura y listo. ¿Te animarías a hacerlo tú mismo?  
  
WYSIWYG  
_**W**hay **Y**ou **S**ee **I**s **W**hat **Y**ou **G**et_: lo que ves es lo que obtienes  
Así es como se denomina a los editores que muestran la apariencia final del documento mientras es editado.  
  
Buscando hacerme una herramienta para tomar notas con más facilidad, entré a explorar en este tema.  
  
Antes, estaba envuelto por un halo misterioso. Suponía que sería una cuestión demasiado complicada. Descubrí que es más fácil de lo que parece.  
  
Antes, para hacer editable un **div**, lo que se me ocurría era montar encima un elemento editable, como un **input text**, que se muestre cuando se necesite la edición. Pero, limitándome a eso, no veía cómo era posible mostrar en negrita o cursiva algo dentro de un elemento editable. Imaginaba que tendría que ver con algún tipo de magia desconocida que involucraría código muy complejo y sofisticado.  
  
Resulta que es posible hacer que un **div** sea editable (¿por qué no difunden más esas cosas?).  
  
Cuando un **div** es editable, está disponible un API que permite ejecutar comandos sobre su contenido (!).  
  
De ese modo, hacer un editor wysiwyg se convierte en una cuestión muy, muy accesible, incluso para un programador como yo :-)  
  
designMode  
Al parecer, IE fue el que primero implementó la idea de que un elemento fuera editable, luego los otros navegadores acogieron la idea y ahora ya es algo estándar.  
  
Esto se consigue haciendo que **designMode="On"** para el objeto que se desea editar.  
  
Cuando se está en designMode="On", se pueden enviar comandos de formato usando la función execCommand. Estos permanecen activos hasta que se vuelven a enviar otra vez. O se aplican sobre el texto que estuviera seleccionado. Sí, como en Word. Hasta funciona deshacer con CTRL+Z  
  
La idea básica  
Una de las primeras guías que encontré usa un iframe y botones.  
  
Pone el iframe en designMode="On". Hecho esto, se puede editar el contenido del iframe como si se estuviera en un textarea.  
  
Los botones permiten invocar los comandos de formato.  
  
Este es un ejemplo basado en: [http://jsfiddle.net/Kxmaf/6/](http://jsfiddle.net/Kxmaf/6/) :  
  
```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">  
<html lang="en">  
<head>  
<meta http-equiv="Content-Type" content="text/html;charset=UTF-8">  
<title>WYSIWYG Demo</title>  
  
<script type="text/javascript" src="js/jquery-1.6.4.min.js"></script>  
  
<style type="text/css">  
input\[type=button\] {  
  border: 1px solid #ccc;  
}  
#editor {  
  width: 500px;  
  height: 170px;  
}  
#bold {  
  font-weight: bold;  
}  
#italic {  
  font-style: italic;  
}  
</style>  
  
<script type="text/javascript">  
$(document).ready(function() {  
  var cw = document.getElementById('editor').contentWindow;  
  var doc = cw.document;  
  doc.designMode = "on";  
  doc.write('');  
  doc.close();  
    
  $('#bold').click(function() {  
    cw.focus();// IE  
    doc.execCommand('bold', false, false);  
    cw.focus();  
  });  
  $('#italic').click(function() {  
    cw.focus();// IE  
    doc.execCommand('italic', false, false);  
    cw.focus();  
  });  
  $('#fontname').change(function() {  
    cw.focus();// IE  
    doc.execCommand('fontname', false, $(this).val());  
    cw.focus();  
  });  
});  
</script>  
  
</head>  
<body>  
  <h1>WYSIWYG Demo</h1>  
    
  <div id="buttons">  
    <input type="button" id="bold" value="B" />  
    <input type="button" id="italic" value="I" />  
    <select id="fontname">  
      <option value="Arial">Arial</option>  
      <option value="Comic Sans MS">Comic Sans MS</option>  
      <option value="Courier New">Courier New</option>  
      <option value="Monotype Corsiva">Monotype</option>  
      <option value="Tahoma">Tahoma</option>  
      <option value="Times">Times</option>  
    </select>  
  </div>  
  <iframe id="editor"></iframe>  
    
</body>  
</html>  

```  
Mejorando  
Es posible usar un div en lugar de un iframe. También se puede aprovechar más cosas de jQuery.  
  
Este es un ejemplo basado en [de77: jQuery Simple WYSIWYG Editor](http://de77.com/javascript/jquery-simple-wysiwyg-editor) :  
  
```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">  
<html lang="en">  
<head>  
<meta http-equiv="Content-Type" content="text/html;charset=UTF-8">  
<title>WYSIWYG Demo</title>  
  
<script type="text/javascript" src="js/jquery-1.6.4.min.js"></script>  
  
<style type="text/css">  
input\[type=button\] {  
  border: 1px solid #ccc;  
}  
#editor {  
  width: 500px;  
  height: 170px;  
  border: 1px solid #ccc;  
}  
#bold {  
  font-weight: bold;  
}  
#italic {  
  font-style: italic;  
}  
</style>  
  
<script type="text/javascript">  
  
$(document).ready(function() {  
  function action(a,p) {  
    $('#editor').focus();  
    if (p == null) p = false;  
    document.execCommand(a, null, p);  
  }  
  
  $('#editor').get(0).contentEditable = "true";  
    
  $('#bold').click(function() {  
    action('bold');  
  });  
  $('#italic').click(function() {  
    action('italic');  
  });  
  $('#fontname').change(function() {  
    action('fontname', $(this).val());  
  });  
  $('#html').click(function() {  
    alert($('#editor').html());  
  });  
});  
</script>  
  
</head>  
<body>  
  <h1>WYSIWYG Demo</h1>  
    
  <div id="buttons">  
    <input type="button" id="bold" value="B" />  
    <input type="button" id="italic" value="I" />  
    <select id="fontname">  
      <option value="Arial">Arial</option>  
      <option value="Comic Sans MS">Comic Sans MS</option>  
      <option value="Courier New">Courier New</option>  
      <option value="Monotype Corsiva">Monotype</option>  
      <option value="Tahoma">Tahoma</option>  
      <option value="Times">Times</option>  
    </select>  
    <input type="button" id="html" value="HTML" />  
  </div>  
  <div id="editor"></div>  
    
</body>  
</html>  

```  
Me parece que esto puede ayudar a aclarar el tema para empezar. Ojalá le sirva de ayuda.  
  
Referencias  

*   [Rich-Text Editing in Mozilla](https://developer.mozilla.org/en/rich-text_editing_in_mozilla)
*   [jQuery Simple WYSIWYG Editor](http://de77.com/javascript/jquery-simple-wysiwyg-editor)

_*Url archivado: [Construyendo un Wysiwyg Editor con jQuery](https://akcdev.blogspot.com/2011/10/construyendo-un-wysiwyg-editor-con.html)*_

---
### Comentarios archivados:

>
> muy buen aporte
> \
> [Anónimo](# "noreply@blogger.com") [2012-04-18 09:55]

>
> Muchas gracias, se agradece que compartan estas cosas, lleva ya un tiempo buscando algo asi  
  
Saludos
> \
> [Cristofer](https://www.blogger.com/profile/11869080319704281591 "noreply@blogger.com") [2013-03-05 21:41]

>
> Muchas gracias, me viene genial. Muy buen aporte :)
> \
> [albertoi](https://www.blogger.com/profile/03255111440707905074 "noreply@blogger.com") [2013-07-01 09:55]

>
> Muchas gracias, muy muy util!!! Estaba buscando algo casi identico a lo que muestras para de alli partir y crear yo mismo mi WysiWyg
> \
> [isosa](https://www.blogger.com/profile/05925200702407165950 "noreply@blogger.com") [2014-06-17 23:41]

>
> Me alegra, buena suerte :-)
> \
> [Rulo Kobashikawa](https://www.blogger.com/profile/07020497448167262255 "noreply@blogger.com") [2014-06-20 16:40]
