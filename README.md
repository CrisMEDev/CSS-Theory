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

## Especificidad

El orden de prioridad que se le da al aplicado de estilos tiene importancia según como se seleccionen
los elemetos, el ejemplo de abajo muestra el orden de prioridad de manera descendente.

El ( !important ) es una palabra reservada en CSS y tiene más prioridad en todos los estilos
El estilo de linea es cuanto se usa el atributo style en la etiqueta

- !important
- estilos en línea
- identificadores
- clases, pseudo clases, atributos
- elementos, pseudo elementos


## Metodología BEM

Para trabajar con la metodología BEM basta con usar el nombre del contenedor
para nombrar la clase del elemento seguido de dos guines bajos más el nombre del elemento

Para diferenciar un elemento del resto, se puede usar al final de la clase un doble guión
seguido de una palabra significativa para la clase. En el ejemplo de abajo se resalta el segundo input

Ej:

```
<div class="contact-form">

    <input type="text" class="contact-form__input">
    <input type="text" class="contact-form__input--active">
    <input type="text" class="contact-form__input">
    <input type="text" class="contact-form__input">
    <input type="password" class="contact-form__input">
        
</div>
```

En el caso de múltiples elementos anidados se usa la nomenclatura anterior y se concatenan los
elementos descendentes con un '-' hasta llegar al deseado.

Ej:

```
<div class="suscriber-form">
    <p class="suscriber-form__p">
        <h4 class="suscriber-form__p-h4">
            Hola mundo
        </h4>
    </p>
</div>
```

## Unidades de medida

Existen dos tipos, fijas y relativas.

Fijas:
- px -> pixeles
- cm -> centímetros
- mm -> milímetros
- pt -> puntos

Relativas:
- rem   (Trabaja en base al root)
- em    1em === 16px generalmente pero el navegador lo puede interpretar a su antojo
        de manera general, 1em === al valor que se le da a la caja contenedora
- vw    (viewport width)    Ocupa el ancho de la pantalla
- vh    (viewport height)   Ocupa el alto de la pantalla

## Normalize

Los siguientes son agregados al archivo de normalize

Para que los contenedores no se redimensionen, usar lo siguiente

```
 * {
   box-sizing: border-box;
 }
```

Para que el ajuste de las imágenes en los navegadores sea de acuerdo a la pantalla
```
img {
    border-style: none;
    max-width: 100%;
  }
```

## Cajas

Hay dos tipos

- En línea: Se ajustan a su contenido como en es caso de la etiqueta b
- En bloque: Se ajustan al ancho del contenedor como el caso de la etiqueta h1

Con CSS se puede pasar de un elemento en línea a uno en bloque y viceversa

Box Model: Está compuesto por 4 propiedades

- content: modificado por line-height
- padding: modificado por padding y su variantes individuales
- border: modificado por border
- margin: modificado por margin y su variantes individuales

**Outline:** Permite resaltar elementos del DOM pero a diferencia de border no ocupa espacios

Position: Permite adquirir nuevas propiedades (top, left, right, bottom) a los elementos, hay varios tipos

top y left tienen mayor priodidad que sus opuestos bottom y right

- static: valor por defecto que adquieren los elementos
- relative: Permite a los elementos ajustaralos a partir de la posicion en donde estan sin afectar a los demas
- absolute: Permite a los elementos ajustaralos a partir de la posicion absoluta desde el contenerdor donde
            se encuentre el elemento, si se usan las propiedades como top y right, se usará el viewport del navegador
            el tamaño de la caja se ajusta al contenido
- fixed: Es como absolute pero la diferencia es que el elemento queda fijado tras usar el scroll
- sticky: Es como fixed solo que el espacio en el DOM lo conserva (define a partir de que lugar en el DOM un elemento se comportará
          como fixed)

**Z index:** ordena a los elementos en el eje Z, es recomendable usar valores altos como 10 en 10 o
100 en 100 para el caso en el que se necesiten poner elementos entre ellos


