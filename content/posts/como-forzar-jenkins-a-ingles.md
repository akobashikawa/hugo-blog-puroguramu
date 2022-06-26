---
title: "Cómo forzar el idioma de Jenkins a Inglés"
slug: "como-forzar-jenkins-a-ingles"
categories: ["Jenkins"]
tags: ["jenkins", "windows", "devops", "problema", "solución"]
featuredImage: "jenkins-english.png"
images: ["jenkins-english.png"]
draft: false
date: 2022-06-26T00:30:00-05:00
---

**¿Quieres forzar a que Jenkins use inglés para seguir mejor la documentación?**
Te cuento el procedimiento que seguí.

<!--more-->

## Motivación
- Luego de instalar Jenkins, puede ser que algunas cosas aparezcan en español y otras en inglés.
	- \
    ![](20220624142332.png)
- Deseo que todo aparezca en inglés, para facilitarme seguir las indicaciones de las guías y documentación que voy consultando.

## Instalar plugin Locale
- _Administrar Jenkins_
	- \
    ![](20220625234144.png)
- _System Configuration_, _Administrar Plugins_
	- \
    ![](20220625234216.png)
- _Plugin Manager_, _Todos los plugins_, buscar _locale_, _Download now and install after restart_
	- \
    ![](20220625234527.png) 
- _Instalando/Actualizando plugins_, _Reiniciar Jenkins..._
	- \
    ![](20220625234617.png)
	- \
    ![](20220625234705.png)

## Configurar el plugin Locale
-  _Administrar Jenkins_, _Configurar el Sistema_
	- \
    ![](20220625235002.png)
- _Locale_, _Default Language_: en_US, _Apply_, _Guardar_
	- \
    ![](20220625235254.png)
	- \
    ![](20220625235415.png)

Espero te sirva de ayuda. \
¿Has encontrado alguna mejor manera de hacerlo? Puedes compartirlo en los comentarios 🙏