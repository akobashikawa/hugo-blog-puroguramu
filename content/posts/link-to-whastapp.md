---
title: "Link hacia Whatsapp"
slug: "link-to-whatsapp"
categories: ["HTML"]
tags: ["html", "whatsapp", "solución"]
featuredImage: "link-to-whatsapp.jpg"
images: ["link-to-whatsapp.jpg"]
draft: false
date: 2022-03-11T23:56:00-05:00
---

**¿Quieres crear un link que abra un chat en Whatsapp?** Te cuento cómo lo solucioné con HTML.

<!--more-->

- Lo que necesitaba era que en el whatsapp del usuario se abriera un chat hacia cierto número y con un texto prestablecido.
- Encontré que debía formar un url con un formato similar a `https://api.whatsapp.com/send?phone=51999888777&text=Hola`
  - El **número de teléfono** indicado por *phone* debe incluir el código del país (51 en este ejemplo)
  - El **texto** indicado por *text* debe ser **url compatible**, es decir que se pueda indicar a través del url.
    - Puedes usar una herramienta como [URLEncoder](https://www.urlencoder.org/) para convertir tu texto. Incluso puedes poner emojis! 🙂
    - Si usas javascript para generar el enlace, la función `encodeURI` hace el trabajo.
- De ese modo, es posible formar un enlace como este:

```html
<a href="https://api.whatsapp.com/send?phone=51999888777&text=Hola%21%20%F0%9F%91%8D%F0%9F%99%82">Saludar por Whatsapp</a>
```

- Cuando el usuario hace clic en el enlace, le aparece un diálogo para permitirle ir a la app whatsapp (si está instalada), donde abrirá el chat correspondiente al número indicado y con el texto indicado pre llenado.

![](screenshot-whatsapp-hola.png)

¿Conoces otro modo de hacer esto, o quizás de manera más sencilla? Puedes compartirlo en los comentarios 🙏