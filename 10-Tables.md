# Tablas

En los primeros días de la web, las tablas eran parte importante en la construcción de interfaces.

Luego, fueron reemplazadas por CSS y su capacidad de creación de interfaces, y hoy tenemos poderosas herramientas como Grid y Flexbox de CSS para construir interfaces. Las tablas son hoy en día usadas para, como se puede imaginar, ¡crear tablas!

### La etiqueta `table`

Puede definir una tabla usando la etiqueta `table`:

```html
<table>

</table>
```

Dentro de la tabla definiremos los datos. Tenemos que pensar en términos de filas, lo que significa que lo que se agrega a una table son filas, no columnas. Las columnas se definirán dentro de una fila.

### Filas

Una fila se agrega usando la etiqueta `tr`, y es lo único que podemos agregar a una etiqueta `table`:

```html
<table>
  <tr></tr>
  <tr></tr>
  <tr></tr>
</table>
```

Esta es una tabla con tres filas.

La primera fila _puede_ tomar el rol de encabezado.

### Encabezados de columna

El encabezado de una tabla contiene el nombre de una columna, típicamente en negritas.

Piense en un documento de Excel / Google Sheets. Es similar al encabezado `A-B-C-D...` superior.

![](9-Tables/Screen%20Shot%202019-06-20%20at%2010.18.17.png)

Se define el encabezado usando la etiqueta `th`:

```html
<table>
  <tr>
    <th>Columna 1</th>
    <th>Columna 2</th>
    <th>Columna 3</th>
  </tr>
  <tr></tr>
  <tr></tr>
</table>
```

### Contenido de una tabla

El contenido de una tabla se define usando etiquetas `td` dentro los otros elementos `tr`:

```html
<table>
  <tr>
    <th>Columna 1</th>
    <th>Columna 2</th>
    <th>Columna 3</th>
  </tr>
  <tr>
    <td>Fila 1 Columna 1</td>
    <td>Fila 1 Columna 2</td>
    <td>Fila 1 Columna 3</td>
  </tr>
  <tr>
    <td>Fila 2 Columna 1</td>
    <td>Fila 2 Columna 2</td>
    <td>Fila 2 Columna 3</td>
  </tr>
</table>
```

Los navegadores lo renderizan de la siguiente manera, si no le agrega estilos con CSS:

![](9-Tables/Screen%20Shot%202019-06-20%20at%2010.24.08.png)

Agregarl el siguiente CSS:

```css
th, td {
  padding: 10px;
  border: 1px solid #333;
}
```

Hace que la tabla se vea más como una tabla:

![](9-Tables/Screen%20Shot%202019-06-20%20at%2010.26.15.png)

### Tamaño de filas y columnas

Una fila puede expandirse a dos o más columnas, usando el atributo `colspan`:

```html
<table>
  <tr>
    <th>Columna 1</th>
    <th>Columna 2</th>
    <th>Columna 3</th>
  </tr>
  <tr>
    <td colspan="2">Fila 1 Columnas 1-2</td>
    <td>Fila 1 Columna 3</td>
  </tr>
  <tr>
    <td colspan="3">Fila 2 Columnas 1-3</td>
  </tr>
</table>
```

![](9-Tables/Screen%20Shot%202019-06-20%20at%2010.27.59.png)

O puede expandirse a dos o más filas, usando el atributo `rowspan`:

```html
<table>
  <tr>
    <th>Columna 1</th>
    <th>Columna 2</th>
    <th>Columna 3</th>
  </tr>
  <tr>
    <td colspan="2" rowspan="2">Filas 1-2 Columnas 1-2</td>
    <td>Fila 1 Columna 3</td>
  </tr>
  <tr>
    <td>Fila 2 Columna 3</td>
  </tr>
</table>
```

![](9-Tables/Screen%20Shot%202019-06-20%20at%2010.29.37.png)

### Encabezados de fila

Antes, le expliqué cómo tener encabezados de columnas, usando la etiqueta `th` dentro de la primera etiqueta `tr` de la tabla.

You can add a `th` tag as the first element inside a `tr` that's not the first `tr` of the table, to have row headings:

```html
<table>
  <tr>
    <th></th>
    <th>Column 2</th>
    <th>Column 3</th>
  </tr>
  <tr>
    <th>Row 1</th>
    <td>Col 2</td>
    <td>Col 3</td>
  </tr>
  <tr>
    <th>Row 1</th>
    <td>Col 2</td>
    <td>Col 3</td>
  </tr>
</table>
```

![](9-Tables/Screen%20Shot%202019-06-20%20at%2010.49.16.png)

### More tags to organize the table

You can add 3 more tags into a table, to have it more organized.

This is best when using big tables. And to properly define a header and a footer, too.

Those tags are

- `thead`
- `tbody`
- `tfoot`

They wrap the `tr` tags to clearly define the different sections of the table. Here's an example:

```html
<table>
  <thead>
    <tr>
      <th></th>
      <th>Column 2</th>
      <th>Column 3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Row 1</th>
      <td>Col 2</td>
      <td>Col 3</td>
    </tr>
    <tr>
      <th>Row 2</th>
      <td>Col 2</td>
      <td>Col 3</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <td></td>
      <td>Footer of Col 1</td>
      <td>Footer of Col 2</td>
    </tr>
  </tfoot>
</table>
```

![](9-Tables/Screen%20Shot%202019-06-20%20at%2010.52.41.png)

## Table caption

A table should have a `caption` tag that describes its content. That tag should be put immediately after the opening `table` tag:

```html
<table>
  <caption>Dogs age</caption>
  <tr>
    <th>Dog</th>
    <th>Age</th>
  </tr>
  <tr>
    <td>Roger</td>
    <td>7</td>
  </tr>
</table>
```
