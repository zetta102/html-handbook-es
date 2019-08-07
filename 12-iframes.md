# Iframes

La etiqueta `iframe` nos permite agregar contenido de origen distinto (otras páginas) a nuestra página web.

A nivel técnico, un iframe crea el contenido de forma anidada. Esto significa que el iframe no interfiere con la página original y viceversa. JavaScript y/o CSS no "gotean" desde/hacia los iframes.

Muchos sitios usan iframes para ejecutar varios procesos. Puede que conozca CodePen, Glitch u otros sitios que le permiten escribir código en una parte de la página, y luego ver el resultado en otra. Eso es un iframe.

Puede crear uno de la siguiente manera:

```html
<iframe src="page.html"></iframe>
```

También puede hacer referencia a una URL absoluta:

```html
<iframe src="https://site.com/page.html"></iframe>
```

Puede también establecer parámetros de altura y anchura. En caso que no lo haga, iframe usará los valores por defecto, una caja de 300x150 píxeles:

```html
<iframe src="page.html" width="800" height="400"></iframe>
```

## Srcdoc

El atributo `srcdoc` le permite especificar algún código HTML para mostrar. Es un alternativa a `src`, pero más reciente y no soportada por Edge 18 y versiones anteriores, así como por Internet Explorer:

```html
<iframe srcdoc="<p>My dog is a good dog</p>"></iframe>
```

## Sandbox

El atributo `sandbox` permite limitar las operaciones permitidas dentro de los iframes.

Si lo omitimos, todo estará permitido:

```html
<iframe src="page.html"></iframe>
```

Si lo establecemos en "", nada estará permitido:

```html
<iframe src="page.html" sandbox=""></iframe>
```

Podemos seleccionar las acciones que permitiremos al añadir opciones al atributo `sandbox`. Puede permitir múltiples acciones al agregarlas con un espacio entre ellas. Esta es una lista incompleta de las opciones posibles:

* `allow-forms`: permite enviar el contenido de las `forms`.
* `allow-modals`: permite abrir ventanas modales, incluyendo llamar a `alert()` en JavaScript.
* `allow-orientation-lock` permite bloquear la orientación de pantalla.
* `allow-popups` permite popups, usando `window.open()` y enlaces `target="_blank"`.
* `allow-same-origin` trata el recurso que está cargándose como si fuera del mismo origen.
* `allow-scripts` deja que el iframe cargado corra scripts (pero no que deje crear popups).
* `allow-top-navigation` da al iframe acceso al nivel superior de navegación.

## Allow

Actualmente experimental y solo soportado por navegadores basados en Chromium, es el futuro de intercambio de recursos entre la ventana padre y el iframe.

Es similar al atributo `sandbox`, pero permitiéndonos características más específicas, incluyendo:

- `accelerometer`, que da acceso a la interfaz API de acelerómetros.
- `ambient-light-sensor`, que da acceso a la interfaz API de AmbientLightSensor.
- `autoplay`, que permite reproducir automáticamente archivos de audio y video.
- `camera`, que da acceso a la cámara del dispositivo por medio de la interfaz API getUserMedia.
- `display-capture`, que permite acceder al contenido de la pantalla usando la API getDisplayMedia.
- `fullscreen`, que permite acceder al modo de pantalla completa.
- `geolocation`, que permite acceder a la API de geolocalización.
- `gyroscope`, que da acceso a la interfaz API del giroscopio.
- `magnetometer`, que da acceso a la interfaz API del magnetómetro.
- `microphone`, que da acceso al micrófono del dispositivo por medio de la interfaz API getUserMedia.
- `midi`, que da acceso a la API Web MIDI.
- `payment`, que da acceso a la API de petición de pagos.
- `speaker`, que da acceso a la reproducción de audio por medio de los altavoces del dispositivo.
- `usb`, que da acceso a la API WebUSB.
- `vibrate`, que da acceso a la API de vibración.
- `vr`, que da acceso a la API WebVR.

## Referrer

Al cargar un iframe, el navegador envía información importante sobre el usuario que lo carga con el encabezado de `Referer`.

El atributo `referrerpolicy` nos deja establecer la información del usuario a enviar al iframe cuando carga. Esta etiqueta es un encabezado HTTP que deja que la página sepa quién la está cargando. Estos son los valores permitidos:

- `no-referrer-when-downgrade`, que es el atributo por defecto, y envía la información cuando la página actual esté cargada sobre HTTPS y el iframe en HTTP.
- `no-referrer`, que no envía la información del encabezado.
- `origin`, que envía la información, y solo contiene el origen (puerto, protocolo y dominio), no solo el origen más la dirección, que suele ser la información que envía por defecto.
- `origin-when-cross-origin`, que envía la información del encabezado en su forma completa (origen + dirección) al cargarlo en una página del mismo dominio (puerto, protocolo y dominio). De otra manera, solo envía el origen.
- `same-origin`, la información se envía solamente si el iframe se carga desde el mismo dominio (puerto, protocolo y dominio).
- `strict-origin`, envía la información de origen como el encabezado si la página actual fue cargada sobre HTTPS y el iframe también. No envía nada si el iframe se envía sobre HTTP.
- `strict-origin-when-cross-origin`, envía el origen + dirección como infomación de encabezado al trabajar en el mismo origen. Envía el origen como infomación si la página actual se carga sobre HTTPS y el iframe también. No envía nada si el iframe se carga sobre HTTP.
- `unsafe-url`, que envía el origen + dirección como información incluso al cargar recursos sobre HTTP mientras que la página haya sido cargada sobre HTTPS.
