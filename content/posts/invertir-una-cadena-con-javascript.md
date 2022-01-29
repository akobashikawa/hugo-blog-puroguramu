---
title: 'Invertir una cadena con javascript'
date: 2017-02-17T00:05:00.002-05:00
draft: false
url: /2017/02/invertir-una-cadena-con-javascript
tags: 
- javascript
- blogger
---

¿Cómo harías una función que invirtiera una cadena dada?  
Es decir que f("abcdef") sea "fedcba".
-------------------------------------------------------------------------------------------------

  
Yo pienso que no hay una "forma correcta" de resolverlo. Simplemente hay formas, y cualquiera que se te ocurra y haga el trabajo está bien.  
  
De todas esas formas habrá algunas que logran hacerlo con menos variables o menos código, o usando técnicas esotéricas. Formas optimizadas.  
  
Hay programadores que se familiarizan con esas técnicas optimizadas y las aplican luego directamente en los siguiente problemas que enfrentan. Puede ser impresionante, como cuando ves a un mago sacando del sombrero cosas que no creías posible. Igual que con los magos, se requiere de práctica y ensayo para lograr esas cosas. Pero, igual que con los magos, no significa que esa es la forma en que todo el mundo debería pretender hacer las cosas.  
  
La optimización prematura es la raíz del mal, es la advertencia de Knuth, comprobada una y otra vez en la experiencia de los programadores. Está bien optimizar, por supuesto, pero tiene su momento, y definitivamente no es al inicio.  
  
En la vida real, la solución de los problemas se produce por tanteo. Como en un cuarto oscuro, estiras los brazos y tientas. Tocas algo una y otra vez, formándote una idea de lo que hay. Así, descubres la puerta hacia la solución. Una vez que la descubriste, podrías volver al punto de partida y hacerlo más rápido, en menos tiempo o de manera más elegante. Recién ahí es que se realiza la optimización. Si intentaras salir a toda velocidad al inicio, sería muy probable que te lastimaras con algún obstáculo o fueras rápido en la dirección equivocada. También sería un poco raro hacer movimientos elegantes si ni siquiera sabes a dónde vas a ir.  
  
Así que para este problema, quizás se te podría ocurrir algo como:  
  
```
// recorrer la cadena en reversa  
function f(s) {  
 var result = "";  
 for (var i=s.length; i>0; i--) {  
  result = result + s\[i-1\];  
 }  
 return result;  
}  

```  
Ok, es lo primero que se me ocurrió. Veamos si se puede hacer mejor. Quizás se pueda recorrer la cadena de otro modo:  
  
```
// recorrer la cadena de frente pero acumular en reversa  
function g(s) {  
 var result = "";  
 for (var i=0; i<s.length; i++) {  
  result = s\[i\] + result;  
 }  
 return result;  
}  

```  
¿Y si vemos como luce con **_reduce?_**:  
  
```
// usando reduce y acumulando en reversa  
function h(s) {  
 return s.split("").reduce(function(result, c) {  
  return c + result;  
 });  
}  

```  
¿Y usando la notación **_fat arrow?_**:  
  
```
// usando reduce y fat arrow  
function j(s) {  
 return s.split("").reduce((result, c) => c + result);  
}  

```  
Quizás con la práctica sea esta forma la que aparezca primero en tu cabeza en el futuro. Podría ser impresionante. Pero hay que recordar que las cosas empiezan tanteando. Y que está bien.

_*Url archivado: [Invertir una cadena con javascript](https://akcdev.blogspot.com/2017/02/invertir-una-cadena-con-javascript.html)*_
