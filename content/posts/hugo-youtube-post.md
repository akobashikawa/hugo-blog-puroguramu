---
title: "Hugo: Tips para publicar un post con un video de youtube"
slug: "2022/01/hugo-youtube-post"
categories: ["Hugo"]
tags: ["hugo", "loveit", "youtube", "tips"]
featuredImage: "hugo-logo-wide.svg"
images: ["hugo-logo-wide.svg"]
draft: false
date: 2022-01-22T10:12:00-05:00
---

- Uso [Hugo](https://gohugo.io/), con el tema [LoveIt](https://hugoloveit.com/), para publicar un blog como este.
- Para mostrar un video se puede usar el shortcode `youtube`
```markdown
{{</* youtube XaKhz3iAxqQ */>}}
```
- Para obtener una featured imagen para el post del video, se puede usar [# Get YouTube Video Thumbnail Image](http://www.get-youtube-thumbnail.com/)
	- Requiere el url del video
- Para mostrar la feature image en el listado del home pero no dentro del post (ya que el video ya lo tiene), se puede usar en el front matter `featuredImagePreview` en lugar de `featuredImage`