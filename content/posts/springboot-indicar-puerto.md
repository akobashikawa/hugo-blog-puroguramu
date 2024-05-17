---
title: "Cómo indicar el port para Spring Boot"
slug: "como-indicar-el-port-para-spring-boot"
categories: ["Java", "SpringBoot"]
tags: ["java", "spring", "springboot", "howto"]
featuredImage: "spring-boot.png"
images: ["spring-boot.png"]
draft: false
date: 2024-05-17T12:53:00-05:00
---

**¿Quieres el puerto por default de Spring Boot?**
Te cuento el procedimiento que seguí y que puede ayudarte.

<!--more-->

# Cómo indicar el port para Spring Boot

{{< mermaid >}}
flowchart LR;

Properties --o SpringBootProyect --> Build --> Run

{{< /mermaid >}}

- Por default, port = 8080. Pero se puede indicar otro al correr el proyecto.

```sh
mvn clean install
java -Dserver.port=9090 -jar target/hello-0.0.1.war
```

- Alternativamente, se puede agregar la siguiente opción en `application.properties`:

```properties
server.port=9090
```

- De ese modo, ya no es necesario indicar ese parámetro en el comando:

```sh
mvn clean install

java -jar target/hello-0.0.1.war

```

- http://localhost:9090