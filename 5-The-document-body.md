# La etiqueta ´body´

Después de cerrar la etiqueta ´head´, solo podemos tener una etiqueta más en un documento HTML: el elemento `body`.

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

Tal como las etiquetas `head` y `html`, solo podemos tener una etiqueta ´body´ en una página.

Dentro de la etiqueta `body` tenemos todas las etiquetas que definen el contenido de la página.

Técnicamente, las etiquetas de apertura y clausura son opcionales, pero considero que es una buena práctica agregarlas solo por cuestiones de claridad.

En los próximos capítulos definiremos la variedad de etiquetas que se pueden usar dentro del cuerpo de la página.

Pero antes, debemos presentar la diferencia entre elementos de bloque y elementos de línea.

## Bloques o líneas

Los elementos visuales, que están definindos en el cuerpo de la página, pueden ser generalmente clasificados en dos categorías:

- elementos en bloque (`p`, `div`, listas y sus objetos, ...)
- elementos en línea (`a`, `span`, `img`, ...)

¿Cuál es la diferencia?

Los elementos en bloque, al posicionarse en la página, no permiten otros elementos cerca de ellos,. ya sea a la derecha o izquierda.

Los elementos en línea, en su lugar, pueden estar cerca de otros elementos en línea.

La diferencia también yace en las propiedades visuales que podemos editar usando CSS. Podemos alterar la altura/anchura, margen interno/externo y el borde de los elementos en bloque, mientras que no podemos en el caso de los bloques en línea.

> Nótese que usar CSS permite cambiar los valores por defecto de los elementos, haciendo que una etiqueta `p` esté en línea, o que un elemento `span` esté en bloque.

Otra diferencia es que los elementos en línea pueden estar dentro de elementos en bloque, pero no al revés.

Algunos elementos en bloque pueden contener otros elementos en bloque, pero depende de cada caso. La etiqueta `p`, por ejemplo, no permite tal opción.
