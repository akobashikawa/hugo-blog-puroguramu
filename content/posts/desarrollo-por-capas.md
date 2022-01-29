---
title: 'Desarrollo por capas'
date: 2010-03-09T16:55:00.004-05:00
draft: false
url: /2010/03/desarrollo-por-capas
tags: 
- programación
- desarrollo
- metodología
- blogger
---

[![](http://3.bp.blogspot.com/_K2xwnQ4Llso/S5bBrGnKZHI/AAAAAAAAAYw/p-vPTk2WdZY/s320/Onions.jpg)](http://3.bp.blogspot.com/_K2xwnQ4Llso/S5bBrGnKZHI/AAAAAAAAAYw/p-vPTk2WdZY/s1600-h/Onions.jpg)

Me parece que hay un paralelo en lo que pasa entre un desarrollador y el jefe del proyecto, respecto a su trabajo, con lo que pasa entre un cliente y el desarrollador, respecto a su producto.  
  
El jefe del proyecto es el encargado de que los desarrolladores consigan el producto requerido. Y para hacerlo los organiza según cierta metodología (bueno, si hay suerte). Y suele ser una metodología genérica (waterfall, RUP, Scrum, ...).  
  
Es como cuando un desarrollador trata de imponer una solución genérica a un cliente. Lo obliga a ejercitarse en un flujo de trabajo artificial en lugar del flujo de trabajo naturalmente determinado por sus necesidades.  
Antes lo hacían a menudo, pero ahora los desarrolladores entienden que es mejor construir una solución específica, basada en las necesidades reales del cliente, en lugar de una basada en necesidades imaginadas.  
  
De forma similar, sería necesario que la forma de organizar el desarrollo de un proyecto sea determinada por las necesidades reales del equipo de desarrollo, en lugar de necesidades imaginadas por el jefe de proyecto, o incluso por el gerente.  
  
Es decir, se necesita una meta-metodología; algo que nos guíe en el proceso de encontrar la mejor organización para un escenario incierto de personas, recursos y problemas.  
  
Por mi parte, me parece que hay que ser pragmáticos, flexibles, intuitivos y algo amigos de descubrir lo desconocido.  
  
Por ejemplo, en el análisis de un problema relativamente extenso no vale la pena tener determinado de antemano todo lo que se requiere implementar.  
  
Me parece que es mejor hacer una lista de lo que se nos va ocurriendo e ir organizándola en capas conforme llega y conforme nos vamos ocupando de las capas más internas, que contienen la base, lo más escencial. E ir cubriendo cada capa gradualmente, hasta llegar a las capas externas, las de los detalles menos escenciales.  
  
Cada nuevo requerimiento justificado encajaría en alguna lugar de alguna capa. Las implementaciones se trabajarían por capas, dejando fuera de una iteración aquellas implementaciones que correspondan a otra capa.

_*Url archivado: [Desarrollo por capas](https://akcdev.blogspot.com/2010/03/desarrollo-por-capas.html)*_
