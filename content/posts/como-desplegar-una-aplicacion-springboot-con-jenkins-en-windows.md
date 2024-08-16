---
title: "Cómo desplegar una aplicación spring boot con Jenkins en Windows"
slug: "como-desplegar-una-aplicacion-springboot-con-jenkins-en-windows"
categories: ["Jenkins"]
tags: ["jenkins", "windows", "springboot", "devops", "problema", "solución"]
featuredImage: "jenkins-on-windows.png"
images: ["jenkins-on-windows.png"]
draft: false
date: 2022-07-07T11:27:00-05:00
---

**¿Quieres desplegar un servicio web hecho con springboot usando Jenkins en Windows?**
Te cuento el procedimiento que seguí en un Windows Server 2019 y que puede ayudarte.

<!--more-->

## Escenario
- **Windows Server 19**
- **Jenkins para windows**, corriendo como servicio en el 8080
  - \
    ![](20220624123449.png " ")
  - Plugin **maven**
  - _Global Tool Configuration_
    JDK: JDK 18
- Aplicación **springboot** que puede correr como servicio en 8081
  - Requiere **JDK 17**
    - Es para esta aplicación en particular, pero puede ser otra versión
  - Usa **maven**
  - Tiene un repositorio en **GitHub**
  - Se ha probado a mano, en el server, los comandos que permiten corren localmente la aplicación
    - git clone git@github.com:akobashikawa/springboot-rest-hello.git
    - cd springboot-rest-hello
    - mvn clean install package
    - cd target
    - java -jar -Dserver.port=8081 springboot-rest-hello-0.0.1-SNAPSHOT.jar
    - Si todo va bien, se puede comprobar en `http://localhost:8081/hello?name=Antonio`

## Referencias
- [Cómo instalar Jenkins en Windows](https://puroguramu.akcstudio.com/posts/como-instalar-jenkins-en-windows/)

## Crear job maven
- En **jenkins**, _New Item_
- _General_
  - _Name_: springboot-rest-hello-maven
  - _Description_: Simple service that say hello
  - _JDK_: JDK18
- _Source Code Management_: `git@github.com:akobashikawa/springboot-rest-hello.git`
- _Build Triggers_
  - Build whenever a SNAPSHOT dependency is built
  - GitHub hook trigger for GITScm polling
- _Build_
  - _Root POM_: `pom.xml`
- _Post Steps_
  - Run only if build succeeds
  - Execute Windows batch command
    ```
    cd C:\tools\SpringbootRestHello
    SpringbootRestHello.exe stop
    copy C:\data\jenkins_home\workspace\springboot-rest-hello-maven\target\springboot-rest-hello-0.0.1-SNAPSHOT.jar C:\tools\SpringbootRestHello /Y
    SpringbootRestHello.exe start
    ```

## Crear el servicio
- [Spring Boot Application as a Service](https://www.baeldung.com/spring-boot-app-as-a-service)
  - [Windows Service Wrapper](https://repo.jenkins-ci.org/releases/com/sun/winsw/winsw/2.9.0/)
- Descargo [WinSW](https://repo.jenkins-ci.org/releases/com/sun/winsw/winsw/2.9.0/winsw-2.9.0-bin.exe) y lo coloco en la carpeta que usaré para configurar el servicio.
  - `C:\tools\SpringbootRestHello`, por ejemplo
- Renombro `winsw-2.9.0-bin.exe` como `SpringbootRestHello.exe`
- Creo el archivo de configuración `SpringbootRestHello.xml`
  ```
  <service>
    <id>SpringbootRestHello</id>
    <name>SpringbootRestHello</name>
    <description>Proyecto simple para probar CI.</description>
    <env name="SPRINGBOOTRESTHELLO_HOME" value="%BASE%"/>
    <executable>C:\java\jdk-18.0.1.1\bin\java</executable>
    <arguments>-Xmx256m -jar -Dserver.port=8081 "%BASE%\springboot-rest-hello-0.0.1-SNAPSHOT.jar"</arguments>
    <logmode>rotate</logmode>
  </service>
  ```
  - Instalo el servicio
  - \
    ```
    C:\tools\SpringbootRestHello>SpringbootRestHello.exe install
    2022-07-07 10:52:11,817 INFO  - Installing the service with id 'SpringbootRestHello'
    ```
  - En _Services_, termino de configurar
    - \
      ![](springboot-service-windows-setting.png " ")
    - Pruebo iniciar el servicio
    - Si hubiera algún error, se puede revisar en `SpringbootRestHello\SpringbootRestHello.err.log`
      - Reviso que el logon lo haga mi usuario
        - Debe estar habilitado para iniciar servicios, según se explica en [Cómo instalar Jenkins en Windows](https://puroguramu.akcstudio.online/posts/como-instalar-jenkins-en-windows/)

## Prueba manual
- En jenkins, _Dashboard_, seleccionar el proyecto
- En el menú, _Build Now_
- Haciendo click sobre el número del build se puede acceder a la salida en consola
- Si todo va bien, se puede comprobar en `http://localhost:8081/hello?name=Antonio`

Espero te sirva de ayuda. \
¿Has encontrado alguna mejor manera de hacerlo? Puedes compartirlo en los comentarios 🙏