# CSS (Cascading Style Sheet)

Notas sobre como manejar CSS

## Como usarlo

Ejemplo: dentro de un archivo css se pueden cambiar las propiedades de varias etiquetas html
haciendo uso de un selector y estableciendo sus propiedades
```
selector {
    propiedad: valor;
}
```

## Tipos de selectores

- **Universal (\*):** Selecciona todos los elementos.
```
* {
    color: #808080;
}
```
- **Tipo (h1, button, p, div, etc...)** Selecciona por el tipo de etiqueta
```
p {
    color: #0000ff;
}
```
- **Clase:** Usando la propiedad class en una etiqueta
```
.miClase {
    color: #006400;
}
```
- **Id:** Usando la propiedad id de una etiqueta
```
.miClase {
    color: #8b008b;
}
```
- **Atributo:** Tomando cualquier atributo de etiqueta(s)
```
.miClase {
    color: #ff8c00;
}
```
- **Descendiente:** Seleccionando elemetos dentro de elementos, ya se por etiquetas o clases
```
/* Se seleccionan los elementos p dentro de una etiqueta h2 */
h2 p {
    color: #cd5c5c;
}
```
- **pseudo-clases:** Actuando sobre las etiquetas al seleccionarlas con interaccion de usuario
```
/* Con hover al pasar el mouse sobre h3, cambiará de color */
h3:hover {
    color: #adff2f;
}
```

