---
title: 'Imprimir formas en consola'
date: 2017-02-22T16:53:00.001-05:00
draft: false
url: /2017/02/imprimir-formas-en-consola
tags: 
- php
- blogger
---

En un aviso de Workana encontré un pedido como este:  
  
_Escribir un programa que pregunte al usuario elegir una forma para dibujar en la pantalla._  
_La forma puede ser: Circle, X, Box y un Box con una X._  
_También el usuario indica cuántas filas se usarán para dibujar la forma._  
_La forma debe ser dibujada con asteriscos (\*)._  
  
Me parece que se trata de un programa para correr en consola.  
  
En mi caso, me pareció más práctico intentarlo con php.  
  
**shapes.php**  
  
```
<?php  
do {  
 print "1. Circle\\n";  
 print "2. X\\n";  
 print "3. Box\\n";  
 print "4. XBox\\n";  
 fscanf(STDIN, "%d\\n", $option);  
} while (!$option);  
  
do {  
 print "Number of rows: ";  
 fscanf(STDIN, "%d\\n", $rows);  
} while (!$rows);  
  
for ($i=0; $i<$rows; $i++) {  
 for ($j=0; $j<$rows; $j++) {  
  $print\_dot = false;  
  switch ($option) {  
   case 1:  
    $print\_dot = is\_circle($i, $j, $rows);  
    break;  
   case 2:  
    $print\_dot = is\_x($i, $j, $rows);  
      
    break;  
   case 3:  
    $print\_dot = is\_box($i, $j, $rows);  
    break;  
   case 4:  
    $print\_dot = is\_xbox($i, $j, $rows);  
    break;  
  }  
  if ($print\_dot) {  
   print "\*";  
  } else {  
   print " ";  
  }  
 }  
 print "\\n";  
}  
  
function is\_circle($i, $j, $rows) {  
 $r = $rows - 1;  
 $d = pow(($i - $r/2), 2) + pow(($j - $r/2), 2) - pow($r/2, 2);  
 return abs($d) <= $rows/3;  
}  
  
function is\_x($i, $j, $rows) {  
 return ($i == $j) || ($j == ($rows-1) - $i);  
}  
  
function is\_box($i, $j, $rows) {  
 return ($i == 0) || ($j == 0) || ($i == $rows-1) || ($j == $rows-1);  
}  
  
function is\_xbox($i, $j, $rows) {  
 return is\_x($i, $j, $rows) || is\_box($i, $j, $rows);  
}  
  

```  
El ejercicio me pareció interesante para ver una manera simple de tomar una entrada desde consola. Y cuando llegué a la parte de impresión de formas me pareció más interesante. En particular la del círculo, que dejé para el final.  
  
Algunos conceptos de coordenadas y geometría analítica me ayudaron a completar el programa.  
  
El problema del círculo es, en el fondo, cómo imprimir una imagen en un medio de baja resolución.  
  
Esta es la forma en que se me ocurrió resolverlo, con una especie de detección de borde seteado a $rows/3, al tanteo (para que se vea bien el círculo en 4, 8 o 16 filas).  
  
Seguramente hay muchas maneras de resolverlo. ¿Cómo lo harías tú?  
  

[![](https://4.bp.blogspot.com/-XrMR4y7QlPk/WK4MKYlmPpI/AAAAAAAAGNw/OloOPFf01dM09yqSLjXeXI35Mg740ipIwCLcB/s320/screenshot.png)](https://4.bp.blogspot.com/-XrMR4y7QlPk/WK4MKYlmPpI/AAAAAAAAGNw/OloOPFf01dM09yqSLjXeXI35Mg740ipIwCLcB/s1600/screenshot.png)

_*Url archivado: [Imprimir formas en consola](https://akcdev.blogspot.com/2017/02/imprimir-formas-en-consola.html)*_
