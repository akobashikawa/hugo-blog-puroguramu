---
title: "Cómo hacer multimodule en Spring Boot"
slug: "como-hacer-multimodule-en-spring-boot"
categories: ["Java", "SpringBoot"]
tags: ["java", "spring", "springboot", "howto"]
featuredImage: "spring-boot.png"
images: ["spring-boot.png"]
draft: false
date: 2024-11-29T02:57:00-05:00
---

**¿Quieres tener varios módulos, cada uno con su propio pom, properties y swagger?**
Te cuento el procedimiento que seguí y que puede ayudarte.

<!--more-->

# Cómo hacer multimodule en Spring Boot

{{< mermaid >}}
flowchart LR;

gs-multi-module --o library
gs-multi-module --o application
gs-multi-module --o applicationdos

{{< /mermaid >}}

- Es posible organizar módulos dentro de un proyecto spring boot, cada uno con su propio pom.xml, su propio application.properties y su propio swagger.

- Referencia: [Getting Started | Creating a Multi Module Project](https://spring.io/guides/gs/multi-module)

- Demo: [akobashikawa/springboot-multimodule: Ejemplo Spring Boot Multimodule](https://github.com/akobashikawa/springboot-multimodule)

## Módulos

```
gs-multi-module
|  pom.xml
└── library
|  pom.xml
|  application.properties
└── application
|  pom.xml
|  application.properties
└── applicationdos
   pom.xml
   application.properties
```

- `library` produce un jar pero no es una aplicación
- `application` tiene a `library` como dependencia
- `applicationdos` tiene a `library` como dependencia


## Build

```sh
mvn clean install
```


## Run

```sh
mvn spring-boot:run -pl application
```

- http://localhost:8081/application/home
- http://localhost:8081/application/swagger-ui/index.html

```sh
mvn spring-boot:run -pl applicationdos
```

- http://localhost:8082/applicationdos/home
- http://localhost:8082/applicationdos/swagger-ui/index.html


## Notas

### pom.xml

- El `pom.xml` del root puede incluir dependencias comunes. Pero también se puede insistir en declarar cada dependencia en cada módulo, lo que puede ser util si se quiere facilitar luego su separación como microservicio.

### application.properties

- `library` usa un `application.properties` local y cada módulo que lo usa tiene que sobrescribir una copia de sus propiedades.

### Swagger

- Aunque la documentación indica que es posible algo como `springdoc.swagger-ui.path=/applicationdos-swagger-ui`, encontré que no, y que lo posible es `springdoc.swagger-ui.path=/applicationdos/swagger-ui`