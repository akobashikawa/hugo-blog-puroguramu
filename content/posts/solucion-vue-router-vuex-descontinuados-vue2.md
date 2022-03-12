---
title: "Solución al Vue Router y Vuex descontinuados para Vue2"
slug: "solucion-vue-router-vuex-descontinuados-vue2"
categories: ["Vue"]
tags: ["vue", "vue-router", "vuex", "problema", "solución"]
featuredImage: "new-features-in-vue-3.avif"
images: ["new-features-in-vue-3.avif"]
draft: false
date: 2022-03-11T23:08:00-05:00
---

**¿Tienes alguna aplicación vue2 que ha dejado de funcionar de pronto?** Te cuento cómo solucioné la incompatibilidad que se presentó para vue-router y vuex.

<!--more-->

- Hoy noté que una de las aplicaciones que desarrollé con **vue2** estaba caída 🙈.
  - Revisando la consola, noté que no encontraba `https://unpkg.com/vue-router@4.0.14/dist/vue-router.js`.
  - Ese era el destino final que correspondería al que le indicaba en mi código: `//unpkg.com/vue-router/dist/vue-router.js`.
    - Cuando se indica así te lleva a la última versión, que al parecer ya no es más vue2 compatible.
- Al parecer, la versión 4 de vue-router se ha vuelto **vue3 compatible por default**, así que hay que indicar explícitamente la versión vue2 compatible que uno quiere usar.
- Pasé a indicar la **versión 3 de vue-router** y ya funcionó esa parte
  - De `//unpkg.com/vue-router/dist/vue-router.js` a `//unpkg.com/vue-router@3`. 👍🙂
- Luego pase a resolver el issue similar para el caso de **vuex**.
  - Allí, también tuve tuve que indicar explícitamente la versión vue2 compatible (casualmente también es la 3)
    - De `//unpkg.com/vuex` a `//unpkg.com/vuex@3`.
- En mi caso, estos dos cambios fueron suficientes para que la aplicación volviera a estar operativa. ✌️🙂

¿Has encontrado alguna versión más reciente de estos paquetes que sea vue2 compatible? Puedes compartirlo en los comentarios 🙏