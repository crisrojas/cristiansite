---
title: Etiquetas HTML personalizadas
date: 2020-07-20
---

Etiquetas HTML personalizadas

Recientemente[^rec] me dí a la tarea de refactorizar mis hojas de estilo.

[^rec]: [[20200720142211]] Refactorizando mis CSS

Para simplificar al máximo el mantenimiento, intento no usar clases. Únicamente las etiquetas nativas de HTML.

No es que la semántica sea un tema que me quite el sueño, es que creo que todo ha de simplificarse tanto cómo sea posible.


Estaba refactorizando un componente —el _header_ del blog—  que contenía una etiqueta `<p>` destinada a mostrar mi profesión.

Intenté encontrar una etiqueta semántica para este caso en específico, pero no hay, a la fecha, ninguna etiqueta que se adapte a la situación.

Se me ocurrió que tal vez, pese a que en la sintáxis oficial tal etiqueta no existe, dado que los navegadores suelen tratar las etiquetas extrañas como div, podría usar una etiqueta personalizada y no oficial : `<job>`

Así que investigué hasta que punto es malo usar este tipo de etiquetas y cómo implementarlas.

Encontré un hilo en stackoverflow que hablaba del tema, y aunque las respuestas eran bastante informativas, el hecho del quel hilo tenga 10 años hace que no pueda conformarme con ellas.

Lo que saqué en claro es que sí se pueden usar, aunque no sea una buena práctica.

**Implementación**

Dado que la mayoría de navegadores tratan las etiquetas ajenas a la sintáxis oficial como divs, puedes empezar a tus etiquetas personalizadas sin ningún tipo de pre-configuración.

Para normalizar su uso, sin embargo, has de darle un par de propiedades en tu hoja de estilos. Por ejemplo, si quiero usar una etiqueta `<job>`, en el css escribiría:

```css
job {
    display: block;
    margin: 0;
    padding: 0;
}
```

Y para que sean compatibles con versiones de IE:

```html
<!--[if lt IE 9]> 
 <script> document.createElement("job"); </script>
 <![endif]-->
-->
```

Fuente: https://stackoverflow.com/questions/2802687/is-there-a-way-to-create-your-own-html-tag-in-html5

Algunas respuestas en hilos similares sugieren que es una buena idea crear el elemento independiemente de que el navegador sea o no IE:

```js
var x = document.createElement('job');
xFoo.addEventListener('click', function(e) {
  alert('Thanks!');
});
```

### Conclusión

Es posible implementar _tags_ o etiquetas personalizadas a sabiendas de que pueden haber problemas en función de los navegadores y nos estaríamos saliendo de los estándares de la web.

Pese a que implementar etiquetas _custom_ facilitaría enormemente el mantenimiento de una web (tanto CSS como HTML), dudo que sea una buena idea a largo plazo.[^jordan]

[^jordan]: Según un artículo de [Jordan Brennan](https://dev.to/jfbrennan/custom-html-tags-4788) no habría ningún problema, es más, es incluso aconsejable

Se puede obtener un resultado similar y que respete los estándares con los [Web Components](https://developer.mozilla.org/es/docs/Web/Web_Components)[^wc], pero a costa de la simplicidad que estabamos buscando en un principio.

[^wc]: Especificación en desarrollo que permite a los desarrolladores crear sus propias etiquetas HTML y registrarlas con el parser del navegador. Mozilla ha desarrollado una librería para facilitar el proceso: x-tags.org


	