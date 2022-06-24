---
title: "Cómo renombrar quitando un prefijo, en la consola de comandos de Windows"
slug: "como-renombrar-quitando-prefijo-en-cmd-windows.md"
categories: ["Windows"]
tags: ["cmd", "windows", "devops", "problema", "solución"]
featuredImage: "cmd-windows.jpg"
images: ["cmd-windows.jpg"]
draft: false
date: 2022-06-22T16:41:00-05:00
---

**¿Quieres un comando para quitar el prefijo de múltiples archivos?** Te cuento el procedimiento que seguí en la consola de comandos de Windows.

<!--more-->

## Referencias
- [How do I remove the same part of a file name for many files in Windows 7?](https://superuser.com/a/871799/840070)

## Problema
- Tengo numerosos archivos nombrados según un patrón como `Pasted image 20220624112437.png`
- Quisiera que tuvieran un nombre tipo `20220624112437.png`.

## Procedimiento
- Usar el comando ren
- Encerrar entre comillas dobles las referencias a los nombres
- Usar `*`, como de costumbre, para representar uno o más caracteres
- Usar `/` para representar lo caracteres que se eliminaran

```
ren "Pasted image *.png" "/////////////*.png"
```

¿Has encontrado alguna mejor manera de hacerlo? Puedes compartirlo en los comentarios 🙏