---
title: 'Solucionando conexión de strapi a mLab'
date: 2018-09-18T11:35:00.000-05:00
draft: false
url: /2018/09/solucionando-conexion-de-strapi-mlab
tags: 
- mongo
- strapi
- blogger
---

[![](https://4.bp.blogspot.com/-Oas_tK7_yx8/W6EouKr18jI/AAAAAAAAQXs/q5R4jXY6j4M80Pq_OttF-tbIdNqiIeFRQCLcBGAs/s400/strapi-mlab-2-3.png)](https://4.bp.blogspot.com/-Oas_tK7_yx8/W6EouKr18jI/AAAAAAAAQXs/q5R4jXY6j4M80Pq_OttF-tbIdNqiIeFRQCLcBGAs/s1600/strapi-mlab-2-3.png)

  

  
[Strapi](https://strapi.io/) es un framework para node que facilita la creación de un cms.  

*   Como base de datos puede usar mongo, mysql, postgres.
*   Como frontend puede usar vue, react, angular.
*   El panel de administración luce bastante similar al de wordpress.
*   Tiene un plugin para servir los datos con graphql.
*   El idioma se puede configurar a español.

[mLab](https://mlab.com/) es un servicio que provee acceso a bases de datos mongo.

*   Tiene una capa de uso gratuita (via AWS de Amazon)

Instalación simple
------------------

*   Para usarlo con mongo, debe estar iniciado el servicio localmente
*   $ node --version

*   Se requiere al menos la versión 9

*   $ npm install -g strapi@alpha

*   Por alguna razón, recomiendan que trabajemos con la versión más fresca

*   $ strapi --version

*   Actualmente 3.0.0-alpha.14.1.1

*   $ strapi new myapp

*   Creará la estructura de directorios.
*   Hay que elegir como base de datos a mongo e indicar los parámetros

*   Esta data se guarda en **myapp/config/environments/development/database.json**
*   La base de datos aún no se crea en este punto

*   $ cd myapp
*   $ strapi start

*   Creará la base de datos
*   Iniciará el server
*   [http://localhost:1337](http://localhost:1337/)

Problema con mongo externo
--------------------------

Por alguna razón, cuando se indica que se conecte a una base de datos mongo externa para development, strapi devuelve un error.

  

Encuentro que en la configuración para production hay una propiedad extra uri.

  

Cuando se usa esta propiedad uri en la configuración para development, ya es posible conectarse a una base de datos mongo externa, como mlab, por ejemplo.

Solución
--------

*   $ strapi new myapp

*   Crear la aplicación indicando una base de datos mongo local
*   Esto aún no creará ninguna base de datos

*   Editar myapp/config/environments/development/database.json y agregar la propiedad uri:
*   $ cd myapp
*   $ strapi start

La configuración sería similar a:

```
{  
  "defaultConnection": "default",  
  "connections": {  
    "default": {  
      "connector": "strapi-hook-mongoose",  
      "settings": {  
        "client": "mongo",  
        "uri": "mongodb://username:password@hostname.mlab.com:12345/dbname",  
        "host": "hostname.mlab.com",  
        "srv": false,  
        "port": "12345",  
        "database": "dbname",  
        "username": "username",  
        "password": "password"  
      },  
      "options": {  
        "authenticationDatabase": "",  
        "ssl": false  
      }  
    }  
  }  
}
```

_*Url archivado: [Solucionando conexión de strapi a mLab](https://akcdev.blogspot.com/2018/09/solucionando-conexion-de-strapi-mlab.html)*_
