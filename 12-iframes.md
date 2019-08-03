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

* `allow-forms`: permite enviar el contenido de las `forms`
* `allow-modals` allow to open modals windows, including calling `alert()` in JavaScript
* `allow-orientation-lock` allow to lock the screen orientation
* `allow-popups` allow popups, using `window.open()` and `target="_blank"` links
* `allow-same-origin` treat the resource being loaded as same origin
* `allow-scripts` lets the loaded iframe run scripts (but not create popups).
* `allow-top-navigation` gives access to the iframe to the top level browsing context

## Allow

Currently experimental and only supported by Chromium-based browsers, this is the future of resource sharing between the parent window and the iframe.

It's similar to the `sandbox` attribute, but lets us allow specific features, including:

- `accelerometer` gives access to the Sensors API Accelerometer interface
- `ambient-light-sensor` gives access to the Sensors API AmbientLightSensor interface
- `autoplay` allows to autoplay video and audio files
- `camera` allows to access the camera from the getUserMedia API
- `display-capture` allows to access the screen content using the getDisplayMedia API
- `fullscreen` allows to access fullscreen mode
- `geolocation` allows to access the Geolocation API
- `gyroscope` gives access to the Sensors API Gyroscope interface
- `magnetometer` gives access to the Sensors API Magnetometer interface
- `microphone` gives access to the device microphone using the getUserMedia API
- `midi` allows access to the Web MIDI API
- `payment` gives access to the Payment Request API
- `speaker` allows access to playing audio through the device speakers
- `usb` gives access to the WebUSB API.
- `vibrate` gives access to the Vibration API
- `vr` gives access to the WebVR API

## Referrer

When loading an iframe, the browser sends it important information about who is loading it in the `Referer` header (notice the single `r`, a typo we must live with).

> The misspelling of referrer originated in the original proposal by computer scientist Phillip Hallam-Baker to incorporate the field into the HTTP specification. The misspelling was set in stone by the time of its incorporation into the Request for Comments standards document RFC 1945

The `referrerpolicy` attribute lets us set the referrer to send to the iframe when loading it. The referrer is an HTTP header that lets the page know who is loading it. These are the allowed values:

- `no-referrer-when-downgrade` it's the default, and sends the referrer when the current page is loaded over HTTPS and the iframe loads on the HTTP protocol
- `no-referrer` does not send the referrer header
- `origin` the referrer is sent, and only contains the origin (port, protocol, domain), not the origin + path which is the default
- `origin-when-cross-origin` when loading from the same origin (port, protocol, domain) in the iframe, the referrer is sent in its complete form (origin + path). Otherwise only the origin is sent
- `same-origin` the referrer is sent only when loading from the same origin (port, protocol, domain) in the iframe
- `strict-origin` sends the origin as the referrer if the current page is loaded over HTTPS and the iframe also loads on the HTTPS protocol. Sends nothing if the iframe is loaded over HTTP
- `strict-origin-when-cross-origin` sends the origin + path as the referrer when working on the same origin. Sends the origin as the referrer if the current page is loaded over HTTPS and the iframe also loads on the HTTPS protocol. Sends nothing if the iframe is loaded over HTTP
- `unsafe-url`: sends the origin + path as the referrer even when loading resources from HTTP and the current page is loaded over HTTPS
