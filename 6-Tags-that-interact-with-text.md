# Etiquetas que interactúan con el texto

## La etiqueta `p`

Define un parágrafo de texto.

```html
<p>Algún texto</p>
```

Es un elemento en bloque.

Dentro, podemos agregar cualquier elemento en línea que queramos, como un `span` o `a`.

No podemos agregar elementos en bloque. Tampoco podemos crear un elemento `p` dentro de otro.

Por defecto, los navegadores dan estilo a los parágrafos con un margen arriba y debajo del mismo. Es de `16px` en Chrome, pero el valor exacto puede variar entre navegadores.

Esto causa que dos parágrafos consecutivos estén espaciados entre ellos, replicando lo que esperaríamos de un "parágrafo" en medios como un periódico.

## La etiqueta `span`

Es una etiqueta en línea que puede ser usada para crear una sección en un parágrafo para que pueda ser modificada con CSS:

```html
<p>Una parte del texto <span>y aquí otra</span></p>
```

## La etiqueta `br`

Esta etiqueta representa un salto de línea. Es un elemento en línea, y no necesita una etiqueta de clausura.

La usamos para crear saltos de línea dentro de una etiqueta `p`, sin crear un nuevo parágrafo.

Y, comparados con un nuevo parágrafo, no necesitan espaciado adicional.

```html
<p>Algo de texto<br>Una nueva línea</p>
```

## Etiquetas de encabezado

HTML nos provee 6 etiquetas de encabezado. De la más a la menos importante, tenemos `h1`, `h2`, `h3`, `h4`, `h5`, `h6`.

Tipicamente, una página tendrá un elemento `h1`, que será el título de la página. Luego, puede que tenga uno o más elementos `h2` dependiendo del contenido de la página.

Los encabezados, especialmente durante la organización de los mismos, son esenciales para el SEO, donde los motores de búsqueda los usan de diferentes maneras.

El navegador mostrará por defecto a la etiqueta `h1` con el tamaño de texto más grande, reduciéndolo a medida que el número cerca de `h` aumenta:

![](6-Tags-that-interact-with-text/Screen%20Shot%202019-06-11%20at%2019.46.57.png)

Todos los encabezados son elementos en bloque. No pueden contener otros elementos, solo texto.

## La etiqueta `strong`

Esta etiqueta es usada para marcar al texto que lleva dentro como *importante*. Vale notar esto porque no es una ayuda visual sino semántica, cuya interpretación dependerá del medio usado.

Los navegadores, por defecto, cambiarán el texto que tengan dentro a **negritas**.

## La etiqueta `em`

Esta etiqueta es usada para darle *énfasis* al texto que lleva dentro. Como `strong`, no es una ayuda visual sino semántica.

Los navegadores, por defecto, cambiarán el texto que tengan dentro a **cursiva**.

## Citas
La etiqueta HTML `blockquote` es útil para insertar citas en el texto. Es una etiqueta en bloque.

Los navegadores, por defecto, aplicarán un margen a un elemento `blockquote`. Chrome aplica un margen de 40px izquierdo y derecho, y un margen de 10px arriba y abado.

La etiqueta HTML `q` es usada también para citas, pero en línea.

## Línea horizontal

No está realmente basada en texto, pero la etiqueta `hr` suele ser usada dentro de una página para agregar una página horizontal en la misma.

Es útil para separar secciones de una página.

## Bloques de código

La etiqueta `code` es especialmente útil para mostrar código, debido a la fuente especial que le otorga al texto que tiene dentro.

Eso suele ser lo único que hacen los navegadores con el texto. Este es el CSS aplicado por Chrome:

```css
code {
    font-family: monospace;
}
```

Esta etiqueta es típicamente agregada dentro de una etiqueta `pre` tag, ya que el elemento `code` ignora el espacio y los saltos de línea, similar a la etiqueta `p`.

Chrome le da el siguiente estilo a la etiqueta `pre`:

```css
pre {
    display: block;
    font-family: monospace;
    white-space: pre;
    margin: 1em 0px;
}
```

lo que previene que el espacio en blanco colapse, haciéndolo un elemento en bloque.

## Listas

Tenemos 3 tipos de listas:

- listas sin ordenar
- listas ordenadas
- listas de definiciones

Las listas sin ordenar son creadas usando la etiqueta `ul`. Cada objeto en la lista es creado con la etiqueta `li`:

```html
<ul>
	<li>Primero</li>
	<li>Segundo</li>
</ul>
```

Las listas ordenadas son similares, solo que con la etiqueta `ol` en su lugar:

```html
<ol>
	<li>Primero</li>
	<li>Segundo</li>
</ol>
```

La diferencia entre ambas es que las listas ordenadas tienen un número antes de cada objeto:

![](6-Tags-that-interact-with-text/Screen%20Shot%202019-06-12%20at%2009.35.05.png)

Las listas de definición son un poco más diferentes. Están compuestas de un término y su descripción:

```html
<dl>
	<dt>Flavio</dt>
	<dd>El nombre</dd>
	<dt>Copes</dt>
	<dd>El apellido</dd>
</dl>
```

Típicamente son mostradas de la siguiente forma por los navegadores:

![](6-Tags-that-interact-with-text/Screen%20Shot%202019-06-12%20at%2009.45.21.png)

Debo admitir que no se ven tanto en el día a día como las dos anteriores, pero pueden ser útiles en algunas ocasiones.

## Otras etiquetas de texto

Hay otro número de etiquetas con propósitos de presentación:

- la etiqueta `mark` 
- la etiqueta `ins` 
- la etiqueta `del` 
- la etiqueta `sup`
- la etiqueta `sub`
- la etiqueta `small`
- la etiqueta `i`
- la etiqueta `b`

Este es un ejemplo de la la visualización aplicada por los navegadores:

![](6-Tags-that-interact-with-text/Screen%20Shot%202019-06-12%20at%2008.43.55.png)

Acá puede que se pregunte, ¿en qué se diferencia `b` de `strong`? ¿Y cómo es `i` diferente de `em`?

La diferencia radica en el significado semántico. Aunque `b` e `i` son instrucciones directas al navegador para que aplique un estilo en particular al texto, `strong` y `em` le da un significado especial, y queda de parte del navegador el estilo que le otorgue. Casualmente, es por defecto el mismo estilo de `b` e `i`, pero puede cambiarse usando CSS.

Todavía quedan algunas otras etiquetas relacionadas al texto por explicar, pero son muy poco usadas.
