---
title: Un blog en HTML puro
date: 2020-05-01
tags: ["webdev"]
type: blog
---

<div class="information-block">
Este artículo fue escrito antes de que descubriese Hugo, el sistema que uso actualmente para gestionar toda esta web
</div>

Siempre he sido de esas personas que se pierden en los detalles, de esos que se deleitan más en la optimización que en la acción.

No es de extrañar que cuándo decidí crear este blog, algo que se supone me tendría que haber llevado un par de horas, tardé en realidad 3 días.

Simplemente no podía decidir con qué herramienta crearlo.

Lo único que tenía claro es que, después de haber pagado un año de hosting a razón de casi 17 euros al mes en un proyecto sin monetizar **no iba a gastar ni un sólo euro más**. 

> Un droplet en DigitalOcean cuesta $5 y Laravel Forge — herramienta para hacer despliegues automáticos desde github, cuesta $12 en su plan más barato.

En el pasado he usado herramientas cómo Wordpress.

Odio Wordpress.

No es mi intención ofender ni menospreciar a nadie, sé que muchas personas usan Wordpress *—entre ellas muchos de mis amigos*...pero, simplemente no lo soporto.

Contratar un buen hosting de pago, configurar la base de datos y la instalación, encontrar plugins que funcionen correctamente y que no corrompan la configuración a largo plazo es un dolor con el que no estoy dispuesto a lidiar nunca más.

Fue por eso que al crear uno de mis proyectos fallidos, me decidí por <a href="//statamic.com">Statamic</a>.

Statamic es elegante, fácil de usar, amigable tanto para el desarrollador cómo para el editor. 
Un panel de control sexy como el sólo, un modelo de datos flexible, un ecosistema rico en plugins y una comunidad vibrante. Solo de pensarlo me entran calores *— y ganas de volver a utilizarlo!*

Pero tiene un problema...

Al igual que Wordpress, Statamic está escrito en PHP y necesita de un servidor capaz de ejecutarlo para hacer el trabajo pesado *—conversión de tus artículos a contenido interpretable por el navegador, indexado, paginación, etc...*

Esto realmente nunca me había molestado, pues estaba acostumbrado a pagar hosting con Wordpress.

El problema vino cuando empecé a crecer como desarrollador. Me di cuenta de que si quería sacarle provecho a Statamic necesitaba un workflow un poquito especial.

Sin entrar en detalles técnicos, ni del cómo ni el porqué, cada vez que creaba un artículo en el servidor tenía que copiar los cambios en local para evitar errores de versiones. <a class="note" id="note1" href="#1">1</a>

Esto significa que, cada vez que hiciese un cambio por muy insignificante que fuera (incluida la corrección una pequeña falta de ortografía) tenía que pasar por ese proceso.

Lo cual, como puedes imaginar, dificulta enormemente el proceso creativo y se traduce en una baja producción escrita *—el objetivo principal de un blog*

Sin contar con el hecho de que estaba pagando $12/mes por un servicio adicional —*adicional al hosting—* que automatizará este proceso

Dado que últimamente el tema económico ha estado un poco complicado para mí, decidí eliminar el servidor que tenía en DigitalOcean.

include "20200225163600.md"

Es por eso, que tras buscar, y empaparme en el fango probando tecnologías que pudiesen ser las perfectas candidatas para mi proyecto <a class="note" id="note2" href="#1">2</a> he decidido volver al origen, a nuestro viejo y fiable HTML.

Puede parecer una locura y de hecho lo es, pero hacía tiempo que no me sentía tan libre. 
De hecho, estoy escribiendo estas líneas poco después *—el mismo día—* de haber tomado la decisión, cuándo en realidad llevaba bastante tiempo sin escribir.

include "20200705174000.md"

Estoy bastante entusiasmado. Entre otras cosas, el hecho de tener un HTML/CSS independiente en cada artículo abre un mundo de posibilidades, cada nuevo artículo puede ser, en términos de diseño: idéntico, ligeramente diferente o completamente diferente al anterior.

Cada artículo es una aventura en la que puedo perderme creativamente, no sólo en la escritura sino en el diseño. Es excitante.

Por otro lado, quería empezar un blog sobre minimalismo, pero hoy, Miércoles 20 de mayo del 2020 le he dado cuenta la ironía de todo este asunto: pese a que quiero escribir sobre simplicidad y minimalismo estaba complicando mi vida más de la cuenta, es lo que en programación se conoce cómo "overenginering"

Estoy en una etapa de mi vida en la que quiero simplificar al máximo, cómo he dicho al principio del artículo, soy de esas personas que disfrutan complicándose la vida, pero luego sufren las consecuencias *— ¿nunca has sentido que cada día es como un "mini-burnout"?*. 

Parece ser que el perfeccionismo, un lastre que intento abandonar desde que tome consciencia de él, vuelve a mí cíclicamente. ¿Conseguiré algún día deshacerme completamente de él? Espero que sí...


### Algunas desventajas de este sistema:

- Olvídate de la paginación a menos que la crees manualmente
- Deberás añadir manualmente cada artículo al índice
- Olvídate de una barra de búsqueda
- Problemas eventuales de consistencia y de branding en el diseño
- El proceso de generación de Sitemaps y RSS no es automático

### Artículos útiles

- [Writing HTML in HTML](http://john.ankarstrom.se/html/)
- [Palabras](https://justinjackson.ca/words_es.html)
- [Never change the techonolgy > How to blog](https://macwright.org/2019/02/06/how-to-blog.html)


### Stack tecnológico

- [Espresso](//espressoapp.com)
- [Markdown](//es.wikipedia.com/markdown)
- [Tailwindcss](//tailwindcss.com)
- [Github Pages](//github.com)

### Notas

1. <a id="2"></a>Github [⤴](#note1)
2. <a id="1"></a>Tecnologías probadas durante mi búsqueda [^1]'[^2]'[^3]'[^4]'[^5] [⤴](#note2)


[^1]: Gatsby cloud + Contentful
[^2]: Gatsby + TinaCMS
[^3]: Gatsby + Sanity
[^4]: Sapper + Vercel
[^5]: Forestry + Hugo



