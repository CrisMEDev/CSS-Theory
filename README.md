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

**Position:** Permite adquirir nuevas propiedades (top, left, right, bottom) a los elementos, hay varios tipos

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

**display:** modifica el comportamiento de las cajas a diferencia de position que modifica la interaccion entre las cajas

- block: elementos como div, h1 son tipo block
- inline: usadas para textos por lo general

- inline-block: adopta las propiedades de block e inline para poder modificar las dimensiones de la caja

Las siguientes 6 ya no se usan
- table
- inline-table
- list-item
- table-cell-
- table-row
- table-column

- grid
- flex

- inline-grid
- inline-flex

**overflow:** es la barra para hacer scroll en un contenido, por defecto es visible
              esta propiedad ayuda a mantener las imagenes en su contenedor, por ejemplo

- visible: valor por defecto
- auto: para poder hacer scroll dentro de la caja del contenido
- scroll: pone la barra scrolleable aunque no se requiera
- hidden: oculta la barra scroll y limita el contenido a lo que alcance

**float:** se usaba en técnicas antiguas para ajustar elementos en el DOM, ahora es más usado grid y flex
            ahora es útil en los casos en los que se desea crear contenedores de TEXTO e IMÁGENES

- right
- left

**pseudo-elementos:** Son un tipo de elementos pero a diferencia de los reales no forman parte del DOM,
se pueden ver cambio visuales pero no afectan al DOM

- ::first-line | funciona en block, primara linea de un texto
- ::first-letter | funcioan en block, primera letra del texto
- ::placeholder, en los inputs modifica el estilo del placeholder
- ::after | funciona en hijos - content necesario - son elementos inline
- ::before | funciona en hijos - content necesario - son elementos inline
- ::selection para cuando un usuario selecciona algo, este estilo lo modifica el CSS

**pseudo-clases:** escuchan un evento y actuan de acuerdo a lo aplicado en cierto elemento

- :hover escucha el evento cuando el mouse esta encima
- :link cambia las propiedades cuando el enlace ya fue visitado
- :visited: aplica los estilos mientras el enlace no sea visitado
- :active aplica los efectos mientras se clicke o seleccione el elemento
- :focus aplica los estilus cuando un input esta enfocado
- :lang aplica los estilos dependiendo del lenguage pasado como argumento

**object-fit:** aplicado generalmente a las imágenes

- contain valor por defecto, las resoluciones se ajustan al contenido
- fill
- cover ajusta la imagen al contenedor manteniendo las resoluciones
- none agranda la imagen a la resolución que tiene que ser de acuerdo a su caja
- scale-down compara none y contain y se queda con la menor resolución

**object-position:** permite mover la imgen dentro del contenedor

- top
- bottom
- left
- right

**cursor:** modifica el estilo del cursor
[cursor styles](https://www.w3schools.com/cssref/tryit.asp?filename=trycss_cursor)

## Flexbox

*<ins>Propiedades de los containers:</ins>*

Es de las nuevas maneras en las que se maqueta en la actualidad.
Un container con display flex consta de 2 ejes main-axis(eje x) y cross axis(eje y)
Todos los elementos directos (hijos) dentro de un flex se conocen como flex-item

**flex-direction:** propiedad que se aplica al contenedor pero afecta al item

- row valor por defecto, alineamiento horizontal
- row-reverse alineamiento horizontal invertido
- column alineamiento vertical
- column-reverse alineamiento vertical invertido

**flex-wrap:** propiedad que permite cambiar el comportamiento de los flex-item

- wrap mantener las dimensiones del flex-item
- no-wrap comportamiento por defecto
- wrap-reverse el comportamiento inverso a wrap

**flex-flow:** es un shorhand para flex-direction y flex-wrap. Se usa como sigue

- flex-flox: row wrap;

**justify-content:** permite ajustar los flex-items en el contenedor sobre el MAIN AXIS

- center centra el contenido
- space-around deja un margen igual entre cada flex-item
- space-between deja la mayor cantidad de espacio entre las cajas
- space-evenly la separacion entre las cajas y el contenedor es la misma

**align-items** permite ajustar los flex-items en el contenedor sobre el CROSS AXIS cuando hay UNA linea de items
**align-content** permite ajustar los flex-items en el contenedor sobre el CROSS AXIS cuando hay MAS DE UNA linea de items

- center centra los items sobre cross axis
- flex-start mantiene el tamaño del item en base al contenido a diferencia de stretch
- flex-end pasa los items al final
- stretch propiedad por defecto, se estira a lo largo del CROSS-AXIS
- baseline usado en conjunto a WRAP-REVERSE para poner los elementos en la parte baja ya que flex-end no funciona

*<ins>Propiedades de los items</ins>*

**align-self:** funciona sobre el cross axis y tiene las mismas propiedades que align-items

**margin** se va al lado contrario del especificado. Si se combina con so homólogo en auto (Ej: top y bottom en auto)
centra de manera vertical, solo funciona cuando hay un contenedor

- top: se va hacia la parte más baja del container

**flex-grow** recibe un entero y lo usa para calcular el tamaño sobrante de el item o items y asignarlo de manera proporcional al entero.

Si hay 3 cajas y a todas se les aplica un flex-grow de 1 entonces todas las cajas se estiran sobre el main axis de manera igual pero al ir reduciendo la resolucion se quedan en su wodt especificado.

Lo que se hace en general es SUMAR TODOS LOS FLEX-GROW y dividirlos con el espacio sobrante para despues repartirlos de manera proporcional

**flex-shrink:** permite a las algunas cajas ceder más espacio cuando no alcance el lugar disponible para que traten de mantener su resolucion especificada, usar CERO significa que no debe ceder espacio

**flex-basis:** Es como el width pero tiene un nivel de prioridad más alto

**flex:** shorthand para grow, shrink, basis en ese orden

**order:** sirve para posicionar los elementos en base a numeros enteros, entre más alto más al final del cross axis se va

## Grid

Es un estilo de layout y es una propiedad de display. Un grilla es una rejilla o malla cuadrada

**Grid container** es el contenedor con todos los items en la rejilla

- grid-template-rows define la cantidad de filas
- grid-template-columns define la cantidad de columnas

- unidades auto y fr

- gap separa las grillas entre ellas por una determinada unidad, no toma en cuenta los bordes del container

- grid-column determina cuantas columnas usará una grilla
```
    grid-column: 1 / 3; /* Toma de la col-linea 1 a la col-linea 3 */
    grid-column: 1 / span 3; /* Toma de la col-linea 1 y toma 3 columnas por delante */
```

- grid-row determina cuantas filas usará una grilla

**Grid item** todos los elementos dentro del container son grid items

**Grid cell** son cada una de las divisiones que componen el grid container

**Grid tracks (columns y rows)** es la suma de filas y columnas en una grilla

**Grid area** es un espacio delimitado por cierta cantidad de grid cells, la única restricción es que las áreas deben de tener
un espacio reactangular o cuadrado

**Grid line (column lines y row lines)** es la linea que separa columnas y renglones entre cada grilla
En una grilla de 3x5 hay 4 row lines y 6 column lines


**<ins>grid explícito:</ins>** es el grid que se define por el desarrollador

**<ins>grid implícito:</ins>** es el grid que se define cuando la grilla se desborda por no caber en el container
definido por el desarrollador

**grid-auto-columns:** define el size por defecto de la grilla que sea implícita y sea columna

**grid-auto-row:** define el size por defecto de la grilla que sea implícita y sea row

**grid-auto-flow:** define el comportamiento de la grilla implícita

- dense si se usa la propiedad dense, rellena los espacios que sean huecos entre las grillas

` grid-auto-flow: column; /* por defecto se comporta como row */ `

**<ins>grid dinámico:</ins>** 

Son valores que generalmente se ponen en repeat
- minmax(cantidad_min, cantidad_max) define la cantidad minima y maxima de una celda se puede usar min-content y max-content
- min-content se usa para ajustar al tamaño mínimo contenido en una celda
- max-content se usa para ajustar al tamaño máximo contenido en una celda

Cantidad usado como primer argumento en repeat por ejemplo:
- auto-fill: genera la cantidad de columnas o filas que cumplan con las propiedades definidas por el estilo
- auto-fit: auto escala el contenido en la fila o la columna

**<ins>Alineación y control de flujo:</ins>**

Cada celda se comporta como un flex.

Alineación de items en grupo
*justify-items:* Alinea las celdas en su forma horizontal
*align-items:* Alinea las celdas en su forma vertical

- stretch es la propiedad que viene por defecto
- center centra a los elementos
- start los lleva al principio de la fila o columna
- end los lleva al final de la fila o columna

Alineación de columnas, además de poder operar con las  porpiedades de los items se agregan las de flex
*justify-content:* Alinea las filas en su forma horizontal
*align-content:* Alinea las columnas en su forma vertical

- space-around
- space-between
- space-evenly

Aplicado al grid item de manera individual
- align-self recibe los mismos argumentos que la alineacion grupar pero se aplica sobre el item deseado
- justify-self recibe los mismos argumentos que la alineacion grupar pero se aplica sobre el item deseado
- place-self shorthand de las anteriores primero va align y luego justify


## Gradientes

Para aplicar un gradiente lineal se puede aplicar con el ejemplo siguiente:

background: linear-gradient( to direccion, color_inicial, color_final );

` background: linear-gradient( to bottom, transparent, #333 ); `

## pseudo-clases

Para selecciona un elemento específico por orden, hijo de un container, se usa la pseudo clase **nth-child(child_number)** 

## Funciones

```
repeat( cantidad, unidad );
repeat( 3, 150px ); /* repite 3 veces 150px */
repeat( 2, 10px 20px ); /* repite 2 veces 10px 20px --> 10px 20px 10px 20px */
```