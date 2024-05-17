---
title: "Cómo indicar no usar Whitelabel en Spring Boot"
slug: "como-indicar-no-usar-whitelabel-en-spring-boot"
categories: ["Java", "SpringBoot"]
tags: ["java", "spring", "springboot", "howto"]
featuredImage: "spring-boot.png"
images: ["spring-boot.png"]
draft: false
date: 2024-05-17T13:04:00-05:00
---

**¿Quieres que Spring Boot ya no muestre la página WhiteLabel?**
Te cuento el procedimiento que seguí y que puede ayudarte.

<!--more-->

# Cómo indicar no usar Whitelabel en Spring Boot

{{< mermaid >}}
flowchart LR;

Properties --o SpringBootProyect --> Build --> Run

{{< /mermaid >}}

- Por default, cuando ocurre algún error para abrir una página, se muestra la página Whitelabel.

![](SpringBoot-NoWhitelabel.png)
- Es posible indicar que no se use:

```sh
mvn clean install

java -Dserver.error.whitelabel.enabled=false -jar target/hello-0.0.1.war
```

![](SpringBoot-NoWhitelabel-1.png)
- Alternativamente, se puede agregar la siguiente opción en `application.properties`:

```properties
server.error.whitelabel.enabled=false
```

- De ese modo, ya no es necesario indicar ese parámetro en el comando:

```sh
mvn clean install

java -jar target/hello-0.0.1.war
```

- Cuando ya no hay Whitelabel para mostrar los errores, estos se mostrarán en la consola.