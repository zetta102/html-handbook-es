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

Tomemos un ejemplo con la etiqueta `nav`. Puede usarla para definir la navegación de página de la siguiente manera:

```html
<nav>
  <ul>
    <li><a href="/">Home</a></li>
    <li><a href="/blog">Blog</a></li>
  </ul>
</nav>
```

Si estuviera *forzado* a usar una etiqueta `div` en lugar de `nav`, debería entonces usar el rol `navigation`:

```html
<div role="navigation">
  <ul>
    <li><a href="/">Home</a></li>
    <li><a href="/blog">Blog</a></li>
  </ul>
</div>
```

Así que acá tiene un ejemplo práctico: `role` es usado para asignar un valor significativo cuando la etiqueta no entrega el significado deseado

## Use el atributo `tabindex`

Este atributo le permite cambiar el orden en el cual la tecla Tabulador "selecciona" los elementos seleccionables. Por defecto, solo los enlaces y elementos de un formulario solo "seleccionables" de esta manera, por lo que no tiene que usar `tabindex` en ellos.

Agregar `tabindex="0"` a un elemento hace al mismo seleccionable:

```html
<div tabindex="0">
...
</div>
```

Por otra parte, usar `tabindex="-1"` en su lugar elimina este tipo de navegación del elemento, siendo bastante útil en algunos casos.

## Use los atributos `aria`

ARIA es un acrónimo que significa Aplicaciones de Internet Ricas y Accesibles (_Accessible Rich Internet Applications_, en inglés), y define semática aplicada a elementos.

### `aria-label`

Este atributo se usa para agregar una oración que describa a un elemento.

Ejemplo:

```html
<p aria-label="Descripción de un producto">...</p>
```

### `aria-labelledby`

Este atributo configuta una correlación entre el elemento actual y el que lo etiqueta.

Si entiende cómo un elemento `input` se puede asociar a un elemento `label`, puede pensar esto en términos similares.

Pasamos la identificación del objetoq ue describe el elemento actual.

Ejemplo:

```html
<h3 id="descripcion">Descripción del producto</h3>

<p aria-labelledby="descripcion">
...
</p>
```

### `aria-describedby`

Este atributo nos permite asociar un elemento con otro elemento que sirva como descripción.

Ejemplo:

```html
<button aria-describedby="pADescripcion" >Pague Ahora</button>

<div id="pADescripcion">¡Hacer click en el botón lo enviará a nuestro fomulario!</div>
```

### Use aria-hidden para ocultar contenido

Con el atributo `aria-hidden="true"`, le dirá a los lectores de pantalla que ignoren el elemento

## Dónde aprender más

Esta es solo una introducción al tema. Para aprender más, recomiendo estos recursos (en inglés):

- [https://www.w3.org/TR/WCAG20/](https://www.w3.org/TR/WCAG20/)
- [https://webaim.org](https://webaim.org/)
- [https://developers.google.com/web/fundamentals/accessibility/](https://developers.google.com/web/fundamentals/accessibility/)
