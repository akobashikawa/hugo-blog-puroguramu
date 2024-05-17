---
title: "Cómo usar una configuración externa en Spring Boot"
slug: "como-usar-una-configuracion-externa-en-spring-boot"
categories: ["Java", "SpringBoot"]
tags: ["java", "spring", "springboot", "howto"]
featuredImage: "spring-boot.png"
images: ["spring-boot.png"]
draft: false
date: 2024-05-17T13:25:00-05:00
---

**¿Quieres que la configuración de Spring Boot esté fuera del compilado?**
Te cuento el procedimiento que seguí y que puede ayudarte.

<!--more-->

# Cómo usar una configuración externa en Spring Boot

{{< mermaid >}}
flowchart LR;

Properties --o SpringBootProyect --> Build --> Run
Params --o Build

{{< /mermaid >}}

- Por default, `application.properties` se busca en estas ubicaciones:
	- `file:./config/`
	- `file:./`
	- `classpath:/config/`
	- `classpath:/`
- Es decir, se puede tener `src\main\resources\application.properties` que será incluido en el war, y `config\application.properties` en la carpeta donde se ejecute el war.
- Referencia: [24. Externalized Configuration](https://docs.spring.io/spring-boot/docs/2.1.13.RELEASE/reference/html/boot-features-external-config.html)
## Usando un nombre diferente

- También es posible indicar un directorio de configuración con nombre distinto.

```sh
mvn clean install

java -Dspring.config.location=conf/application.properties -jar target/hello-0.0.1.war
```

- Alternativamente, se puede agregar la siguiente opción en `application.properties`:

```properties
spring.config.additional-location=file:${user.dir}/conf/
```

- De ese modo, ya no es necesario indicar ese parámetro en el comando:

```sh
mvn clean install

java -jar target/hello-0.0.1.war

```