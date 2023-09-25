 _Document Object Model_ o **DOM** es una de las innovaciones que más ha influido en el desarrollo de las páginas web dinámicas y de las aplicaciones web más complejas.

DOM permite a los programadores web acceder y manipular las páginas XHTML como si fueran documentos XML. De hecho, DOM se diseñó originalmente para manipular de forma sencilla los documentos XML.

A pesar de sus orígenes, DOM se ha convertido en una utilidad disponible para la mayoría de lenguajes de programación (Java, PHP, JavaScript) y cuyas únicas diferencias se encuentran en la forma de implementarlo.
Los objetos del DOM **modelizan tanto la ventana del navegador como el historial, el documento o página web, y todos los elementos que pueda tener dentro la propia página**, como párrafos, divisiones, tablas, formularios y sus campos, etc.  A través del DOM se puede acceder, por medio de Javascript, a cualquiera de estos elementos, es decir a sus correspondientes objetos para alterar sus propiedades o invocar a sus métodos.

funciones para modificar el DOM

Acceder a elementos
![[Pasted image 20230925115208.png]]
getelementById(id)
El primer método, `.getElementById(id)` busca un elemento HTML con el `id` especificado. En principio, un documento HTML bien construído **no debería** tener más de un elemento con el mismo `id`, por lo tanto, este método devolverá siempre un solo elemento:

```js
const page = document.getElementById("page");   // <div id="page"></div>
```

#### Acceder a elementos padre/Hijo
Existen dos términos que vamos a utilizar de ahora en adelante:

- **Nodos hijos (childNodes)** – elementos que son hijos directos, es decir sus descendientes inmediatos. Por ejemplo, `<head>` y `<body>` son hijos del elemento `<html>`.
- **Descendientes** – todos los elementos anidados de un elemento dado, incluyendo los hijos, sus hijos y así sucesivamente.

Por ejemplo, aquí `<body>` tiene de hijos `<div>` y `<ul>` (y unos pocos nodos de texto en blanco):

![[Pasted image 20230925122125.png]]

Y los descendientes de `<body>` no son solo los hijos `<div>`, `<ul>` sino también elementos anidados más profundamente, como `<li>` (un hijo de `<ul>`) o `<b>` (un hijo de `<li>`) – el subárbol entero.

**La colección `childNodes` enumera todos los nodos hijos, incluidos los nodos de texto.**

#### Añadir a DOM elementos

Crear elementos

![[Pasted image 20230925121426.png]]
Mediante el método `.createElement()` podemos crear un  HTML **en memoria** (_¡no estará insertado aún en nuestro documento HTML!_). Con dicho elemento almacenado en una variable o constante, podremos modificar sus características o contenido, para **posteriormente** insertarlo en una posición determinada del DOM o documento HTML.

Vamos a centrarnos en el proceso de **creación del elemento**, y más adelante veremos diferentes formas de insertarlo en el DOM. El funcionamiento de `.createElement()` es muy sencillo: se trata de pasarle el nombre de la etiqueta `tag` a utilizar:

```js
const div = document.createElement("div");      // Creamos un <div></div>
const span = document.createElement("span");    // Creamos un <span></span>
const img = document.createElement("img");      // Creamos un <img>
```

Aunque menos frecuente, de la misma forma, podríamos crear comentarios HTML con `.createComment()` o fragmentos de texto sin etiqueta HTML con `.createTextNode()`, pasándole a ambos un  con el texto en cuestión. En ambos, se devuelve un  que podremos utilizar luego para insertar en el documento HTML:

```js
const comment = document.createComment("Comentario");   // <!--Comentario-->
const text = document.createTextNode("Hola");           // Nodo de texto: 'hola'
```

El método `createElement()` tiene un parámetro opcional denominado `options`. Si se indica, se espera un objeto con una propiedad `is` para definir un **elemento personalizado** en una modalidad menos utilizada. Se verá más adelante en el apartado de **Web Components**.

#### Añadir y eliminar clases

La propiedad **className** que todo elemento del DOM posee, **cambia el contenido del atributo `class`** de dicho elemento, y está soportada incluso por versiones viejísimas de los navegadores.

Con esta propiedad para cambiar la clase "rojo" por "verde" podemos escribir por ejemplo:

```none
var miElto = document.getElementsByClassName("rojo")[0];
miElto.className = "verde";
```

y el primer elemento localizado pasaría de color rojo a verde.

Sin embargo, **esto presenta un grave problema**: si el elemento tenía más clases aplicadas además de "rojo", las pierde. el motivo es que ahora le estamos asignando como única clase aplicada "verde".

> O sea, asignar un valor a className es como asignárselo directamente al atributo `class` de un elemento HTML.
#### Obtener atributos

Los atributos son propiedades del elemento, no elementos secundarios del elemento. Es importante hacer esta distinción, debido a los métodos utilizados para navegar por los nodos relacionados, principales y secundarios del DOM. Por ejemplo, los métodos **PreviousSibling** y **NextSibling** no se utilizan para navegar de un elemento a un atributo, ni entre atributos. En su lugar, un atributo es una propiedad de un elemento y pertenece a un elemento, tiene una propiedad **OwnerElement** y no una propiedad **parentNode**, y tiene métodos de navegación distintos.

Cuando el nodo actual es un elemento, utilice el método **HasAttribute** para ver si hay algún atributo asociado a dicho elemento. Una vez que se sabe que un elemento tiene atributos, existen múltiples métodos de acceso a atributos. Para recuperar un único atributo de un elemento, utilice los métodos **GetAttribute** y **GetAttributeNode** de **XmlElement**, u obtenga todos los atributos en una colección. La obtención de la colección resulta útil si es necesario recorrerla en iteración. Si desea obtener todos los atributos del elemento, utilice la propiedad **Attributes** del elemento para recuperar todos los atributos en una colección.

Imports System.IO
Imports System.Xml
Public Class Sample
Public Shared Sub Main() Dim doc As XmlDocument = New XmlDocument() doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" & _ "<title>The Handmaid's Tale</title>" & _ "<price>14.95</price>" & _ "</book>")

#### Escribir texto dentro de un elemento

## Sintaxis de jQuery text()

Vamos a repasar la sintaxis extraída de su web [oficial](http://api.jquery.com/text/):

JavaScript

|   |   |
|---|---|
|1<br><br>2<br><br>3<br><br>4|//obtener el texto del nodo seleccionado<br><br>$(selector).text()<br><br>//Asignar texto al nodo seleccionado<br><br>$(selector).text(texto)|

Os comento la sintaxis para obtener el texto:

- **selector (Obligatorio)**: Es el nodo del que queremos obtener el texto. Afecta también a la profundidad del nodo, es decir, que saca también el texto de los nodos hijo.

Y ahora explico la sintaxis para asignar el texto:

- **selector (Obligatorio)**: Es el nodo al que queremos asignar el texto.
- **texto (Obligatorio)**: Texto que queremos insertar en el nodo.

## Ejemplo de jQuery text() para obtener el texto de un nodo

He preparado este primer [ejemplo para ver cómo obtener el texto de un nodo](https://www.anerbarrena.com/demos/2014/031-ejemplo-jquery-text.php "Ejemplos de jQuery text() para obtener el texto de un nodo") con **jQuery**.

![[Pasted image 20230925130743.png]]

- Se detecta el [click](https://www.anerbarrena.com/jquery-click-1931/ "jQuery click(): Controla los clicks en los elementos de tu web") del botón con id ‘boton01’.
- Sacamos un alert por pantalla con el texto del párrafo con id ‘parrafo’.
- Dicho párrafo contiene un nodo hijo ‘span’ del cual también sacamos el texto.
El código HTML del párrafo y botones es el siguiente:

![[Pasted image 20230925130832.png]]

#### Modificar atributos



funciones para modificar en jquery

acceder a elementos
![[Pasted image 20230925115418.png]]

#### [querySelector()](https://lenguajejs.com/javascript/dom/seleccionar-elementos-dom/#queryselector)

El método `.querySelector()` devuelve el primer elemento que encuentra que encaja con el selector CSS suministrado por parámetro. Siempre devuelve un solo elemento y en caso de no coincidir con ninguno, devuelve :

![[Pasted image 20230925115752.png]]


Lo interesante de este método, es que al permitir suministrarle un [selector CSS básico](https://lenguajecss.com/css/selectores/selectores-basicos/) o incluso un [selector CSS avanzado](https://lenguajecss.com/css/selectores/selectores-avanzados/), se vuelve un sistema mucho más potente.

- El primer ejemplo sería equivalente a utilizar un `.getElementById()`, sólo que en la versión de `.querySelector()` indicamos por un parámetro , y en el primero le pasamos un simple . Observa que estamos indicando un `#` porque se trata de un `id`.
    
- En el segundo ejemplo, estamos recuperando el primer elemento con clase `info` que esté dentro de otro con clase `main`. En los métodos tradicionales, sería menos directo ya que tendríamos que realizar varias llamadas. Con `.querySelector()` se hace directamente sólo con una

Acceder a elementos padre/hijo

el `.parents()`método nos permite buscar entre los antepasados ​​de estos elementos en el árbol DOM y construir un nuevo objeto jQuery a partir de los elementos coincidentes ordenados desde el padre inmediato hacia arriba; los elementos se devuelven en orden desde el padre más cercano a los externos. Cuando hay varios elementos DOM en el conjunto original, el conjunto resultante también estará en orden _inverso_ al de los elementos originales, y se eliminarán los duplicados.

Los métodos `.parents()`y `[.parent()](https://api.jquery.com/parent/)`son similares, excepto que este último solo sube un nivel en el árbol DOM. Además, `$( "html" ).parent()`el método devuelve un conjunto que contiene, `document`mientras que `$( "html" ).parents()`devuelve un conjunto vacío.

Crear elementos

1. `append()`: este método agregará el elemento al final de los elementos seleccionados.
2. `prepend()`: este método agregará el elemento al principio de los elementos seleccionados.
3. `after()`: este método agregará el elemento después de los elementos seleccionados.
4. `before()` - Este método agregará el elemento antes de los elementos seleccionados.

#### Añadir y eliminar clases


## Sintaxis de jQuery addClass()

Os detallo la sintaxis de esta función de [jQuery](https://www.anerbarrena.com/programacion/jquery/ "Programación jQuery") para añadir clases.

JavaScript

|   |   |
|---|---|
|1|$(elemento).addClass(nombreClase,funcion(index,oldclass))|

Os explico los parámetros disponibles:

- **elemento (obligatorio)**: Objeto al cual queremos añadir una o varias clases.
- **nombreClase (obligatorio)**: Nombre de la clase existente que queremos asignar.
- **funcion (opcional)**: Al usar la [Función callback](https://www.anerbarrena.com/jquery-callback-5110/) por defecto nos devuelve estos valores: **index** con el número de posición del elemento en el DOM, y **oldclass** con la clase actual del elemeto.

## Sintaxis de jQuery removeClass()

La sintaxis para eliminar clases de los elementos es la siguiente:
  

JavaScript

|   |   |
|---|---|
|1|$(elemento).removeClass(nombreClase,funcion(index,claseactual))|

Y repaso los parámetros:

- **elemento (obligatorio)**: Objeto del cual queremos eliminar una o varias clases.
- **nombreClase (obligatorio)**: Nombre de la clase existente que queremos asignar.
- **funcion (opcional)**: Al usar la función por defecto nos devuelve estos valores de las clases a eliminar: **index** con el número de posición del elemento en el DOM, y **claseactual** con la clase actual del elemeto.

#### Obtener atributos

## Sintaxis de jQuery attr()

Cuando **attr()** se usa para **obtener el valor de un atributo** devuelve el valor del primer elemento encontrado. Veamos su sintaxis extraída de su [web oficial](http://api.jquery.com/attr/):

JavaScript

|   |   |
|---|---|
|1|$(selector).attr(atributo)|

De esta manera obtendríamos el valor del atributo seleccionado, os explico los parámetros:

- **selector (Obligatorio)**: Elemento que queremos examinar a nivel de atributos.
- **atributo (Obligatorio)**: Atributo del cual queremos obtener su valor.

En cambio, cuando se usa para **modificar/asignar valores en los atributos** se aplica a todos los elementos especificados. Las sintaxis posibles en este caso serían las siguiente:
  

JavaScript

|   |   |
|---|---|
|1<br>2<br><br>3<br>4<br><br>5<br><br>6<br>7<br><br>8|/* Sintaxis por defecto */<br><br>$(selector).attr(atributo, valor)<br><br>/* Modificar valor usando una funcion */<br><br>$(selector).attr(atributo,function(index,valor))<br><br>/* Modificar multiples valores en otros tantos atributos */<br><br>$(selector).attr({atributo1:valor1, atributo2:valor2,...})|

parámetros:

- **selector (Obligatorio)**: Elemento que queremos examinar a nivel de atributos.
- **atributo (Obligatorio)**: Atributo del cual queremos obtener su valor.
- **valor (Obligatorio)**: Valor que queremos aplicar al atributo.
- **index (Obligatorio)**: Posición del elemento en el DOM en caso de haber varios.

