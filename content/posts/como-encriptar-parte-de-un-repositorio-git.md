---
title: "Cómo usar git-crypt para encriptar parte de un repositorio Git"
slug: "como-encriptar-parte-de-un-repositorio-git"
categories: ["Git"]
tags: ["git", "windows", "linux", "problema", "solución"]
featuredImage: "git-crypt.png"
images: ["git-crypt.png"]
draft: false
date: 2022-07-16T02:24:00-05:00
---

**¿Quieres guardar de manera más segura información dentro de tu repositorio git?**
Te cuento el procedimiento que seguí con `git-crypt` que puede ayudarte.

<!--more-->
## Referencias
- [CIFRANDO ARCHIVOS EN GIT CON GIT-CRYPT](https://ugeek.github.io/blog/post/2019-07-10-cifrando-archivos-en-git-con-git-crypt.html)
- [How to Manage Your Secrets with git-crypt](https://dev.to/heroku/how-to-manage-your-secrets-with-git-crypt-56ih)
- [git-crypt for Windows](https://github.com/oholovko/git-crypt-windows)
- [Syncing your Obsidian vault to Android via an encrypted GitHub repository](https://renerocks.ai/blog/obsidian-encrypted-github-android/)

## Escenario
- **Git instalado**

## Instalar git-crypt

### Linux
- $ sud apt install git-crypt

### Windows
- Colocar en el path el ejecutable que se puede descargar de [git-crypt for Windows](https://github.com/oholovko/git-crypt-windows)

### Android
- Via termux
  - $ pkg install git-crypt

## Preparacion del repositorio

### Git
- $ git init
- $ echo "# Readme" > readme.md
- $ git add .
- $ git commit -m "First commit"
- $ git push

### Git Crypt
- $ git-crypt init
- $ git-crypt export-key ../git-crypt-key
  - Este archivo `git-crypt-key` **es la llave que hay que conservar y usar con cuidado**
- $ mkdir secret
  - Esta será una carpeta para contenido secreto
  - También podría haber sido un archivo
  - Los patrones se indicaran en `.gitattributes` 
- $ vim `.gitattributes`

```
secret/** filter=git-crypt diff=git-crypti
.gitattributes !filter !diff
```
- A partir de ahora, **cada commit encriptará esos archivos**
- $ git add .
- $ git commit -m "Add .gitattributtes"
- $ git push

### Guardar contenido
- $ echo "This is a secret" > secret/readme.md
- $ git add .
- $ git commit -m "Add secret content"
- $ git push
- En el repositorio, el contenido dentro de secret aparecerá encriptado
- Cualquiera que descargue el repositorio, vera encriptado ese contenido
- Localmente, sin embargo, el contenido no está encriptado
  - Pero modo fácil de comprobar la encriptación en local es usando `lock`
  - $ git-crypt lock
  - $ cat secret/readme.md
    - Esta vez se verá encriptado

### Desencriptar
- $ git-crypt unlock ../git-crypt-key
  - Esto vuelve a mostrar sin encriptar el contenido local, que es la manera usual de trabajar

## Flujo de trabajo
- Trabajar de modo que el contenido local no se muestre encriptado, usando `unlock`
- Usar `lock` y ocultar la llave cuando se desee asegurar el contenido local

## Util
- $ git-crypt status secret
  - Muestra info acerca del estado de la carpeta `secret`

Espero te sirva de ayuda. \
¿Has encontrado alguna mejor manera de hacerlo? Puedes compartirlo en los comentarios 🙏