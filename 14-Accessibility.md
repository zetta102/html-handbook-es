# Accesibilidad

Es importante que diseñemos nuestro HTML con la accesibilidad en mente.

Tener un HTML con esto en mente significa que las personas con discapacidad puedan usar tu página. Existen personas completa o parcialmente invidentes, personas con pérdida auditiva y una multitud de otras diferentes discapacidades.

Desafortunadamente, no suele dársele a esta sección la importancia que requiere, ya que no es tan llamativa como las demás.

¿Qué pasaría si una persona que no puede *ver* tu página quiere consumir su contenido? En primer lugar, ¿cómo lo hacen? No pueden usar el ratón, usan algo llamado **lector de pantalla**. No tiene por qué imaginárselo cuando puede probarlo. Google provee la extensión gratuita de Chrome, [ChromeVox](https://chrome.google.com/webstore/detail/chromevox/kgejglhpjiefppelpmljglcjbhoiplfn/). La accesibilidad también debe tomar en cuenta que se permita a estas herramientas seleccionar los elementos o navegar por las páginas con tranquilidad.

Las páginas y aplicaciones web no son siempre construidas con la accesibilidad como una de sus primeras metas y, aunque tal vez la versión 1 no tenga este acercamiento, puede hacerse accesible en una iteración futura. Mientras antes se haga, mejor, pero nunca es demasiado tarde.

Es importante tomar esto siempre en cuenta, especialmente cuando se habla de contenido de interés público, como puede ser las páginas web de los gobiernos u otras organizaciones públicas.

¿Qué significa hacer una página HTML accesible? Déjeme ilustrarle las cosas principales que debe tomar en cuenta.

> Nota: hay una gran cantidad de cosas extra para tomar en cuenta, pero van dentro de otra sección, dedicada a CSS, como podría ser los colores, el contraste y las fuentes. O tal vez [cómo hacer las imágenes en formato SVG accesibles](https://css-tricks.com/accessible-svgs/). No hablaremos de esto en este libro.

## Uso de HTML semático

El HTML semático es importantísimo, y una de las cosas principales que usted debería hacerse cargo al crear una página. Déjeme ilustrar algunos escenarios comunes.

Es importante usar la estructura correcta para las etiquetas de escritura. La más importante es `h1`, siendo otros números usados para información menos importante, pero todas las del mismo nivel deberían tener el mismo significado (piense en ello como en la estructura de un árbol):

```
h1
	h2
		h3
	h2
	h2
		h3
			h4
```

Use `strong` y `em` en lugar de `b` e `i`, respectivamente. Tienen el mismo aspecto visual, pero las dos primeras tienen significado semántico asociado a ellas. `b` e `i` son elementos mas visuales.

Las listas también son parte importante en la accesibillidad. Un lector de pantalla puede detectar uan lista y proveer un resumen, dejando luego que el usuario decida leer el resto o no.

Una tabla debería tener una etiqueta `caption` que describa su contenido:

```
<table>
  <caption>Edad de los perros</caption>
  <tr>
    <th>Perro</th>
    <th>Edad</th>
  </tr>
  <tr>
    <td>Roger</td>
    <td>7</td>
  </tr>
</table>
```

## Use atributos `alt` para las imágenes

Todas sus imágenes deben tener un atributo `alt` que describa el contenido de la misma. No solo es una buena práctica, es requerido por el estándar HTML y su HTML no estará validado sin esto.

```html
<img src="dog.png" alt="Una foto de mi perro">
```

También ayuda al SEO, así que es otro incentivo para agregarlo.

## Use el atributo `role`

Este atributo `role` le permite asignar roles específicos a los varios elementos de su página.

Puede asignar un montón de roles distintos, eso sí, todos en perfecto inglés, por lo que puede que tener un diccionario a la mano le ayude.

Son un montón, y para una completa referencia de cada uno, le entrego este [enlaze de MDN](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles). Pero tampoco es necesario asignar un rol a cada elemento de la página. Los lectores de pantalla pueden inferirlo de la etiqueta HTML en la mayoría de los casos. Por ejemplo, no necesita agregar este atributo a etiquetas como `nav`, `button` o `form`.

Let's take the `nav` tag example. You can use it to define the page navigation like this:

```html
<nav>
  <ul>
    <li><a href="/">Home</a></li>
    <li><a href="/blog">Blog</a></li>
  </ul>
</nav>
```

If you were *forced* to use a `div` tag instead of `nav`, you'd use the `navigation` role:

```html
<div role="navigation">
  <ul>
    <li><a href="/">Home</a></li>
    <li><a href="/blog">Blog</a></li>
  </ul>
</div>
```

So here you got a practical example: `role` is used to assign a meaningful value when the tag does not convey the meaning already.

## Use the `tabindex` attribute

The `tabindex` attribute allows you to change the order of how pressing the Tab key selects "selectable" elements. By defaults only links and form elements are "selectable" by navigation using the Tab key (and you don't need to set `tabindex` on them).

Adding `tabindex="0"` makes an element selectable:

```html
<div tabindex="0">
...
</div>
```

Using `tabindex="-1"` instead removes an element from this tab-based navigation, and it can be pretty useful.

## Use the `aria` attributes

ARIA is an acronym that means Accessible Rich Internet Applications and defines semantics that can be applied to elements.

### `aria-label`

This attribute is used to add a string to describe an element.

Example:

```html
<p aria-label="The description of the product">...</p>
```

I use this attribute on my blog sidebar, where I have an input box for search without an explicit label, as it has a placeholder attribute.

### `aria-labelledby`

This attribute sets a correlation between the current element and the one that labels it.

If you know how an `input` element can be associated to a `label` element, that's similar.

We pass the item id that describes the current element.

Example:

```html
<h3 id="description">The description of the product</h3>

<p aria-labelledby="description">
...
</p>
```

### `aria-describedby`

This attribute lets us associate an element with another element that serves as description.

Example:

```html
<button aria-describedby="payNowDescription" >Pay now</button>

<div id="payNowDescription">Clicking the button will send you to our Stripe form!</div>
```

### Use aria-hidden to hide content

I like a minimalistic design in my sites. My blog for example is mostly just content, with some links in the sidebar. But some things in the sidebar are just visual elements that don't add up to the experience of a person that can't see the page. Like my logo picture, or the dark/bright theme selector.

Adding the `aria-hidden="true"` attribute will tell screen readers to ignore that element.

## Where to learn more

This is just an introduction to the topic. To learn more, I recommend these resources:

- [https://www.w3.org/TR/WCAG20/](https://www.w3.org/TR/WCAG20/)
- [https://webaim.org](https://webaim.org/)
- [https://developers.google.com/web/fundamentals/accessibility/](https://developers.google.com/web/fundamentals/accessibility/)
