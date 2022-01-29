---
title: 'Un mapa con Raphael'
date: 2010-08-27T00:17:00.008-05:00
draft: false
url: /2010/08/un-mapa-con-raphael
tags: 
- gráficos
- javascript
- blogger
---

[![](http://3.bp.blogspot.com/_K2xwnQ4Llso/THdVyweqr6I/AAAAAAAABLc/BSf1k8xASfE/s200/Raphael_1.jpg)](http://3.bp.blogspot.com/_K2xwnQ4Llso/THdVyweqr6I/AAAAAAAABLc/BSf1k8xASfE/s1600/Raphael_1.jpg)

[Raphäel](http://raphaeljs.com/) es una biblioteca javascript que permite incorporar a la página imágenes vectoriales.  

Píxeles y vectores
------------------

A diferencia de una fotografía formada por pixeles, una imagen vectorial está determinada por vectores. Mientras que hay que guardar la información de cada pixel, en el caso de los vectores sólo hay que guardar la información de sus extremos o puntos notables; los demás serán calculados a partir de ellos.  
  
Eso permite que una imagen vectorial ocupe, en general, mucho menos espacio en disco que una imagen fotográfica. Además, se escala y siempre está nítida. No ocurre el 'pixeleo' que se suele notar en las fotos cuando se fuerza una ampliación.  
  
Esas características hacen que sean una opción atractiva para gráficos web. Flash, por ejemplo, usa imágenes vectoriales.  

SVG
---

SVG es un estándar XML para imágenes vectoriales en web. Raphael se apoya príncipalmente en ese estandar, de modo que cada elemento gráfico sea parte del DOM (el árbol XML que representa la página web), y provee adaptadores para compatibilidad entre navegadores (todavía no todos los navegadores soportan SVG del mismo modo).  
  
El que un elemento gráfico sea parte del DOM permite manipularlo con javascript.  
  

Usando Raphael
--------------

¿Qué tan fácil de usar es Raphael? Bueno, la entrada me pareció relativamente sencilla. Declarar la biblioteca raphael.js, un canvas y luego crear elementos gráficos como rectángulos, círculos, etc.  
...  
  <script type="text/javascript" src="js/jquery-1.4.2.min.js"></script>  

  <script type="text/javascript" src="js/raphael-min.js"></script>

  <script type="text/javascript">

    $(function() {

      var paper = Raphael('canvas', 800, 600);

      var circle = paper.circle(150, 150, 100);

      var circle2 = paper.circle(150, 450, 100);

      var ellipse = paper.ellipse(150, 150, 100, 50);

      var ellipse2 = paper.ellipse(150, 150, 50, 100);

      var ellipse3 = paper.ellipse(350, 350, 50, 100);

      var rect = paper.rect(0, 0, 800, 600);

      var rect2 = paper.rect(50, 50, 200, 200);

      var rect3 = paper.rect(270, 50, 200, 200, 20);

      var image = paper.image('images/bee.jpg', 490, 50, 100, 75);

      var set = paper.set();

      set.push(circle, rect3);

      set.attr({fill: "gold"});

      var text = paper.text(150, 280, 'Hello World!\\nLos niños de Andalucía');

      var path = paper.path("M50 50L250 250");

      var path2 = paper.path("M250 50L50 250");

      //paper.clear();

      circle.paper.path("M10,10L50,50M50,10L10,50")

        .attr({stroke: "red"});

      ellipse2.remove();

      ellipse2.show(); // not show because previous remove

      ellipse.hide();

      ellipse.show();

      rect3.rotate(10);

      image.rotate(80, 490, 50);

      image.translate(100, 0);

      image.scale(1.1, 1.1);

      image.animate({'translation':'-100, 10'}, 1000, 'bounce');

      circle2.animate({

        "20%": {cx: 20, r: 20, easing: ">"},

        "50%": {cx: 70, r: 120, callback: function () {}},

        "100%": {cx: 10, r: 10}

      }, 2000);

      var c = paper.circle(200, 200, 50),

        r = paper.rect(200, 200, 50, 50);

      c.animate({cx: 20, r: 20}, 2000);

      r.animateWith(c, {x: 20}, 2000);

      var path3 = paper.path("M300,300c0,100 100-100 100,0c0,100 -100-100 -100,0z");

      var spot = paper.circle(300, 300, 4).attr({fill: 'red'});

      spot.animateAlong(path3, 4000);

    }

  </script>

  ...

  <div id="canvas"></div>

  ...

El paso siguiente, la interactividad y el manejo de eventos sí me pareció más complicado:  
...  
  circle.drag(  
    function(dx, dy) {// move  
      this.attr({cx: this.ox + dx, cy: this.oy + dy, opacity: .5});  
    },  
    function() {// start  
      this.ox = this.attr("cx");  
      this.oy = this.attr("cy");  
      this.attr({opacity: .5});  
    },  
    function() {// up  
      this.attr({opacity: 1});  
    }  
  );  
...  
La propiedad .node permite manipular un elemento con jQuery. Sin embargo, tardé un poco en comprender que es mejor usar las funciones de manejo de eventos que provee Raphael, al menos para los gráficos. Resulta más simple y claro.  
  
En el caso del drag, notar que se requieren tres funciones, que definen las acciones para move, start y up (en ese orden). La función que corresponde a move tiene los parámetros dx y dy (los diferenciales de movimiento), y la que corresponde a start tiene los parámetros ox y oy (el punto donde se hace click). Mientras se arrastra el objeto, dx y dy crecen contínuamente, así que implementar el drag no es tan simple como hacer un translate(dx, dy) (hacerlo provoca un desconcertante efecto acelerado), sino que hay que reflexionar un poco, como en el ejemplo, que los suma a la posición inicial.  
  
Para el ejemplo del mapa, tardé varios días en descubrir el modo de usar hover y drag para que funcionaran como quería.

El mapa
-------

[![](http://1.bp.blogspot.com/_K2xwnQ4Llso/THdW3rmxIoI/AAAAAAAABLk/aQLK1BnMGQE/s320/mapa_raphael.png)](http://1.bp.blogspot.com/_K2xwnQ4Llso/THdW3rmxIoI/AAAAAAAABLk/aQLK1BnMGQE/s1600/mapa_raphael.png)

  
La idea es tener el mapa del Perú con sus departamentos, y que estos se resalten al pasar el mouse sobre ellos. Al hacer click en alguno, se dispara alguna acción, por ejemplo mostrar su nombre en una caja.  

  

Puede ver el demo [aquí](https://akobashikawa.github.io/mapa-puzzle/), y descargar el código fuente del proyecto en GitHub [aquí](https://github.com/akobashikawa/mapa-puzzle).

  
Raphael se puede usar sólo, pero es de ayuda ayuda usar también jquery.  
...  
<style type="text/css">  
  body {  
    background-color: #222;  
    color: white;  
  }  
  #wrapper {  
    \_position: absolute;  
    \_top: 50%;  
  }  
  #container {  
    background-color: black;  
    width: 700px;  
    height: 500px;  
    position: absolute;  
    top: 0; right: 0; bottom: 0; left: 0;  
    margin: auto;  
    overflow: hide;  
    \_position: relative;  
    \_margin: 0 auto;  
    \_top: -50%;  
    \_overflow: none;  
  }  
  .info {  
    display: none;  
    text-align: center;  
    font-family: "Century Gothic", Helvetica, "Bitstream Vera Sans", sans-serif;  
    font-size: 24pt;  
    line-height: 100px;  
  }  
  #infobox {  
    border: 1px solid #ccc;  
    position: absolute;  
    top: 150px;  
    left: 350px;  
    width: 300px;  
    height: 100px;  
    overlay: auto;  
  }  
  #test {  
    display: none;  
    color: #0f0;  
  }  
</style>  
...  
  
<script type="text/javascript">  
  $(function() {  
  
    //http://www.switchonthecode.com/tutorials/xml-parsing-with-jquery  
    $.ajax({  
      type: 'GET',  
      url: 'images/peru-h500.xml',// .svg renamed .xml for IE support  
      dataType: 'xml',  
      success: function(xml) {  
        var r = Raphael('canvas', 700, 500);  
        var map = {};  
        var map\_set = r.set();  
        var active\_fill = 'gold';  
        var active\_stroke = 'white';  
        var normal\_fill = $('body').css('background-color');  
        var normal\_stroke = '#ccc';  
        var active = null;  
  
        $(xml).find('path').each(function() {  
          var id = (String)($(this).attr('id'));  
          var path = (String)($(this).attr('d'));  
          map\[id\] = r.path(path)  
            .attr({fill:normal\_fill, stroke: normal\_stroke})  
            .drag(  
              // dx,dy van incrementandose  
              // aqui calculo el diferencial continuamente  
              function(dx, dy) {// move  
                this.translate(dx-this.dx, dy-this.dy);  
                this.dx = dx;  
                this.dy = dy;  
                //$('#test').html(dx+'--'+dy);  
              },  
              function(ox, oy) {// start  
                //this.ox = ox;  
                //this.oy = oy;  
                this.dx = 0;  
                this.dy = 0;  
                this.toFront();  
                this.attr({opacity: .5});  
                //$('#test').html(ox+'-'+oy);  
              },  
              function() {// up  
                // regresa a la posición original  
                this.translate(-this.dx, -this.dy);  
                this.attr({opacity: 1});  
  
                // Este bloque lo hacia en un .click()  
                // pero mejor aqui para que tambien funcione en IE  
  
  
                // restablecer activo previo  
                if (active) {  
                  active.animate({fill: normal\_fill, stroke: normal\_stroke}, 500, '>');  
                }  
                // activar actual  
                active = this;  
                active.animate({fill: this.color, opacity: 1}, 500, '>');  
  
  
                // ocultar otras info  
                $('.info').hide();  
                // mostrar info actual  
                $('#'+id).show().css('background-color', this.color);  
  
              }  
            )  
            .hover(function() {  
              this.color = Raphael.getColor();  
              if (this!=active) {  
                this.animate({fill: this.color, stroke: active\_stroke}, 500, '>');  
              }  
            }, function() {  
              if (this!=active) {  
                this.animate({fill: normal\_fill, stroke: normal\_stroke}, 500, '>');  
              }  
            })  
          map\_set.push(map\[id\]);  
        });// end each  
      } // end success  
    });  
  
  });  
</script>    
...  
  
<div id="wrapper">  
  <div id="container">  
    <div id="canvas"></div>  
    <div id="test">\[TEST\]</div>  
    <div id="infobox">  
      <div class="info" style="display:block;">Perú</div>  
      <div id="Arequipa" class="info">Arequipa</div>  
      <div id="Ancash" class="info">Ancash</div>  
      <div id="Apurimac" class="info">Apurímac</div>  
      <div id="Ica" class="info">Ica</div>  
      <div id="Lima" class="info">Lima</div>  
      <div id="Ayacucho" class="info">Ayacucho</div>  
      <div id="Piura" class="info">Piura</div>  
      <div id="Lambayeque" class="info">Lambayeque</div>  
      <div id="Tumbes" class="info">Tumbes</div>  
      <div id="Tacna" class="info">Tacna</div>  
      <div id="Puno" class="info">Puno</div>  
      <div id="Huancavelica" class="info">Huancavelica</div>  
      <div id="Cuzco" class="info">Cuzco</div>  
      <div id="Junin" class="info">Junín</div>  
      <div id="Ucayali" class="info">Ucayali</div>  
      <div id="Pasco" class="info">Pasco</div>  
      <div id="Huanuco" class="info">Huánuco</div>  
      <div id="San\_Martin" class="info">San Martín</div>  
      <div id="Cajamarca" class="info">Cajamarca</div>  
      <div id="Amazonas" class="info">Amazonas</div>  
      <div id="La\_Libertad" class="info">La Libertad</div>  
      <div id="Loreto" class="info">Loreto</div>  
      <div id="Moquegua" class="info">Moquegua</div>  
      <div id="Madre\_de\_Dios" class="info">Madre de Dios</div>  
      <div id="Titicaca" class="info">Lago Titicaca</div>  
    </div>  
  </div>  
</div>  

*   En los estilos aparecen #wrapper y #container para la técnica que permite centrar el #container absolutamente en la ventana.
*   También verá un div #test, que uso durante el desarrollo como consola de salida.
*   En un comienzo, copié a mano cada path (el atributo path.d dentro del .svg). Luego me pareció más práctico cargarlos desde un archivo.  
    Aquí los he cargado de un archivo svg externoperu-h500.xml  
    Originalmente se llamaba peru-h500.svg, pero lo renombré cuando descubrí que IE8 no lo procesaba como .svg.
*   El svg base lo obtuve de [Wikipedia](http://en.wikipedia.org/wiki/File:Scalable_Vectorized_Adminstrative_Map_of_Per%C3%BA_JMK.SVG). Luego use [Inkscape](http://www.inkscape.org/) para dejar sólo los paths que necesitaba.  
    También corregí los id de los path para que fueran cadenas sin acentos ni espacios en blanco, ya que los iba a usar como claves de los arrays de propiedades que iba a crear.  
    Algo especialmente complicado en Inkscape fue lograr que desapareciera la transformación translate() para el grupo de paths, y que en su lugar se aplicara a cada valor.  
    Para ser sinceros, no estoy seguro de como lo logré, pero me parece que funcionó cuando desagrupé, seleccioné los paths, y elegí alinearlos respecto a la página (top y left).  
    Previamente, para cambiar el tamaño escalé y para cambiar el tamaño del canvas entré a propiedades del documento, fit.
*   Cuando pruebe el demo, arrastre uno de los departamentos para comprobar el efecto del drag.
*   He probado esta aplicación en FF5 (3.6.8), Chrome 6, y IE8.

Para mí es muy interesante las cosas que se pueden hacer con SVG y con Raphael. Ojalá este material le sirva de ayuda.

_*Url archivado: [Un mapa con Raphael](https://akcdev.blogspot.com/2010/08/un-mapa-con-raphael.html)*_

---
### Comentarios archivados:

>
> Buenas Tardes ,porfavor podrias subir denuevo el archivo peru-h500.xml ,gracias por tu ayuda estare al tanto de tu pronta respuesta
> \
> [Elis](https://www.blogger.com/profile/09734591863174109114 "noreply@blogger.com") [2012-08-09 15:21]

>
> Gracias por la observación. Ya están corregidos los enlaces.  
También hay un juego basado en la idea: [http://rulokc.heliohost.org/games/javascript/mapa-peru/](http://rulokc.heliohost.org/games/javascript/mapa-peru/)
> \
> [Rulo Kobashikawa](https://www.blogger.com/profile/07020497448167262255 "noreply@blogger.com") [2012-08-09 16:38]

>
> Muchas Gracias, estaré revisando la información.
> \
> [Elis](https://www.blogger.com/profile/09734591863174109114 "noreply@blogger.com") [2012-08-09 17:46]

>
> Buen dia,por favor me podrias explicar estas funciones bueno aun no entiendo para que la utilizastes.Gracias  
  
function(dx, dy) {// move  
this.translate(dx-this.dx, dy-this.dy);  
this.dx = dx;  
this.dy = dy;  
//$('#test').html(dx+'--'+dy);  
},  
function(ox, oy) {// start  
//this.ox = ox;  
//this.oy = oy;  
this.dx = 0;  
this.dy = 0;  
this.toFront();  
this.attr({opacity: .5});  
//$('#test').html(ox+'-'+oy);  
},
> \
> [Elis](https://www.blogger.com/profile/09734591863174109114 "noreply@blogger.com") [2012-08-10 09:56]

>
> Hace tiempo que hice el ejemplo, pero veo que son argumentos de la función drag.  
Puedes ver más detalles en la documentación de Raphael al respecto(http://raphaeljs.com/reference.html#Element.drag).  
Cómo los uso aquí puede ayudarte como ejemplo práctico.  
Quizás sea buena idea que trates de modificar las funciones para que veas como reaccionan los elementos.
> \
> [Rulo Kobashikawa](https://www.blogger.com/profile/07020497448167262255 "noreply@blogger.com") [2012-08-10 15:49]

>
> Holas Puroguramu cuando descarague el mapa que hicistes(mapa del peru con fondo negro con rapahael)en mi pc no sale el mapa ,solo sale en firefox pero no en chrome ni en internet,pero lo mas raro ke si carga en la web en los 3 navegadores
> \
> [TEECWEB](https://www.blogger.com/profile/15723288410524719666 "noreply@blogger.com") [2012-11-27 05:28]

>
> Tienes razón, cuando hago doble click al index.html, y Chrome lo abre usando el protocolo file://, el mapa no aparece.  
En cambio, cuando lo publico en web, o con un servidor web local como Xampp, entonces se usa el protocolo http:// y sí aparece el mapa.
> \
> [Rulo Kobashikawa](https://www.blogger.com/profile/07020497448167262255 "noreply@blogger.com") [2012-11-27 11:44]

>
> los links de los archivos estan rotos, por favor podria solucionarlos, es muy importante , gracias
> \
> [Elis](https://www.blogger.com/profile/09734591863174109114 "noreply@blogger.com") [2015-07-29 23:25]

>
> Hola, puse los archivos en un proyecto GitHub (https://github.com/akobashikawa/mapa-puzzle) y ahora los enlaces ya están hábiles.
> \
> [Rulo Kobashikawa](https://www.blogger.com/profile/07020497448167262255 "noreply@blogger.com") [2015-08-02 01:45]
