# Bases de HTML

HTML es el lenguaje de marcado que usamos para estructural el contenido que consumimos en internet.

HTML se sirve al navegador de diferentes maneras. 
* Puede ser generado por una aplicación del servidor que lo construya dependiendo de la petición o de los datos de la sesión, como por ejemplo con Rails, Laravel o Django. 
* Puede ser generado por una aplicación de JavaScript del lado del cliente que genere HTML en su ejecución. 
* De manera más simple, puede ser almacenado en un archivo y servido al navegador por medio de un servidor web.

Vayamos a este último caso. Aunque en la práctica posiblemente es la forma menos popular para generar HTML, sigu siendo esencial conocer al menos los bloques más básicos.

Por convención,  un archivo HTML es guardado con una extensión `.html` o `.htm`.

Dentro de este archivo, organizamos el contenido usando **etiquetas** (o _tags_, en inglés).

Las etiquetas están alrededor del contenido, y cada una le da un significado especial al texto que rodea.

Hagamos algunos ejemplos.

Este fragmento de HTML crea un parágrafo usando la etiqueta `p`:

```html
<p>Un parágrafo de texto</p>
```

Este otro fragmento crea una lista de objetos usando la etiqueta `ul`, que significa *lista sin ordenar* (el nombre viene del inglés _unordered list_), y las etiquetas `li`, que significan *objeto de lista* (_list item_, en inglés):

```html
<ul>
  <li>Primer objeto</li>
  <li>Segundo objeto</li>
  <li>Tercer objeto</li>
</ul>
```

Cuando una página HTML es servida por el navegador, las etiquetas son interpretadas, y el navegador muestra los elementos de acuerdo con las reglas que definen su apariencia visual.

Algunas de estas reglas están estrablecidas de fábrica, como la manera en la que una lista se muestra o como un enlace está subrayado y en color azul.

Algunas otras reglas pueden ser establecidas por usted usando hojas de estilo en cascada, conocidas más comúnmente como CSS..

HTML no es un lenguaje de presentación. No se preocupa por cómo las cosas se *ven*, sino por qué *significan*.

Queda de parte del navegador determinar cómo se ven las cosas con las reglas establecidas por la persona que crea la página usando el lenguaje CSS.

Sin embargo, esos dos ejemplos eran fragmentos tomados fuera del contexto de una página real.

### Estructura de una página en HTML

Hagamos un ejemplo de una página en HTML real

Las cosas comienzan con la declaración del tipo de documento (conocido como _doctype_), una manera de decirle al navegador que lo que está "viendo" es una página HTML, así como la versión que está utilizándose.

El HTML moderno usa esta declaración de la siguiente manera:

```html
<!DOCTYPE html>
```

Luego tenemos el elemento `html`, que tiene una etiqueta de apertura y de clausura:

```html
<!DOCTYPE html>
<html>
...
</html>
```

La mayoría de las etiquetas viene en pares, con una etiqueta de apertura y de cerradura. La etiqueta de cerradura se escrible casi de la misma manera que la de clausura, pero con un `/`:

```html
<etiqueta>contenido</etiqueta>
```
Hay algunas etiquetas que no requieren etiquetas de clausura, dado que _no contienen_ nada dentro de ellas.

La etiqueta de apertura `html` se usa al principio del documento, después de la declaración del tipo de documento.

La etiqueta de clausura de `html` es lo último presente en un documento de HTML.

Dentro del elemento `html` tenemos dos elementos : `head` y `body`:

```html
<!DOCTYPE html>
<html>
	<head>
	...
	</head>
	<body>
	...
	</body>
</html>
```

Dentro de `head` tendremos etiquetas esenciales para la creación de una página web, como el título, los metadatos, el CSS interno o externo y el código de JavaScript. La mayoría de estas cosas no aparecen directamente en la página, sino que ayudan al navegador (o a los bots de búsqueda) a mostrarla apropiadamente.

Dentro de `body` tendremos el contenido de la página. Las **cosas visibles**.

### Etiquetas o elementos

Mencioné etiquetas y elementos. ¿Cuál es la diferencia?

Los elementos tienen una etiqueta de apertura y una de clausura. En este ejemplo, usaremos las etiquetas de apretura y clausura `p`para crear un elemento `p`:

```html
<p>Un parágrafo de texto</p>
```

Así, un elemento constituye el _paquete entero_:

- una etiqueta de apertura
- el texto de contenido (y posiblemente otras cosas)
- una etiqueta de clausura

Si un elemento no tiene una etiqueta de clausura, está solo escrito con la etiqueta de apertura y por esto no puede contener ningun texto.

Explicado esto, puedo usar ambos términos de manera intercambiable, a menos que explícitamente se mencione una etiqeuta de apertura o de clausura.

### Atributos

La etiqueta de apertura de un elemento puede tener fragmentos especiales de información que podemos agregarle, llamados **atributos**.

Los atributos tienen una sintaxis de `atributo="valor"`:

```html
<p class="una-clase">Un parágrafo de texto</p>
```

> También pueden usarse comillas simples, pero es una buena práctica usar comillas dobles en su lugar.

Podemos tener muchos de ellos:

```html
<p class="una-clase" id="un-id">Un parágrafo de texto</p>
```

algunos de los atributos son booleanos, lo que significa que solo se necesita el atributo:

```html
<script defer src="archivo.js"></script>
```

Los atributos `class` e `id` son de los que más te encontrarás.

Tienen un significado especial, y son útiles tanto en CSS como en JavaScript.

La diferencia entre ambos es que un `id` es único dentro del contexto de una página web, no puede ser duplicado.

Las clases, por otra parte, pueden aparecer múltiples veces en múltiples elementos.

Además, un `id` debe ser solo un valor. `class`, por su parte, puede contener múltiples valores, separados por un espacio:

```html
<p class="una-clase otra-clase">Un parágrafo de texto</p>
```

Es común usar guiones `-` para separar palabras en un valor de clase, pero no es obligatorio.

Esos son solo dos de los atributos que puede usar. Algunos de ellos pueden ser usados solo en ciertas etiquetas, ya que son altamente especializados.

Otros atributos pueden ser usados de manera más general. Justo acaba de ver dos de ellos, `id` y `class`, pero también tenemos otros, como `style`, que puede ser usado para agregar CSS dentro de un elemento (vale acotar que es una práctica no recomendada).

### ¿Mayúsculas o minúsculas?

En HTML, es irrelevante que se use unas u otras dentro de las etiquetas. Las etiquetas pueden ser escritas enteramente en mayúsculas o minúsculas. Otrora era común usar mayúsculas, pero hoy en día es común usar minúsculas.

Usualmente escribiría así:

```html
<p>Un parágrafo de texto</p>
```

y no así:

```html
<P>Un parágrafo de texto</P>
```

### White space

Pretty important. In HTML, white space is not relevant. Space is removed from the equation.

To the browser,

```html
<p>A paragraph of text</p>
```

is the same as

```html
<p>        A paragraph of text</p>
```

and the same as

```html
<p>A paragraph

of
           text          </p>
```

 
I'd say use the syntax that makes things visually more organized and easier to read, but you can use any syntax you like.

I typically favor

```html
<p>A paragraph of text</p>
```

or

```html
<p>
	A paragraph of text
</p>
```

Nested tags should be indented with 2 or 4 characters, depending on your preference:

```html
<body>
	<p>
		A paragraph of text
	</p>
	<ul>
		<li>A list item</li>
	</ul>
</body>
```

> Note: this "white space is not relevant" feature means that if you want to add additional space, it can make you pretty mad. I suggest you use CSS to make more space when needed.

> Note: in special cases, you can use the `&nbsp;` HTML entity (an acronym that means _non-breaking space_) - more on HTML entities later on. I think this should not be abused. CSS is always preferred to alter the visual presentation.
