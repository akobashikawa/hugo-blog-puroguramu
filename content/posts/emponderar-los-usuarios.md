---
title: 'Emponderar a los usuarios'
date: 2017-05-24T12:07:00.000-05:00
draft: false
url: /2017/05/emponderar-los-usuarios
tags: 
- libertad
- opinión
- windows
- linux
- programación
- mac
- blogger
---

[![](https://4.bp.blogspot.com/-LrOgLPu848s/WSXADSpyWJI/AAAAAAAAHDs/04_4Z_7Tu7UzGLYNr0cENOyXmcm5r5ydACLcB/s320/lego-composer.png)](https://4.bp.blogspot.com/-LrOgLPu848s/WSXADSpyWJI/AAAAAAAAHDs/04_4Z_7Tu7UzGLYNr0cENOyXmcm5r5ydACLcB/s1600/lego-composer.png)

Cuando estaba en la universidad, retomé el contacto con las computadoras después de un largo tiempo y conocí el **DOS **de Microsoft.  
  
Estaba frente a una pantalla negra con el prompt **C:\\>** esperando a que ingresara algo. Cuando lo hacía, me respondía.  
  
Me sentía fascinado.  
  
Aprendí a usar casi todos los comandos de la consola, y a programar nuevos comandos.  
  

*   En la consola **command**, se pueden ejecutar comandos cuyas salidas pueden ser entradas de otros comandos.
*   Se pueden crear fácilmente nuevos comandos **batch **ejecutables desde la consola. Ya que los batch son archivos de texto simple y la consola tiene algunos comandos para generarlos.
*   Un comando podría generar nuevos comandos dinámicamente. Es decir, un batch se podría generar dentro de la rutina de un comando y ser ejecutado luego dentro del mismo comando.
*   Los programas de **pantalla completa**, aunque impresionantes, rompen el esquema de reutilización de comandos al apropiarse de toda la interfaz.

Más tardee, conocí **Linux **y la consola de comandos **bash**, donde se pueden observar puntos similares.

  

  

En la interfaz gráfica de **Windows**, en cambio:

*   En el escritorio, se pueden ejecutar **aplicaciones**, pero estas ejecuciones son **aisladas **y no se puede realizar ejecuciones compuestas donde la salida de una aplicación sea la entrada de otra, dinámicamente.
*   No hay herramientas para construir fácilmente nuevos programas desde el escritorio. Las aplicaciones no son interpretadas, sino ejecutadas desde un **binario**, y construir ese binario requiere conocimientos y herramientas especializadas.
*   No hay una forma sencilla de construir aplicaciones que puedan generar otras aplicaciones dinámicamente, dentro de su ejecución. No es sencillo construir compiladores.
*   La reutilización de las características de una aplicación es difícil. Cada característica está pegada a la aplicación. Cada mejora de características requiere una nueva versión realizada principalmente por quienes la programaron.

Algo parecido se puede decir de las interfaces gráficas de Linux (Gnome) y de la Mac (OSX), que vine a conocer luego.

  

  

En la interfaz gráfica de la **Web**, en el browser, se muestra una aplicación:

*   Cómo hacer que la aplicación sea un entorno donde se puedan ejecutar **componentes **que puedan componerse para formar nuevos componentes?
*   Cómo hacer que sea fácil crear componentes con los componentes presentes en el entorno?
*   Cómo hacer que un componente pueda generar dinámicamente otros componentes dentro de su ejecución?
*   Cómo prevenir que un componente pueda apropiarse de la interfaz?

  

Me parece distinguir que ese conjunto de características facilita que un sistema pueda ser **extendido **con la participación de sus usuarios.

  

El conjunto de comandos DOS y bash, puede ser fácilmente extendido por sus usuarios. Habrá programadores capaces de hacer nuevos binarios, pero la capacidad de hacer scripts, batch o bash, está disponibles de inmediato.

  

El conjunto de aplicaciones en Windows (o Gnome, o OSX) no puede ser fácilmente extendido por sus usuarios. Sólo puede serlo a través de programadores capaces de hacer nuevos binarios.

  

Uno se puede preguntar si esta limitación es puesta **a propósito**.

  

Al limitar que los usuarios puedan extender el sistema que usan, las empresas proveedoras de software se aseguran el papel de intermediarios, entre los usuarios y las soluciones que los usuarios requieren.

  

Y es conocido en el **comercio **que el **intermediario **siempre gana.

  

Así que me parece que la cuestión de limitar la extensibilidad del sistema por parte de los usuarios puede ser algo diseñado.

  

Sin embargo, ¿por qué ocurre también en la interfaz gráfica de Linux?. Siendo la comunidad Linux un fuerte representante del movimiento de **software libre** (promotor de dar a la gente la libertad de usar el software como quiera), esperaría que hubieran escritorios que permitieran componer aplicaciones visualmente, siguiendo la filosofía de composición de comandos que está presente en la consola.

  

Quizás sea que están distraidos por las complejidades de otros problemas.  
  

  

Pero me parece que resolver esta situación sería muy interesante. Un escritorio así, emponderaría a los usuarios para crear cosas, sus propias cosas, y compartirlas en comunidad.

  

A mediados de los 80, [**Hypercard**](https://en.wikipedia.org/wiki/HyperCard), de **Bill Atkinson**, fue una aplicación gráfica que facilitaba a los usuarios la creación de sus propias soluciones y a compartirlas. Atkinson insistió en que se distribuyera de modo **gratuito **y **Apple **insistió en encontrarle alguna manera de obtener ganancias. Finalmente, el desarrollo de Hypercard se estancó y **Steve Jobs** canceló su desarrollo, cuando volvió a mediados de los 90.

  

Aunque hoy hay fans que recuerdan el legado de Hypercard, me parece que se enfocan más en las **cualidades técnicas** (como la interfaz gráfica, que sirvió de inspiración a **VisualBasic **y otras herramientas), que en la **cualidad social** de emponderar a los usuarios para hacer sus propias soluciones.

  
  
Quizás sea posible implementar la idea en la web, usando componentes que puedan componerse para formar nuevos componentes, tanto a mano como dinámicamente.  
  
Quizás **React** pueda ser una buena opción para eso. (Sin embargo, la forma en que se suele usar React, con **Webpack** para generar compilados, parece una especie de barrera. A veces parece como si las compilaciones fueran una forma de dejar fuera a los demás y ponerse uno como intermediario.)  

  

  

_Transcrito de [http://rulokoba.blogspot.pe/2017/05/un-entorno-que-empondere-los-usuarios.html](http://rulokoba.blogspot.pe/2017/05/un-entorno-que-empondere-los-usuarios.html)_

_*Url archivado: [Emponderar a los usuarios](https://akcdev.blogspot.com/2017/05/emponderar-los-usuarios.html)*_
