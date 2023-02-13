---
title: Mis planes para esta web
tags: ["webdev"]
date: 2020-06-21
position: Monkey
background: "yellow"
---

Me gustaría que esta web se convirtiera en una plataforma educativa.

Irónicamente, tras abandonar _beelearner_[^1] por ser un proyecto poco humilde y concentrarme en el pequeño paso, he acabado creando algo mucho más grande y con más potencial.

El método Zettelkästen[^2] ha sido para mi una completa revelación con un potencial transformador en el cual tengo una fé casi ciega.

Es tan flexible y simple que resuelve todos los problemas que tuve con Beelearner:

1. Flujo de información `notas -> proyecto`, o dicho de otra manera, escribir artículos/tutoriales a partir de mis apuntes. Con este método mis apuntes son ficheros que compilan en las páginas de este proyecto de forma automática, con lo cual **no hay ningún paso intermedio entre escritura y publicación, toda nota en mi archivo se convierte en una página de este sitio web**
2. Arquitectura de la información. Con este método no necesito pensar en cómo estructurar los cursos ni las carpetas del proyecto, pues cada página puede ser incluida y reutilizada en múltiples cursos.

Tengo muchísimas ganas de empezar a monetizar el proyecto en cuanto antes, pero no es tan simple, pues necesitaría crear un área de miembros, lo cual da lugar a varios quebraderos de cabeza, pues tengo básicamente 2 opciones:


1. Usar [Statamic](https://statamic.com)
2. Usar [Hugo](https://gohugo.io)

Cada cual con sus ventajas y desventajas

### Statamic

La ventaja de usar Statamic es que es un framework de desarrollo web que viene de serie con todo lo que necesito para crear un área de miembros *— y mucho más*, todo ello empaquetado en un motor de templates sumamente sencillo, sin exagerar creo que un neófito podría perfectamente tener su propio Udemy montado en alrededor de una semana.

Eso sin contar con las múltiples bondades que trae incorporadas de serie:

- Búsqueda
- Multi-lengua (que es una opción que definitivamente voy a usar en el futuro o incluso en el corto plazo)
- Protección con contraseña: Puedo proteger las notas privadas con contraseña y acceder a ellas en el frontend
- Muy extensible y con el mejor sistema de templates del mundo


**Lo no tan bueno**

- Para procesar pagos tendría que hacer uso de un plugin premium que cuesta $100...
- Necesitaría encontrar una manera de desplegar el proyecto usando Git en los dos sentidos (aunque creo que no haría falta realmente)
- Tal vez tendría que aprender a configurar una base de datos para almacenar los usuarios, aunque no sería necesario en las primeras etapas
- No sabría elegir entre la versión 2 y 3 (lista para producción, pero todavía en desarrollo y con la cual no podría usar los plugins de pago que usaba en la v2)


### Hugo: Making the web great again

¿Qué decir de Hugo?

Es el descubrimiento del siglo.
Hugo es sencillez, es eficacia, es potencia. 
Hugo es poderoso, rápido y, lo más importante, GRATIS!

Hugo me permitió recortar mis facturas, pasando de 15€ mes a 0€ mes y enamorarme del desarrollo web y el movimiento JAMStack.

Este chico malo compila mis más de 900 notas en cuestión de milisegundos sin despeinarse siquiera y todo eso mientras compila y minifica SASS y empaqueta los JS en un bundle único.

Los problemas son además fáciles de "debuggear".

**Lo no tan bueno**

- Hugo es un SSG, es decir, un generador de sitios **estático**, ES-TÁ-TI-CO, consecuentemente, para implementar una área de miembros tendría que aprender mucho más javascript del que sé para hacer uso de firebase o bien usar un servicio de terceros a 25€/mes.
- He invertido muchísimo en Statamic cómo para no usarlo, *—mea culpa*[^3]


### Notas

- Crear una pequeña nota explicando lo que es Beelearner, añadir también el mockup que estaba haciendo en Xd cuando estaba en la comunidad
- Añadir footnotes al artículo


[^1]: [[la-colmena-de-mrbee]] Beelearner era un proyecto que consistía en una academia en línea
[^2]: [[20200502133930]] Zettelkästen
[^3]: 2 licencias + 2 plugins de pago
