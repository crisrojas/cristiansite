---
title: ¿Qué arquitectura debería usar para esta web?
date: 2019-07-19
---


Para responder es necesario listar (1) lo que quiero crear y conseguir con este sitio (2) mi workflow ideal.

1. Construir una plataforma monetizable, con contenido de mucha calidad, una red de conocimientos que aporten en todo momento al usuario la información específica que este necesita en función de su nivel (mucha para principiantes, poca para expertos) y con un workflow en el que la creación de contenido sea un camino de cero resistencia
2. Tener una flexibilidad total a la hora de organizar el contenido: transclusión y reutilización de lecciones en diferentes cursos.

Actualmente todo el contenido de esta web existe en una sola carpeta, la carpeta `content`.

Todas las notas existen en el mismo nivel, es decir, **no hay subcarpetas ni jerarquías**.

¿Cómo consigo organizarme y encontrar exactamente lo que busco en ese berenjenal?

Bueno, la respuesta es simple: Dado que puedo conectar cualquier nota a cualquier lugar del sitio web, simplemente creo una nota que enlaza a otras notas y que sirve cómo índice.

Así de fácil.

La ventaja de esto es que **no necesito preocuparme por la jerarquía ni la arquitectura de la información** <ins>sino que esta emerge solita y de forma natural con la acumulación de notas relacionadas entre ellas</ins>

La posibilidad de hacer una transclusión de contenido (es decir, incluir contenido de una o más notas dentro de otra) amplia exponencialmente la flexibilidad y posibilidades.

Así, en un artículo de blog, si un párrafo habla de algo que ya existe en el archivo, en vez de reescribir la misma información duplicándola en dos sitios, una simple transclusión es suficiente.

Y podemos ir mucho más allá: Sería posible usar la transclusión de contenido entre las lecciones de cursos (para una plataforma de cursos) haciendo posible la reutilización de una lección en diferentes cursos.

Entonces, si todo es tan flexible y perfecto, ¿por qué crear una arquitectura?

Crear una carpeta separada para los cursos facilitaría las cosas a la hora de crear la lógica de la plataforma con Hugo.

Igualmente y aunque actualmente tengo artículos largos **dentro** del archivo de notas, no creo que a largo plazo sea una buena idea mezclar mi zettelkasten con notas largas, tengo la intuición de que lo ideal sería una arquitectura de este tipo:

```shell
├── notes
├── courses
├── components
├── blog
├── _index.md
├── now.md
└── cv.md
```

Dónde las notas existen dentro de la carpeta `notes` y las lecciones y artículos que están en un nivel superior "beben" de esas notas a través de transclusiones.

Sin embargo, esto genera ciertos problemas con la lógica (programación) que he implementado hasta ahora:

**Transclusión**

Al hacer una transclusión se necesita la ruta exacta del archivo. Dado que "blog" y "courses" ya no están al mismo nivel que "notes", tendría que especificar la ruta:

```shell
❌ {{ include "mi-nota.md" }} // Ya no funciona!
✅ {{ include "notes/mi-nota.md" }}
```

O al menos eso creo (puede que al estar en un nivel superior no haga falta especificar la carpeta)

Y esto genera un problema con los *backlinks*, y es que, el *shortcode* de transclusión incluye un wikilink de la nota transcludida, pero no con su nombre, sino con su **ruta**. Habría que modificarlo para que solo se incluya el nombre del fichero.


**Wikilinks**

Los wikilinks funcionan únicamente entre elementos que están al mismo nivel (es decir, en la misma carpeta)

No sería posible enlazar una nota del zettelkasten desde las lecciones presentes en la carpeta "courses" o artículos de la carpeta "blog".

A menos que...

Hagamos una ligera modificación al regex correspondiente para que los wikilinks dentro de las carpetas externas al archivo se rendericen con un `href="notes/{$1}.html"`

En ese caso perderíamos la habilidad de enlazar ficheros presentes en la misma carpeta, aunque podríamos tener dos síntaxis:

- Monobrackets para enlazar los ficheros de forma relativa. `href="{$1}.html"`
- Doblebracktes para enlazar los ficheros del zettelkasten. `href="notes/{$1}.html"`

Para los monobrackets tendríamos que ampliar la función de los backlinks:


```go

{{ $wikilink := ... }}

...

{{ $bracketStart := "[" }}
{{ $braketEnd := "]" }}
{{ $fileName := .File.BaseName }}

{{ $bracketsLink := print "s%s%s%" $bracketStart $filename $bracketEnd }} 

{{ if or (findRE $wikilink) (findRE $bracketsLink) }}
```

### Carpeta cursos

En el caso de los cursos, la estructura de los ficheros sería algo así:

```shell
├── courses
│	├── _index.md	
│	├── course1
│		├── _index.md
│		├── lesson1.md
│		├── lesson2.md
│	├── course2
│		├── _index.md
│		├── lesson1.md
```

Si quisiese conservarlos dentro de la carpeta notes. Tendría que:

1. Crear una carpeta courses con un layout `list.html`  y otro layout ` single.html` 
2. En cada nota del curso tendría que especificar en el yaml ` type: course` , también ` layout: list.html`  

Sin embargo, en el template `list.html`  tendría que complicarme muchísimo la vida para recuperar la lista de lecciones correspondientes a cada curso (si es que es realmente posible)

Otra opción sería crear una simple nota índice para cada curso.

Es decir, algo así:

```shell
├── notes
│	├── 20200718212157.md
│	├── 20200718212159.md
│	├── ...
│	├── indice-curso-1.md	
│	├── ...
│	├── lección-curso-1.md	
```

Dónde `indice-curso-1.md`  contiene un wikilink que enlaza al archivo `leccion-curso-1.md` 

Sin embargo, dado que quiero proteger el contenido y la manera más rápida es usar una solución cómo [Memberstack](//memberstack.io) o [Memberspace](//memberspace.com) tendría que reescribir las URL de las lecciones para que en vez de ser accesibles a través de `notas/mi-lección.html` , sean accesibles a través de `mi-curso/mi-lección.html` lo que invalidaría los wikilinks que enlazaran a estas lecciones desde cualquier otra nota.

Realmente, no creo que sea tan importante que los wikilinks funcionen entre ficheros que no sean notas del zettelkasten, puesto que (1) si los quiero enlazar entre ellos, basta con usar enlaces tradicionales y (2) no es interesante habilitar backlinks entre ellos.

Lo que sí es importante es que los artículos/cursos que enlacen o hagan transclusión de notas del archivo sean recogidos en la sección backlinks de las notas que enlazan/transcluden.


### Componentes y artículos.

Disfruto mucho empezar a escribir artículos (más bien contenido en general) dentro de [The Archive](https://zettelkasten.de/https://zettelkasten.de/the-archive/) por lo que todavía no sé si es buena idea cambiar mi workflow (si muevo los artículos a una carpeta, ya no podría empezar a escribir desde *The Archive*)

Sin embargo, si no los muevo y meto mi archivo en una carpeta `notas` , sus URL se verán afectadas por la migración: `notes/mi-articulo.html` 

Tendría que redefinir en cada artículo la URL lo cual rompería los wikilinks.

Es decir, para el `artículo-1`

```yaml
---
title: Artículo 1
url: blog/articulo-1
---
```

Si intentásemos enlazarlo desde otra nota:

```shell
# Nota 1

[[articulo-1]] ❌
```

El wikilink renderizaría con un `href="notes/articulo-1.html`  cuando la URL es `misitio.com/blog/articulo-1` 

### Conclusión

**Estructura de carpetas**

Carpeta1 <-> Carpeta1 

(si los ficheros no reescriben las url en el yaml)

- ✅ Wikilinks (urls relativas)
- ✅ Transclusión (urls relativas)
- ✅ Backlinks


Carpeta1 <-> Carpeta1/Subcarpeta

- ❌ Wikilinks (urls relativas)
- ✅ Transclusión (¿rutas absolutas?)
- ✅ Backlinks

Carpeta1 -> Carpeta2 || subcarpeta1 -> subcarpeta2

- ❌ Wikilinks 
- ✅ Transclusión (rutas absolutas)
- ✅ Backlinks

Sin embargo, me doy cuenta de que no podría usar la transclusión como quería: Compartir lecciones entre cursos.

Digamos que tengo una carpeta para el curso `curso1` y otra para el curso `curso2`.

Digamos que quiero usar la lección  `lección-3` del `curso1` como la lección n°4 del `curso2`, tal como está dispuesto el sistema, tendría que: (1) crear un fichero `lección-4.md` y dentro de ese fichero hacer una transclusión de la `lección-3`. Es decir, tendría que crear un fichero nuevo.

¿Y si pusiera todas las lecciones de todos los cursos al mismo nivel? 

Tendríamos la situación 1! y sería una muy buena opción para organizar el contenido y reusar las lecciones.

En lugar de usar una carpeta para estructurar el contenido de un curso, tendríamos un fichero 
 `curso1.md` y `curso2.md` con las notas referenciadas.
 
El problema: creo que toda la carpeta "cursos" tendría que ser privada (al usar "Memberstack" has de a elegir una carpeta "premium")

Aunque...

Una solución podría ser crear aliases en cada lección.

Es decir, digamos que tengo un `curso-gratis` y un `curso-premium`

Quiero incluir la misma lección `leccion.md` en ambos cursos. En el yaml de esta lección podría incluir lo siguiente:

```yaml
title: Lección de la escuela de la vida
alias: curso-premium/leccion
url: curso-gratis/leccion
```

La lección se renderizaría en ambas urls, y sólo una estaría bloqueada.

Pero engendraríamos otro problema (esto parece no tener fin): ¡el menú del curso!

Tal vez podríamos crear un menu en el yaml, tal que para el `curso1.md` :

```yaml
title: Curso 1
type: list
layout: course
menu:
    - curso1/leccion1
    - curso1/leccion2
    - curso1/leccion3
    - curso1/leccion4
    - ...
    - curso1/leccion26
```

Y en el layout `list/course.html` podríamos iterar en los elementos del menu, algo así como:


```go
{{ if .Page.Params.menu }}
   <a href="{{ . }}">Link lección</a>
{{ end }}
```
 
 Y tenemos otro problema: ¡El texto que mostraremos en el link!
 
 Podríamos solucionarlo con 
 
```yaml
title: Curso 1
type: list
layout: course
menu:
    - item1: 
        - url: curso1/leccion1
        - title: Lección 1
        - format: video
    - item2:
        - url: curso1/leccion2
        - title: Lección 2
        - format: text
```

Y en el layout `list/courses.html` :

```go
{{ if .Page.Params.menu }}
   <a href="{{ .Page.Params.menu.url }}">{{ .Page.Params.menu.title }}</a>
{{ end }}
```
 
### Una idea para separar los backlins de la transclusión

En el shortcode `include.html` podemos hacer lo siguiente:

```html
<!-- transcluded:{{ $file }}> -->
```

Y en el partial `backlinks.html` lo siguiente:

```go
{{ $transcludeStart := "transcluded:" }}
{{ $transcluded print "s%s%" $transcludeStart $filename }}

<h3>Transcluded in:</h3>

{{ if (findRE $transcluded) }}
<a href="{{ .Permalink }}">{{ .Title }}</a>
{{ end }}
```

### Conclusión

Si usamos esta metodología podríamos incluso guardar los cursos al mismo nivel, es decir en la misma carpeta del archivo.
 
1. Voy a usar una estructura de carpetas, al menos para los cursos
2. Todas las carpetas externas al zettelkasten usarán wikilinks únicamente funcionales con las notas de este último (ligera modificación al regex específico de esas carpetas). De esta manera conservaremos los backlinks.
3. He de hacer una pequeña modificación al shortcode de transclusión. De esta manera conservaremos los backlinks si las notas son transcludidas desde sitios ajenos al *Zettelkasten*

