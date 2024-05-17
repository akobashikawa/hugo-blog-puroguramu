---
title: "Cómo usar un public externo en Spring Boot"
slug: "como-usar-un-public-externo-en-spring-boot"
categories: ["Java", "SpringBoot"]
tags: ["java", "spring", "springboot", "howto"]
featuredImage: "spring-boot.png"
images: ["spring-boot.png"]
draft: false
date: 2024-05-17T13:22:00-05:00
---

**¿Quieres que la carpeta pública de Spring Boot esté fuera del compilado?**
Te cuento el procedimiento que seguí y que puede ayudarte.

<!--more-->

# Cómo usar un public externo en Spring Boot

{{< mermaid >}}
flowchart LR;

Properties --o SpringBootProyect --> Build --> Run
Params --o Build

{{< /mermaid >}}

- Por default, el contenido estático se pone en `src\main\resources\static` y es incluido en el compilado.
- Es posible indicar usar un directorio externo al compilado.

```sh
mvn clean install

java -Dspring.web.resources.static-locations=file:$(pwd)/public/ -jar target/hello-0.0.1.war
```

- Alternativamente, se puede agregar la siguiente opción en `application.properties`:

```properties
spring.web.resources.static-locations=file:${user.dir}/public/
```

- De ese modo, ya no es necesario indicar ese parámetro en el comando:

```sh
mvn clean install

java -jar target/hello-0.0.1.war
```