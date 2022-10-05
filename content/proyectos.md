---
title: Proyectos
---

<!-- @todo: Añadir referencias -->

## Personales 

### Cristian.lat

_Cristian.lat_ es mi sitio web personal. Es un proyecto modesto y pequeño, pero hecho con mucho amor. 

Estoy muy orgulloso de él y cuido de mantenerlo liviano y depurado.

En él, publico de vez en cuando algún que otro artículo o traducción.

### MiyanoSwift

_MiyanoSwift_ es el nombre en clave de un proyecto de publicación automatizada de mis notas creadas con la aplicación _[Bear](//bear.app)_

Se llama _[Miyano](//github.com)_ en honor al primer proyecto del mismo tipo. También lleva la palabra _Swift_ en el nombre porque empezó siendo un proyecto hecho con ese lenguaje de programación. 

Actualmente lo desarrollo con _[SvelteKit](//sveltekit)_, aunque hay varios proyectos derivados que me gustaría explorar en _Swift_.

El objetivo del proyecto es crear una interfaz gráfica igual a la de _Bear_, pública y desde la cual pueda compartir mis notas. 

También estoy evaluando la idea de crear una _API_ a través de la que recuperar las notas con la(s) etiqueta(s) deseada(s) en formato _JSON_ para mostrarlas directamente en el blog de esta web, lo que me permitiría escribir los artículos en Bear y no tener que duplicar la información en el Blog.

El proyecto es visible en su estado actual [aquí](//bearkit.onrender.com)

### Zettels

El hermano mayor de _MiyanoSwift_. Empecé con este proyecto antes de usar _Bear_.

En esa época tomaba notas en formato de texto con aplicaciones como _The Archive_, _Obsidian_, _Notable_, etc...

Quería publicar mis notas para crear lo que algunos llaman _"Jardín digital"_ o _"Digital Garden"_.

Utilicé _Hugo_. En esa época todavía no era programador profesional. Algunas de las funcionalidades me costaron bastante (los _wikilinks_, los _backlinks_, la barra de búsqueda, etc...)

<!-- @todo añadir primera versión del proyecto y changelogs-->

Después empecé a usar Bear y me obsesioné con la idea de publicar mis notas. Pero el proceso de exportar las notas de forma manual en Bear para dárselas a Hugo y transformarlas con Zettels no era una opción.

Investigué y encontré un pequeño script PHP en Github creado por Steve Francia[^sfrancia] en Github con el que publicaba sus notas y me sirvió de base para crear un primer prototipo.

[^sfrancia]: Co-fundador de Panic

El principio era crear un repositorio en el que habría: la base de datos de Bear, el proyecto *Hugo* y el script PHP.

El repositorio era desplegado a _Netlify_, que estaba configurado para lanzar primero el script PHP (que exportaba las notas a la carpeta _content_ de _Hugo_) y luego el script de _Build_ de _Hugo_.

Al principio el proyecto convivía con mi blog personal (_cristian.lat_), pero me dí cuenta de la necesidad de separarlos en dos porque el repositorio se hacía cada vez más complejo ya quería que el blog tuviera un estilo diferente y cada vez que intentaba añadir algo al blog, rompía alguna cosa relacionada con las notas y viceversa.

Para ese entonces ya había empezado una carrera como desarrollador (aunque ~~seguía~~ sigo ~~muy~~ un poco verde) y pude sufrir en _"carne propia"_ los efectos de no aplicar la separación de responsabilidades [^concerns]

[^concerns]: _Separation of concerns_

### SwiftUItilities

Pequeña librería que extiende _SwiftUI_ para simplificar y acortar la sintáxis. La uso en todos mis proyectos. La he usado también en producción.

### Curso de organización digital

Curso sobre cómo gestionar correctamente el exceso de información y cómo organizar archivos de forma efectiva sin volverse loco.

Actualmente está en proceso de redacción.



