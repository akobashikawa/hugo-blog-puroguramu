---
title: "Cómo crear una página de error en Spring Boot"
slug: "como-crear-una-pagina-de-error-en-spring-boot"
categories: ["Java", "SpringBoot"]
tags: ["java", "spring", "springboot", "howto"]
featuredImage: "spring-boot.png"
images: ["spring-boot.png"]
draft: false
date: 2024-05-17T13:04:00-05:00
---

**¿Quieres mostrar los errores a tu modo en Spring Boot?**
Te cuento el procedimiento que seguí y que puede ayudarte.

<!--more-->

# Cómo crear una página de error en Spring Boot

{{< mermaid >}}
flowchart LR;

Properties --o SpringBootProyect --> Build --> Run
Templates --o SpringBootProyect

{{< /mermaid >}}

- Por default, cuando ocurre algún error para mostrar una página, se muestra la página Whitelabel, a menos que haya una página de error explícita.
- El template de una página de error explícita se puede colocar en `src\main\resources\templates\error.html`:

```html
<h1>Error</h1>
<dl>
	<dt>timestamp</dt>
	<dd><span th:text="${timestamp}"></span></dd>

	<dt>path</dt>
	<dd><span th:text="${path}"></span></dd>

	<dt>status</dt>
	<dd><span th:text="${status}"></span></dd>

	<dt>exception</dt>
	<dd><span th:text="${exception}"></span></dd>

	<dt>message</dt>
	<dd><span th:text="${message}"></span></dd>

	<dt>error</dt>
	<dd><span th:text="${error}"></span></dd>

	<dt>errors</dt>
	<dd><span th:text="${errors}"></span></dd>

	<dt>trace</dt>
	<dd><span th:text="${trace}"></span></dd>

</dl>
```
- Una página de error específica se puede colocar en `src\main\resources\templates\error\`. Por ejemplo, `src\main\resources\templates\error\404.html`