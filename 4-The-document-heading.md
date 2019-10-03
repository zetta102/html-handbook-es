# La etiqueta head

Esta etiqueta contiene otras etiquetas especiales que definen las propiedades del documento.

Siempre se escribe antes de la etiqueta `body`, justo después de la etiqueta `html` de apertura:

```html
<!DOCTYPE html>
<html>
	<head>
		...
	</head>
	...
</html>
```

Nunca usamos atributos en esta etiqueta, tampoco escribimos contenido en ella, ya que es solo un contenedor para otras etiquetas.

Algunas de ellas son las siguientes, dependiendo de lo que necesite

- `title`
- `script`
- `noscript`
- `link`
- `style`
- `base`
- `meta`

### La etiqueta `title`

Esta etiqueta determina el título de la página. El mismo es mostrado en el navegador, y es especialmente importante ya que es parte esencial en el tema de la optimización de motor de búsqueda (o SEO, por sus siglas en inglés).

### La etiqueta `script`

Esta etiqueta es usada para agregar JavaScript a la página.

Puede agregarlo dentro del mismo documento, con una etiqueta de apertura, el código, y una etiqueta de clausura:

```html
<script>
..código JS
</script>
```

O, alternativamente, puede cargar un archivo JavaScript externo usando el atributo `src`:

```html
<script src="archivo.js"></script>
```

> El atributo `type`, por defecto, está configurado como `text/javascript`, así que es completamente opcional.

Hay un detalle bastante importante respecto a esta etiqueta.

Suele ser colocada, si existe, al final de la página, justo antes de la etiqueta `</body>` de clausura. ¿Por qué? Por cuestiones de rendimiento.

Al cargar código JS (o scripts), el navegador bloquea por defecto la visualización de la página hasta que el script esté interpretado y cargado.

Al colocarlo al fondo de la página, es cargado y ejecutado después que la página haya sido interpretada y cargada, otorgando una mejor experiencia al usuario que si estuviera en la etiqueta `head`.

En mi opinión, estas son malas prácticas hoy en día. No hay problemas en dejar que las etiquetas `script` estén dentro de `head`.

En el JS moderno, tenemos una alternativa mejor que dejar los scripts al final, siendo este el atributo `defer`. Este es un ejemplo que carga un `archivo.js`, relativo a la dirección actual: 

```html
<script defer src="archivo.js"></script> 
```

Con esto, se tiene un escenario que llevará a un camino más rápido para cargar tanto la página como el JavaScript.

### La etiqueta `noscript`

Esta etiqueta es usada para detectar si los scripts están deshabilitados por el navegador.

> Nota: los usuarios pueden elegir deshabilitar los scripts de JS en los ajustes del navegador, así como también puede que el navegador no los soporte por defecto.

Se usa de manera distinta dependiendo del lugar en el que se ponga, pudiendo ser dentro de la etiqueta `head` o dentro de la etiqueta `body`.

Ya que estamos hablando de la etiqueta, presentaré su uso.

En este caso, la etiqueta `noscript` solo puede contener etiquetas:

- `link`
- `style`
- `meta`

para alterar los recursos servidos por la página, en caso que los scripts estén deshabilitados.

En este ejemplo, establezco un elemento con la clase `no-script-alert` a mostrarse si los scripts están desactivados, ya que tiene la clase de CSS `display: none` por defecto:

```html
<!DOCTYPE html>
<html>
	<head>
		...
		<noscript>
			<style>
				.no-script-alert {
					display: block;
				}
			</style>
		</noscript>

		...
	</head>
	...
</html>
```

> Por otra parte, si se pone dentro de la etiqueta `body`, puede contener parágrafos u otras cosas para ser mostradas en la interfaz de usuario.

### La etiqueta `link`

Es usada para establecer relaciones entre un documento y otros recursos.

Es usada principalmente para enlazar y permitir cargar un archivo de CSS externo.

Este elemento no tiene etiqueta de clausura.

Uso:

```html
<!DOCTYPE html>
<html>
	<head>
		...
		<link href="archivo.css" rel="stylesheet">
		...
	</head>
	...
</html>
```

El atributo `media` permite cargar diferentes hojas de estilo dependiendo de las capacidades del dispositivo:

```html
<link href="file.css" media="screen" rel="stylesheet">
<link href="print.css" media="print" rel="stylesheet">
```

También se pueden lanzar otros contenidos además de hojas de estilo.

Por ejemplo, podemos enlazar una fuente RSS usando

```html
<link rel="alternate" type="application/rss+xml" href="/index.xml">
```

O podemos enlazar un favicon usando:

```html
<link rel="apple-touch-icon" sizes="180x180" href="/assets/apple-touch-icon.png">

<link rel="icon" type="image/png" sizes="32x32" href="/assets/favicon-32x32.png">

<link rel="icon" type="image/png" sizes="16x16" href="/assets/favicon-16x16.png">
```

Esta etiqueta _fue_ usada por Google para contenido multipágina, para indicar la página anterior y previa, usando `rel="prev"` y `rel="next"`. Hasta el momento de la escritura de este libro (2019), [Google anunció que ya no usa más esta etiqueta](https://twitter.com/googlewmc/status/1108726443251519489), ya que puede encontrar la estructura correcta del libro sin ella.

### La etiqueta `style`

Puede ser usada para agregar estilos al documento, en lugar de cargar una hoja de estilos externa.

Uso:

```html
<style>
.algun-css {}
</style>
```


Como con a etiqueta `link`, peude usar el atributo `media` para ajustar dónde se usará, específicamente, ese CSS:

```html
<style media="print">
.some-css {}
</style>
```

### La etiqueta `base`

Es usada para establecer una dirección base para todas las direcciones relativas contenidas en la página.

```html
<!DOCTYPE html>
<html>
	<head>
		...
		<base href="https://github.com/zetta102">
		...
	</head>
	...
</html>
```

### La etiqueta `meta`

Las etiquetas meta ejecutan una variedad de importantes tareas, especialmente en cuando a SEO se refiere.

Los elementos `meta` solo tienen una etiqueta de apertura.

La más básica es la etiqueta meta de `description`, usada para describir algo:

```html
<meta name="descripción" content="Una bonita página">
```

Esto "puede" ser usado por Google para generar la descripción de la página en sus resultados de búsqueda, en caso que lo encuentre mejor que el contennido dentro de la misma (no me pregunte cómo).

La etiqueta meta de `charset` es usada para establecer la codificación de los caracteres de la página. Suele ser `utf-8` en la mayoría de los casos:

```html
<meta charset="utf-8">
```

La etiqueta meta de `robots` instruye al motor de búsqueda respecto a la posibilidad (o no) de indexar una página (en otras palabras, mostrarla en los resultados de búsqueda del respectivo motor):

```html
<meta name="robots" content="noindex">
```

O si deberían seguir los enlaces o no (esto significa pedir que los enlaces sean [o no] indexados por el motor de búsqueda):

```html
<meta name="robots" content="nofollow">
```

> También puede establecerlo con enlaces individuales. Esta es una manera de establecerlo globalmente.

También se pueden combinar:

```html
<meta name="robots" content="noindex, nofollow">
```

El comportamiento por defecto es `index, follow`.

También puede usar otras propiedades, como podrían ser `nosnippet`, `noarchive`, `noimageindex` y más.

También puede simplemente 'hablar' con Google en lugar de *todos* los motores de búsqueda:

```html
<meta name="googlebot" content="noindex, nofollow">
```

Y otros motores de búsqueda podrían también tener sus propias etiquetas meta.

Hablando de ello, podemos pedirle a Google que deshabilite algunas características. Esto previene, por ejemplo, que se active la funcionalidad de traducción en los resultados del motor de búsqueda:

```html
<meta name="google" content="notranslate">
```

La etiqueta meta `viewport` es usada para decirle al navegador que estableca la anchura de la página en base a la del dispositivo.

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

Otra etiqueta meta bastante popular es `http-equiv="refresh"`. En este caso, pide que el navegador redirija a otra página después de esperar 3 seg:

```html
<meta http-equiv="refresh" content="3;url=http://otra-pagina.com>
```

Usar 0, redirigirá tan rápido como sea posble.

Vale acotar que no es una referencia completa, existen otras etiquetas meta menos usadas.

Después de este deocumento, podremos ahondar en el cuerpo del mismo.
