# Etiquetas multimedia: `audio` y `video`

En esta sección quiero mostrarte las etiquetas `audio` y `video`.

## La etiqueta `audio`

Esta etiqueta le permite agregar audio a sus páginas HTML.

Este elemento puede tanto transmitir audio, por medio de `getUserMedia()`, o puede reproducir de alguna fuente de audio a la cual debe hacer referencia con un atributo `src`:

```html
<audio src="file.mp3">
```

Por defecto el navegador no muestra controles para este elemento, lo que significa que el audio solo será reproducido si se establece con reproducción automática (explicación al respecto más adelante) y el usuario no puede detenerlo, cambiar el volumen, o moverse a una posición específica del audio.

Para mostrar controles, puede agregar el atributo `controls`:

```html
<audio src="file.mp3" controls>
```

Los controles de esta etiqueta puede tener un aspecto visual personalizado.

Puede especificar el tipo MIME del archivo de audio usando el atributo `type`. Si no es agregado, el navegador intentará determinarlo de forma automática:

```html
<audio src="file.mp3" controls type="audio/mpeg">
```

Por defecto, un archivo de audio no se reproduce automáticamente. Agregue el atributo `autoplay` para darle esta funcionalidad:

```html
<audio src="file.mp3" controls autoplay>
```

> Nota: los navegadores móviles no permiten la reproducción automática

El atributo `loop` reinicia el archivo desde el minuto 0:00. Si no es agregado, la reproducción se detiene al terminarse:

```html
<audio src="file.mp3" controls autoplay loop>
```

También puede reproducir un archivo de audio con el volumen silenciado usando el atributo `muted` (no estoy muy seguro cuál pueda ser la utilidad de esto):

```html
<audio src="file.mp3" controls autoplay loop muted>
```

Usando Javascript puede 'escuchar' (detectar) varios eventos que puedan ocurrir en un elemento `audio`, siendo los más básicos:

- `play` cuando el archivo comience a reproducirse
- `pause` cuando la reproducción del archivo se pause
- `playing` cuando la reproducción de un archivo se continue
- `ended`	cuando la reproducción del archivo se termine

## La etiqueta `video`

Esta etiqueta le permite agregar contenido a su página de HTML.

Este elemento puede tanto transmitir video, por medio de `getUserMedia()` o **WebRTC**,  o puede reproducir de alguna fuente de video a la cual debe hacer referencia con un atributo `src`:

```html
<video src="file.mp4">
```

Tal como los archivos de audio, el navegador no muestra por defecto controles para este elemento, solo el video en cuestión.

Por defecto el navegador no muestra controles para este elemento, lo que significa que el audio solo será reproducido si se establece con reproducción automática (explicación al respecto más adelante) y el usuario no puede detenerlo, cambiar el volumen, o moverse a una posición específica del video.

Para mostrar los controles, puede agregar el atributo `controls`:

```html
<video src="file.mp4" controls>
```

Los controles de esta etiqueta puede tener un aspecto visual personalizado.

Puede especificar el tipo MIME del archivo de audio usando el atributo `type`. Si no es agregado, el navegador intentará determinarlo de forma automática:

```html
<video src="file.mp4" controls type="video/mp4">
```

Por defecto, un archivo de video no se reproduce automáticamente. Agregue el atributo `autoplay` para darle esta funcionalidad:

```html
<video src="file.mp4" controls autoplay>
```

Algunos navegadores también requieren el atributo `muted` (que hace exactamente lo mismo que si se aplicara a un archivo de audio) para poder reproducir automáticamente, de manera que el video se reproduce automáticamente solo si está silenciado por defecto:

```html
<audio src="file.mp3" controls autoplay muted>
```

El atributo `loop` reinicia el archivo desde el minuto 0:00. Si no es agregado, la reproducción se detiene al terminarse:

```html
<video src="file.mp4" controls autoplay loop>
```

También puede definir una imagen para que se vea por defécto antes que se reproduzca el video.

```html
<video src="file.mp4" poster="picture.png">
```

Si no está definida, el navegador mostrará el primero cuadro del vídeo apenas esté disponible.

Puede establecer los atributos `width` (anchura) y `height` (altura) para definir el espacio que el elemento tomará de manera que el navegador pueda tomarlo en cuenta para que no modifique la interfaz cuando termine de cargarse.
Toma un valor numérico, expresado en píxeles.

Usando Javascript puede 'escuchar' (detectar) varios eventos que puedan ocurrir en un elemento `audio`, siendo los más básicos:

- `play` cuando el archivo comience a reproducirse
- `pause` cuando la reproducción del archivo se pause
- `playing` cuando la reproducción de un archivo se continue
- `ended`	cuando la reproducción del archivo se termine
