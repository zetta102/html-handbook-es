# Etiquetas de contenedor y estructura de página

## Etiquetas de contenedor

HTML provee un conjunto de etiquetas contenedor. Estas etiquetas contienen un conjunto no especificado de otras etiquetas.

Tenemos:

- `article`
- `section`
- `div`

y puede ser difícil entender la diferencia entre ellas.

Veamos cuándo usar cada una de ellas.

### `article`

Esta etiqueta identifica una *cosa* que puede ser independiente de otras *cosas* en una página.

Por ejemplo, una lista de posts en la página principal.

O una lista de enlaces.

```html
<div>
	<article>
		<h2>Un post</h2>
		<a ...>Leer más</a>
	</article>
	<article>
		<h2>Otro post</h2>
		<a ...>Leer más</a>
	</article>
</div>
```

El límite no son solo las listas: un articulo puede ser el elemento principal de una página.

```html
<article>
	<h2>Un post</h2>
	<p>Contenido...</p>
</article>
```

Dentro de una etiqueta `article` deberíamos tener un título (`h1`-`h6`) y una

### `section`

Representa una sección de un documento. Cada sección tiene una etiqueta de encabezado (`h1`-`h6`), y luego la sección del _cuerpo_.

Ejemplo:

```html
<section>
	<h2>Una sección de la página</h2>
	<p>...</p>
	<img ...>
</section>
```

Es útil dividir un artículo largo en diferentes **secciones**.

No debería usarse como un elemento contenedor génerico, ya que ese es el trabajo de `div`.

### `div`

`div` es el elemento contenedor genérico:

```html
<div>
	...
</div>
```

Se suele agregar un atributo `class` o `id` a este elemento, para poder modelarlo con CSS.

Usamos `div` en cualquier lugar que necesitemos un contenedor, pero que las etiquetas existentes no se ajusten lo suficiente.

## Etiquetas relacionadas con la página

### `nav`

Está etiqueta es usada para crear el esqueleto que define la navegación de página. Dentro de ella suele agregarse una lista `ul` u `ol`:

```html
<nav>
	<ol>
		<li><a href="/">Home</a></li>
		<li><a href="/blog">Blog</a></li>
	</ol>
</nav>
```

### `aside`

La etiqueta `aside` es usada para agregar una pieza de contenido que está relacionado al contenido principal.

Una caja en la cual agregar una cita, por ejemplo. O una barra lateral.

Ejemplo:

```html
<div>
  <p>algún texto..</p>
  <aside>
    <p>Una cita..</p>
  </aside>
  <p>otro texto...</p>
</div>
```

Usar `aside` permite señalar que las cosas que contiene no son parte del flujo regular del documento.

### `header`

La etiqueta `header` representa la introducción (o también el resumen) de una página. Puede, por ejemplo, contener una o más etiquetas de encabezado (`h1`-`h6`), un resumen, o una imagen.

```html
<article>
  <header>
	  <h1>Título del Artículo</h1>
  </header>
  ...
</div>
```

### `main`

La etiqueta main representa la parte principal del artículo `main`:

```html
<article>
  ....
  <main>
    <p>....</p>
  </main>
</div>
```

### `footer`

La etiqueta `footer` se usa para determinar el pie de un artículo, o el pie de una página:

```html
<article>
 ....
  <footer>
    <p>Pie de nota..</p>
  </footer>
</div>
```
