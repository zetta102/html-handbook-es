# Imàgenes

Las imàgenes pueden ser mostradas usando la etiqueta `img`.

Esta etiqueta acepta un atributo `src`, usado para configurar la fuente de la imagen:

```html
<img src="image.png">
```

Podemos usar una amplia cantidad de imàgenes, estando las màs comunes en formato PNG, JPEG, GIF, SVG y, màs recientemente, en WebP.

El estàndar HTML requiere que esté presente un atributo `alt` que describa el contenido de la imagen. Esto es usado tanto por herramientas de lectura de pantalla como por bots de motores de búsqueda:

```html
<img src="dog.png" alt="Una foto de un perro">
```

Puede cambiar los atributos `width` y `height` para configurar el espacio que el elemento tomará, de manera que el navegador pueda tomarlo en cuenta y no cambie la interfaz al terminarse de cargar. Toma un valor numérico, expresado en píxeles.

```html
<img src="dog.png" alt="Una foto de un perro" width="300" height="200">
```

## La etiqueta `figure`

La etiqueta `figure` suele ser usada con la etiqueta `img`.

`figure` es una etiqueta semántica que suele usarse cuando se busca mostrar una imagen con pie de foto. Se usa de la siguiente manera:

```html
<figure>
    <img src="dog.png"
         alt="Un buen chico">
    <figcaption>Un buen chico</figcaption>
</figure>
```

La etiqueta `figcaption` ajusta el texto del pie de foto.

## Imágenes responsivas usando `srcset`

El atributo `srcset` te permite configurar imágenes responsivas que el navegador puede usar dependiendo de la densidad de píxeles o la anchira de la ventana, de acuerdo a sus preferencias. De esta manera, solo podrá descargar los recursos que necesite para mostrar la página, sin descargar una imagen grande si está en un dispositivo móvil, por ejemplo.

Acá un ejemplo, donde damos 4 imágenes adicionales para 4 tamaños de pantalla diferentes:

```html
<img src="dog.png"
	alt="Una foto de un perro"
	srcset="dog-500.png 500w,
	  		 dog-800.png 800w,
			 dog-1000.png 1000w,
			 dog-1400.png 1400w">ventana de
```

En `srcset` usamos la medida `w` (del inglés _width_) para indicar la anchura de la ventana.

Ya que lo hacemos, también debemos usar el atributo `sizes`:

```html
<img src="dog.png"
	alt="Una foto de un perro"
	sizes="(max-width: 500px) 100vw, (max-width: 900px) 50vw, 800px"
	srcset="dog-500.png 500w,
	  		 dog-800.png 800w,
			 dog-1000.png 1000w,
			 dog-1400.png 1400w">
```

En este ejemplo, la línea `(max-width: 500px) 100vw, (max-width: 900px) 50vw, 800px` en el atributo `sizes` describe el tamaño de la imagen en relación a la ventana del navegador, con múltiples condiciones separadas por una coma.

La condición `max-width: 500px ` configura el tamaño de la imagen en correlación con la anchura de la ventana del navegador. En resumen, si el tamaño de la ventana es < `500px`, muestra la imagen al 100% del tamaño de la ventana.

Si el tamaño de la ventana es más grande, pero < `900px`, muestra la imagen, pero al 50% del tamaño de la ventana.

Y si es incluso más grande, ajusta la imagen a `800px`.

La unidad de medida `vw` (del inglés _viewport width_) puede ser nueva para usted, y en resumen diremos que 1 `vw` es 1% de la anchura de la ventana, así que `100vw` es el 100% de la misma. También existe una medida `vh` (del inglés _viewport height_) que, como tal vez se imagine, es similar a `vw`, pero refiriéndose a la altura de la ventana, en lugar de su anchura.

Un sitio útil para generar las imágenes necesarias para `srcset` es [https://responsivebreakpoints.com/](https://responsivebreakpoints.com/).

## La etiqueta `picture`

HTML también nos otorga la etiqueta `picture`, que hace un trabajo similar a `srcset`, con diferencias muy sutiles pero importantes.

Puede usar `picture` cuando, en lugar de mostrar una versión más pequeña de la imagen, quiera cambiarla completamente. O usar un formato distinto.

El mejor caso que he encontrado es usarlo al mostrar una imagen en formato WebP, que no está todavia ampliamente soportado. En la etiqueta `picture` puede especificar una lista de imágenes, y éstas serán mostradas en orden, de manera que, en el siguiente ejemplo, los navegadores que soporten WebP usarán la primera, o JPG si no es el caso:

```html
<picture>
  <source type="image/webp" srcset="image.webp">
  <img src="image.jpg" alt="An image">
</picture>
```

> La etiqueta `source` define uno (o más) formatos para las imágenes. La etiqueta `img` se usa en caso que el navegador sea antiguo y no soporte la etiqueta `picture`.

En la etiqueta `source` dentro de `picture` puede agregarse un atributo `media` para configurar consultas multimedia (llamadas también _media queries_).

El ejemplo siguiente funciona más o menos como el ejemplo usado con `srcset`:

```html
<picture>
  <source media="(min-width: 500w)" srcset="dog-500.png" sizes="100vw">
  <source media="(min-width: 800w)" srcset="dog-800.png" sizes="100vw">
  <source media="(min-width: 1000w)" srcset="dog-1000.png"	sizes="800px">
  <source media="(min-width: 1400w)" srcset="dog-1400.png"	sizes="800px">
  <img src="dog.png" alt="Una imagen de un perro">
</picture>
```

Aunque funciona más o menos de la misma manera, lleva un poco más de código que la etiqueta `img`.

Esta etiqueta es muy reciente, pero ya es [soportada](https://caniuse.com/#search=picture) por todos los navegadores más populares, salvo Opera Mini e IE en todas sus versiones.

