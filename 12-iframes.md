# iframes

The `iframe` tag allows us to embed content coming from other origins (other sites) into our web page.

Technically, an iframe creates a new nested browsing context. This means that anything in the iframe does not interfere with the parent page, and vice versa. JavaScript and CSS do not "leak" to/from iframes.

Many sites use iframes to perform various things. You might be familiar with Codepen, Glitch or other sites that allow you to code in one part of the page, and you see the result in a box. That's an iframe.

You create one this way:

```html
<iframe src="page.html"></iframe>
```

You can load an absolute URL, too:

```html
<iframe src="https://site.com/page.html"></iframe>
```

You can set a set of width and height parameters (or set them using CSS) otherwise the iframe will use the defaults, a 300x150 pixels box:

```html
<iframe src="page.html" width="800" height="400"></iframe>
```

## Srcdoc

The `srcdoc` attribute lets you specify some inline HTML to show. It's an alternative to `src`, but recent and not supported in Edge 18 and lower, and in IE:

```html
<iframe srcdoc="<p>My dog is a good dog</p>"></iframe>
```

## Sandbox

The `sandbox` attribute allows us to limit the operations allowed in the iframes.

If we omit it, everything is allowed:

```html
<iframe src="page.html"></iframe>
```

If we set it to "", nothing is allowed:

```html
<iframe src="page.html" sandbox=""></iframe>
```

We can select what to allow by adding options in the `sandbox` attribute. You can allow multiple ones by adding a space in between. Here's an incomplete list of the options you can use:

* `allow-forms`: allow to submit forms
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
