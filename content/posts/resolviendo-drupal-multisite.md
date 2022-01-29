---
title: 'Resolviendo Drupal multisite'
date: 2010-03-12T02:09:00.003-05:00
draft: false
url: /2010/03/resolviendo-drupal-multisite
tags: 
- drupal
- blogger
---

[![](http://2.bp.blogspot.com/_K2xwnQ4Llso/S5npftXwF6I/AAAAAAAAAZ4/jCw57lVO100/s320/drupal_multisite.png)](http://2.bp.blogspot.com/_K2xwnQ4Llso/S5npftXwF6I/AAAAAAAAAZ4/jCw57lVO100/s1600-h/drupal_multisite.png)

Aunque la instalación y configuración inicial de Drupal es relativamente sencilla y directa, configurarlo para que varios sites compartan el mismo motor fue, para mí, casi un dolor de cabeza.  
  
**Drupal**  
Drupal es un CMS (Sistema administrador de contenidos) open source escrito en PHP. Es muy popular y, debido a su arquitectura especialmente extensible, que permite construir aplicaciones más allá del CMS, es considerado también como framework.  
  
La instalación es simple. Se descomprime el archivo que se descarga de [drupal.org](http://drupal.org/) en algún lugar del directorio web. Luego se accede a la dirección correspondiente y se siguen los pasos, que incluye indicar los parámetros de acceso a una base de datos MySQL (o PostgreSQL) y definir un usuario administrador.  
  
**Drupal Multi-Site**  
En el árbol drupal instalado hay un directorio _**sites**_. Allí, en el directorio _**default**_ podemos colocar los archivos, módulos y temas del site. Además hay un directorio _**all**_, donde el manual, los tutoriales y los libros colocan los módulos y temas para que 'estén disponibles para todos los otros sites'.  
  
Así que uno se imagina que puede tener más sites bajo ese mismo árbol, funcionando con el mismo motor. De hecho, esa configuración se denomina **multi-site**.  
  
Pareciera que es algo que no se usa mucho, porque no lo mencionan en ningún material introductorio. En la documentación hay varios casos para leer. Si antes de hacerlo uno se imagina que bastará con crear otros subdirectorios con la misma estructura, encontrará que no es así.  
  
Entonces, lógicamente, se lee un poco el manual... luego en los foros... blogs... googleando en la búsqueda de una explicación que quién iba a pensar sería tan difícil de encontrar. Es un problema algo frustrante. Al menos para mí; me tomó todo el día dar con una solución.  
  
**Mi ambiente**  
En un sistema con Windows 7, desarrollo usando XAMPP 1.7.1.  
  
_XAMPP es un paquete que facilita el desarrollo PHP/MySQL. Viene con Apache, PHP, MySQL y Mercury Mail preconfigurados para trabajar juntos, lo que es realmente un gran ahorro de tiempo, respecto a realizar manualmente cada instalación/configuración. Uso la versión 1.7.1 porque usa PHP 5.2, que no emite una alarma cada vez que un parámetro es pasado por referencia (lo cual en PHP 5.3 se ha vuelto deprecated). Y como muchos módulos que corren con Drupal 6.x tienen funciones con parámetros pasados por referencia me parece mejor ser un poco prácticos y usar una versión menos que la ultimita :)_  
  
_XAMPP 1.7.1 viene con Apache 2.2.11, PHP 5.2.9, MySQL 5.1.33-community, entre otros paquetes (__ver [Old Version of XAMPP](http://www.oldapps.com/xampp.php?old_xampp=44) para más detalles)._  
  
Se supondrá que XAMPP está instalado en C:\\bin\\dev\\xampp\\. Eso significa que el directorio web es C:\\bin\\dev\\xampp\\htdocs\\. Allí, Drupal 6.16 está instalado en test\\drupal\_101\\. Es decir que, para acceder a mi drupal, el url es http://localhost/test/drupal\_101/.  
  
Podría ser más sencillo, pero no es demasiado complicado y creo que tener el drupal un poco metido en el árbol ayudará a ilustrar mejor el punto.  
  

**Mi solución**

Los pasos que suelen aparecer en la mayoría de la documentación, foros, blogs y otras fuentes de internet mencionan virtualhosts o aliases en apache, .htaccess, hosts, subdominios y otras cosas complicadas.  
  
Practicamente nadie se detiene a explicar el por qué la necesidad de estas complicaciones, o cuál es la idea básica del proceso. Y me parece que deberian hacerlo, porque aclara algo muy importante del funcionamiento de Drupal.  
  
Cuando accedo a http://localhost/test/drupal\_101/, Drupal eventualmente buscará un archivo settings.php. En una instalación típica lo encuentra en sites/default/settings.php.  
  
Lo que no se nos dice con claridad es que, en realidad, **Drupal usa el url como parámetro para determinar dónde buscar el archivo settings.php**. De hecho, parece que **default** es el último lugar donde busca. Antes ha buscado en **localhost.test.drupal\_101**. Puede hacer la prueba renombrando **sites/default** como **sites/localhost.test.drupal\_101** y ver que funciona igual. Sorprendente ¿no?  
  
Si yo quisiera un nuevo site, digamos http://localhost/test/drupal\_202/, lo que tendría que hacer es correr la misma aplicación pero bajo ese nuevo nombre. Es decir, lograr que al entrar a ese url se corra exactamente el mismo php que antes. Eso haría que Drupal busque el archivo **sites/localhost.test.drupal\_202/settings.php** correspondiente. Y si existiera y estuviera bien configurado, listo, ¡tendríamos Drupal multi-site!  
  
Pero ¿cómo hacer eso?. Ahí es donde la mayoría mete en el juego las complicaciones de los dominios, subdominios, hosts, virtualhosts, .htaccess, etc. Son soluciones válidas pero, en mi humilde opinión, hay un modo más sencillo, que está al alcance tanto de los usuarios Windows como Linux, y además ilustra bastante más cláramente lo que ocurre.  
  
Abro una consola de comandos en el directorio que contiene a mi arbol drupal\_101, htdocs/test/ (SHIFT+clic derecho, Open command window here), para ejecutar el comando **mklink**:  
  

mklink /J drupal\_202 drupal\_101

  
Eso crea un enlace simbólico (una especie de directorio ficticio) que permite apuntar al directorio drupal\_101 con un nombre nuevo adicional drupal\_202.  
  
_mklink está disponible en Windows 7 y WIndows Vista. Para Windows XP puede usar el comando **Junction** (puede ver más información sobre esto en el post [Enlaces simbólicos en Windows](http://akcdev.blogspot.com/2010/03/enlaces-simbolicos-en-windows.html)). En Linux usaría un comando similar a **ln -s drupal\_101 drupal\_202** (allí primero se indica el destino y luego el link)._  
  
Hecho esto, al entrar a http://localhost/test/drupal\_202/ uno esperaría ver lo mismo que si se entrara a http://localhost/test/drupal\_101/. Después de todo se trata del mismo directorio, aunque tenga dos etiquetas. Pero, como Drupal usa el url como parámetro para determinar el lugar dónde debe estar el archivo settings.php, encontrará uno diferente en sites/localhost.test.drupal\_202/ y así veremos un site también diferente.  
  

**En resúmen**

Drupal usa el url como parámetro para determinar que settings.php usar. Y el settings.php determina el site que se carga. De ese modo podemos tener varios sites, si logramos entrar al mismo drupal usando diferentes nombres. Una manera sencilla de lograr eso es usando enlaces simbólicos. Eso me parece menos complicado que la alternativa de los aliases, y virtualhosts.  
  
En el fondo, esta técnica aparece en la documentación cuando habla del uso de subdominios, pero la idea escencial está tan opacada por las otras dificultades que cuesta distinguirla. Ojalá este artículo sea de ayuda.  
  

**Posibilidades**

Basta cambiar la configuración de la base de datos que aparece en el settings.php para que el site se transforme en algo completamente diferente. Jugar con esto me ayudó a entender un poco mejor la naturaleza de una aplicación drupal respecto de otras opciones.  
  
El nombre localhost.test.drupal\_202 sigue un patrón que se explica mejor en el comentario contenido en el archivo **default.settings.php**

_*Url archivado: [Resolviendo Drupal multisite](https://akcdev.blogspot.com/2010/03/resolviendo-drupal-multisite.html)*_

---
### Comentarios archivados:

>
> Estimado  
llevo una semana tratando de activar un multisitios  
Mi sitio drupal 7 esta en www.publisearch.cl  
Dentro de la carpeta sites cree la carpeta prueba  
Y dentro de pruebas copie y pegue el default.settings.php  
Lo renombre a settings.php  
En mi cpanel cree una nueva base de datos  
Edite el settings.pho que esta en la carpeta prueba  
y lo configure para trabajar con esta nueva base de datos  
Con chmod le di permisos 777  
Fui a www.publisearch.cl/sites/prueba  
Y me da el mensaje PAGINA NO ENCONTRADA  
No logro como forzar a drupal para que lea este settings.php que esta  
en sittes/prueba/settings.php  
Vi por alli en un foro que podia crear en php un enlace simbolico (baje uno)pero NO se como configurarlo para que funcione  
Trate con subdominios configurados en cpanel  
Pero no logro llegar a este nuevo settings.php  
me da el mensaje Forbiden, error 404 ....  
Una pregunta ignorante  
Si llegase a entrar a este nuevo settings.php  
Se ejecuta una nuevo proceso de instalacion (para ingresar user, pasword, nombre del sitio, mail de contacto etc...)  
O de inmediato abre un nuevo sitio en blanco listo para recibir su primer contenido?  
No sabes lo agradecido que estaria si logras ayudarme  
Att  
Hernando Acevedo  
Santiago - Chile  
hdac1960@gmail.com
> \
> [Anónimo](# "noreply@blogger.com") [2011-01-15 15:49]

>
> Hola, he trabajado poco tiempo con Drupal 7 y no he tenido oportunidad de usar el multisitios en ese caso.  
Pero, si fuera un Drupal 7 normal, y deseas acceder a él en www.publisearch.cl/sites/prueba, lo que se hace es colocar el árbol de drupal en ese directorio prueba, luego en sites/default/ crear el archivo settings.php y acceder en el navegador a http://www.publisearch.cl/sites/prueba para proceder con la instalación. Más info en https://drupal.org/documentation/install y https://drupal.org/node/43816 Buena suerte!
> \
> [Rulo Kobashikawa](https://www.blogger.com/profile/07020497448167262255 "noreply@blogger.com") [2014-06-03 23:26]

>
> This post will assist the internet visitors for setting up new web site or even a blog from start  
to end.  
  
My site - [seo web development company](https://www.youtube.com/watch?v=QRrPhWYXfRA)
> \
> [Anónimo](# "noreply@blogger.com") [2014-08-05 13:45]
