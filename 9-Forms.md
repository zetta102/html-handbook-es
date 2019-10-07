# Formularios

Los formularios son una forma de interacturar on una página o una aplicación construida con tecnologías web.

Tiene un conjunto de controles, y cuando envía el formulario, ya sea con un boton dedicado o por medio de código, el navegador enviará la información al servidor.

Por defecto, este envío de información hace que la página se recargue después de enviar los datos, pero este comportamiento puede ser alterado con JS. Sin embargo, este libro está dedicado únicamente a HTML.

Un formulario se crea usando la etiqueta `form`:

```html
<form>
	...
</form>
```

Por defecto, los formularios son enviados usando el método HTTP GET, el cual tiene algunas contraindicaciones, por lo que usualmente preferirá usar POST.

Puede ajustar el método a POST al enviar usando el atributo `method`:

```html
<form method="POST">
	...
</form>
```

El formulario se enviará, ya sea usando GET o POST, a la misma dirección en la que está alojada.

Así, si el formulario está en `https://flaviocopes.com/contacts`, al presionar el botón de envío, hará una petición a la misma dirección.

Lo que puede que resulte en que no ocurra nada

Se necesita algo del lado del servidor para manejar la petición, y normalmente se "escuchan" estos eventos por medio de una dirección dedicada.

Puedes especificar la dirección por medio el parámetro `action`:

```html
<form action="/new-contact" method="POST">
	...
</form>
```

Esto causará que el navegador envíe los datos de formulario con método POST a la dirección `/new-contact` del mismo origen.

Si el origen (esto es, protocolo + dominio + puerto) es `https://flaviocopes.com` (siendo el puerto 80 el usado por defecto), esto significa que los datos del formulario serán enviados a `https://flaviocopes.com/new-contact `.

Hablé de datos, ¿pero cuáles datos?

Los datos son provistos por los usuarios por medio de un conjunto de controles que están disponibles en la plataforma web:

- Cajas de texto (de línea única)
- Áreas de texto (de líneas múltiples)
- Cajas de selección (de selección única de una lista)
- Botones radio (o _radio buttons_, de selección única de una lista siempre visible)
- Cajas de tildado (o _checkboxes_, de selección múltiple, o ninguna)
- Subida de archivos
- ¡Y mucho más!

Procederé a presentar cada uno de ellos a continuación.

## La etiqueta `input`
Este campo es uno de los elementos de formulario más usados. También es un elemento muy versátil, que puede cambiar completamente su comportamiento basado en su atributo `type`.

El comportamiento por defecto es de un control de línea única:

```html
<input>
```

Y eso es equivalente a:

```html
<input type="text">
```

Como con todos los otros campos a continuación, se debe dar un nombre al campo para que su contenido sea correctamente identificado al ser enviado el formulario al servidor:

```html
<input type="text" name="username">
```

El atributo `placeholder` se usa para mostrar texto dentro del elemento, en color gris claro, cuando esté vacío. Es útil para dar una pista al usuario de qué información introducir:

```html
<input type="text" name="username" placeholder="Su nombre de usuario">
```

### Email

Usar `type="email"` validará la información introducida del lado del cliente (en otras palabras, en el navegador), para asegurarse que esté semáticamente correcto (lo que significa que no verificará si existe el correo), antes de enviar el formulario.

```html
<input type="email" name="email" placeholder="Su correo">
```

### Contraseña

Usar `type="password"` hará que cualquier información introducida se muestre como un asterisco (*), o un punto, útil para campos que estén destinados a contraseñas.

```html
<input type="password" name="password" placeholder="Su contraseña">
```

### Números

Puede tener un campo que únicamente reciba números:

```html
<input type="number" name="edad" placeholder="Su edad">
```

Puede especificar un valor máximo y mínimo por medio de los atributos `max` y `min`, respectivamente:

```html
<input type="number" name="edad" placeholder="Su edad" min="18" max="110">
```

El atributo `step` permite establecer los 'pasos' entre distintos valores. Por ejemplo, este campo acepta un valor entre 10 y 50, en incrementos de 5 unidades:

```html
<input type="number" name="un-numero"  min="10" max="50" step="5">
```

### Campo oculto

Los campos pueden estar ocultos del usuario, pero aún así su información será enviada al servidor:

```html
<input type="hidden" name="campo-oculto" value="algun-valor">
```

Esto es usado para almacenar valores como un token CSRF, conocido por ser útil para seguridad e identificación de usuario, e inclusive la detección de bots de envío de spam, usando técnicas especiales.

También se puede usar para identificar un formulario y su acción.

### Configurando un valor por defecto

Todos estos tipos aceptan un valor por defecto. Si el usuario no lo cambia, ese será el valor enviado al servidor:

```html
<input type="number" name="edad" value="18">
```

Si usa un `placeholder`, ese valor aparecerá si el usuario borra el valor dentro del campo:

```html
<input type="number" name="edad" placeholder="Su edad" value="18">
```

## Envío de formulario

El campo `type="submit"` es un botón que, una vez presionado, envía el formulario:

```html
<input type="submit">
```

El atributo `value` ajusta el texto del botón, el cual se ajusta por defecto a "Submit":

```html
<input type="submit" value="Haz click">
```

## Validación de Formulario

Los navegadores proveen funcionalidades de validación del lado del cliente a los formularios.

Puedes ajustar los campos como sea requerido, asegurándose de que fueron rellenados, así como imponer un formato establecido para los datos de cada campo.

Veamos ambas opciones.

### Establecer campos requeridos

El atributo `required` ayuda a validar los campos. Si el campo no está lleno, la validación del lado del cliente falla y el navegador no envía el formulario:

```html
<input type="text" name="nombre de usuario" required>
```

### Establecer un formato específico

Describí el `type="email"` hace unos párrafos atrás. Automáticamente valida la dirección de correo electrónico de acuerdo con un formato establecido en su especificación.

En el campo `type="number"`, mencioné el atributo `min` y `max` para limitar los valores a cierto intervalo.

Pero puede hacer más.

Puede imponer un formato específico en cualquier campo.

El atributo `pattern` le otorga la habilidad de establecer una expresión regular, conocida como _regular expression_ en inglés, contra la cual comparar la información introducida.

Recomiendo leer mi guía de expresiones regulares en el siguiente [enlace](https://flaviocopes.com/javascript-regular-expressions/), en inglés.

```html
<input type="text" name="username" pattern="[a-zA-Z]{8}">
```

## Otros campos

### Subidas de archivos

Puede subir archios locales desde su computador y enviarlos al servidor usando un elemento con atributo `type="file"`:

```html
<input type="file" name="documentos-secretos">
```

Puede también adjuntar múltiples archivos:

```html
<input type="file" name="documentos-secretos" multiple>
```

Puede especificar uno o más tipos de archivo permitido con el atributo `accept`. Este ejemplo en particular acepta imágenes:

```html
<input type="file" name="documentos-secretos" accept="image/*">
```

Puede usar un tipo MIME específico, como `application/json`, o también establecer una o múltiples extensiones de archivo, como podría ser `.pdf`:

```html
<input type="file" name="secret-documents" accept=".jpg, .jpeg, .png">
```

### Botones

Los campos `type="button"` pueden ser usados para agregar botones adicionales a el formulario, que no sean botones de envíos:

```html
<input type="button" value="Hazme click">
```

Son usados para hacer algo por medio de un método de código, usando JS.

Hay un campo especial mostrado como un botón, cuya acción es la de limpiar el formulario entero y reestablecer el estado de los campos:

```html
<input type="reset">
```

### Botones radio

Son usados para crear un conjunto de elecciones dónde, si uno es presionado, los demás son deshabilitados.

El nombre viene de las antiguas radios de automóvil que tenían este tipo de interfaz.

Se define por medio de un conjunto de `type="radio"`, todos con el mismo atributo `name`, y diferentes atributos `value`:

```html
<input type="radio" name="color" value="amarillo">
<input type="radio" name="color" value="rojo">
<input type="radio" name="color" value="azul">
```

Una vez el formulario sea enviado, la propiedad de datos `color` tendrá un único valor.

Siempre hay al menos un elemento seleccionado. El primer objeto es el seleccionado por defecto.

Se puede establecer el valor preseleccionado por medio del atributo `checked`. Solo puede ser usado una vez por cada grupo de botones radio.

### Cajas de tildado

Similares a los botones radio, pero permiten múltiples valores, o ninguno de ellos.

Se definen por medio de un conjunto de `type="checkbox"`, todos con el mismo atributo `name`, y diferentes atributos `value`:

```html
<input type="checkbox" name="color" value="amarillo">
<input type="checkbox" name="color" value="rojo">
<input type="checkbox" name="color" value="azul">
```

Ninguna de estas cajas estarán tildadas por defecto. Puede usar el atributo `checked` para tildarlas al cargar la página.

Ya que este campo permite múltiples valores, al enviar el formulario, estos serán enviados al servidor como un `array`.

### Fecha y hora

Tenemos algunos campos que aceptan valores de fecha.

El campo `type="date"` permite al usuario introducir una fecha, y muestra un seleccionador si es necesario:

```html
<input type="date" name="cumpleaños">
```

El campo `type="time"` permite al usuario introducir una hora, y muestra un seleccionador si es necesario:

```html
<input type="time" name="hora-de-busqueda">
```

El campo `type="month"` permite al usuario introducir un mes y un año:

```html
<input type="month" name="mes-lanzamiento">
```

El campo `type="week"` permite al usuario introducir una semana y un año:

```html
<input type="week" name="elegir-semana">
```

Todos estos campos permiten limitar el rango y los incrementos entre cada valor. Recomiendo revisar la Red de Desarrolladores de Mozilla (abreviado MDN) para los pormenores de su uso.

El campo `type="datetime-local"` te permite elegir una fecha y una hora.

```html
<input type="datetime-local" name="fechar-y-hora">
```

Acá una [página](https://codepen.io/flaviocopes/pen/ZdWQPm) en la cual probarlos todos.

### Selección de color

Puedes permitir que el usuario seleccione un color por medio del elemento `type="color"`:

```html
<input type="color" name="color-auto">
```

Puede ajustar un valor por defecto usando el atributo `value`:

```html
<input type="color" name="color-auto" value="#000000">
```

El navegador se encargará de mostrar un seleccionador al usuario.

### Rango

Este elemento muestra una barra deslizante, la cual puede ser movida desde un valor de inicio hasta un valor final:

```html
<input type="range" name="edad" min="0" max="100" value="30">
```

Opcionalmente, se puede incluir el valor de los incrementos entre valores:

```html
<input type="range" name="age" min="0" max="100" value="30" step="10">
```

### Teléfono

El campo `type="tel"` se usa para introducir un número de teléfono:

```html
<input type="tel" name="numero-telefono">
```

La ventaja de usar `tel` sobre `text` es que, en móviles, el dispositivo mostrará un teclado númerico.

Puede especificar un atributo `pattern` para validación adicional:

```html
<input type="tel" pattern="[0-9]{3}-[0-9]{8}" name="numero-teléfono">
```

### Dirección

El campo `type="url"` se usa para introducir una dirección.
```html
<input type="url" name="sitio-web">
```

Se puede validar usando el atributo `pattern`:

```html
<input type="url" name="website"  pattern="https://.*">
```

## La etiqueta `textarea`

El elemento `textarea` permite a los usuarios introducir texto multilinea. Comparado con `input`, requiere una etiqueta de clausura:

```html
<textarea></textarea>
```

Puede ajustar sus dimensiones usando CSS, así como también usando los atributos `rows` y `cols`:

```html
<textarea rows="20" cols="10"></textarea>
```

Como otras etiquetas de formulario, el atributo `name` determinar el nombre de los datos enviados al servidor:

```html
<textarea name="articulo"></textarea>
```

## La etiqueta `select`

Esta etiqueta se usa para crear un menú desplegado.

Allí, el usuario puede elegir una de las opciones disponibles.

Cada opción se crea usando la etiqueta `option`. Se agrega un nombre a la selección, y un valor a cada opción:

```html
<select name="color">
	<option value="rojo">Rojo</option>
	<option value="amarillo">Amarillo</option>
</select>
```

También puede deshabiltar alguna de las opciones:

```html
<select name="color">
	<option value="rojo" disabled>Rojo</option>
	<option value="amarillo">Amarillo</option>
</select>
```

También puede tener una opción vacía:

```html
<select name="color">
	<option value="">None</option>
	<option value="rojo">Rojo</option>
	<option value="amarillo">Amarillo</option>
</select>
```

Las opciones pueden ser agrupadas usando la etiqueta `optgroup`. Cada grupo de opciones tiene un atributo `label`:

```html
<select name="color">
	<optgroup label="Primarios">
		<option value="rojo">Rojo</option>
		<option value="amarillo">Amarillo</option>
		<option value="azul">Azul</option>
	</optgroup>
	<optgroup label="Otros">
		<option value="verde">Verde</option>
		<option value="rosa">Rosa</option>
	</optgroup>
</select>
```
