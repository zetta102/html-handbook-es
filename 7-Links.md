# Enlaces

Los enlaces son definidos usando la etiqueta `a`. El destino del enlace estará en su atributo `href`.

Ejemplo:

```html
<a href="https://flaviocopes.com">haz click aquí</a>
``

Entre la etiqueta de apertura y de clausura tendremos el texto del enlace.

El ejemplo de arriba es una dirección absoluta, aunque los enlaces también sirven con direcciones relativasThe above example is an absolute URL. Links also work with relative URLs:

```html
<a href="/test">haz click aquí</a>
```

En este caso, al hacer click en el enlace, el usuario es movido a la dirección `/test`, partiendo desde el punto actual.

Tenga cuidado con el caracter '/'. Si es omitido, en lugar de comenzar desde la raíz, el navegador solo agregará la palabra 'test' a la dirección actual.

Por ejemplo, si estoy en la página `https://flaviocopes.com/axios/` y tengo los enlaces `/test` y `test`:

- `/test` me llevará a `https://flaviocopes.com/test`
- `test` me llevará a `https://flaviocopes.com/axios/test`

Las etiquetas de enlace pueden contener otras cosas dentro aparte del texto. Por ejemplo, imágenes:

```html
<a href="https://flaviocopes.com">
	<img src="test.jpg">
</a>
```

o cualquier otro elemento, excepto otras etiquetas `a`.


Si desea que el enlace se abra en una nueva ventana, puede usar el atributo `target`:

```html
<a href="https://flaviocopes.com" target="_blank">abrir en nueva ventana</a>
```
