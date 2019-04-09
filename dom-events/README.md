# DOM y Eventos

## Dom
El modelo de objeto de documento (DOM) es una interfaz de programación para los documentos HTML y XML. Facilita una representación estructurada del documento y define de qué manera los programas pueden acceder, al fin de modificar, tanto su estructura, estilo y contenido. El DOM da una representación del documento como un grupo de nodos y objetos estructurados que tienen propiedades y métodos. Esencialmente, conecta las páginas web a scripts o lenguajes de programación.

El DOM fue diseñado para ser independiente de cualquier lenguaje de programación particular, hace que la presentación estructural del documento sea disponible desde un simple y consistente API. Aunque en este manual nos centramos exclusivamente en JavaScript, la directrices del DOM pueden construirse para cualquier lenguaje, así lo demuestra el siguiente ejemplo de Python:

```python
import xml.dom.minidom as m
doc = m.parse("C:\\Projects\\Py\\chap1.xml");
doc.nodeName # Propiedad DOM del objeto document;
p_list = doc.getElementsByTagName("para");
```

### Accediendo al DOM

El DOM es una interfaz, eso quiere decir que tenemos atributos y objetos a nuestra disposicion para poder manipular el DOM. Podemos recorrer y desplazarnos por el dom a travez de estos metodos.

* __getElementById__
Podemos acceder a cualquier elemento del dom a travez de su identificador de id.

```javascript
  let header = document.getElementById('id');
```

* __getElementsByTagName__
Podemos acceder a todas las etiquetas del dom a travez de su identificador de tag. getElementByTagName nos devolvera una coleccion tipo HTMLCollection, este tipo de array no se puede iterar. Si quisieramos iterarlo, tendriamos que convertirlo en array.

```javascript
  let header = document.getElementsByTagName('p');
```

* [querySelector](https://developer.mozilla.org/es/docs/Web/API/Document/querySelector)
Devuelve el primer elemento del documento

```javascript
  let p = document.querySelector('.parent p');
```

* [querySelectorAll](https://developer.mozilla.org/es/docs/Web/API/Document/querySelectorAll)
El método querySelectorAll() de un Element devuelve una NodeList estática (no viva) que representa una lista de elementos del documento que coinciden con el grupo de selectores indicados.

```javascript
  let ps = document.querySelectorAll('p');
```

* [parentNode](https://developer.mozilla.org/es/docs/Web/API/Node/parentNode)
La propiedad de sólo lectura node.parentNode devuelve el padre del nodo especificado en el árbol.

```javascript
  document.body.parentNode
```

* [childNodes](https://developer.mozilla.org/es/docs/Web/API/Node/childNodes)
La propiedad de solo lectura Node.childNodes  devuelve una colección de hijos nodes del elemento dado donde el primer nodo hijo es asignado un índice 0.

```javascript
  document.childNodes
```

* [firstChild](https://developer.mozilla.org/en-US/docs/Web/API/Node/firstChild)
La propiedad de solo lectura Node.childNodes  devuelve el primer hijo del arbol o null si este no es encontrado.

```javascript
  document.firstChild
```

* [lastChild](https://developer.mozilla.org/es/docs/Web/API/Node/lastChild)
La propiedad de sólo lectura Node.lastChild devuelve el último hijo del nodo. Si su padre es un elemento, entonces el hijo es generalmente un nodo de element, nodo de texto o un nodo de comentario. Devuelve null si no hay elementos hijos.

```javascript
  document.lastChild
```

* [nextSibling](https://developer.mozilla.org/es/docs/Web/API/Node/nextSibling)
La propiedad de sólo lectura Node.nextSibling devuelve el siguiente nodo

```javascript
  document.body.nextSibling
```

* [previousSibling](https://developer.mozilla.org/es/docs/Web/API/Node/previousSibling)
La propiedad de sólo-lectura Node.previousSibling devuelve el nodo inmediatamente anterior al especificado en la lista de nodos

```javascript
  document.body.previousSibling
```

* [closest](https://developer.mozilla.org/es/docs/Web/API/Element/closest)
El método closest() de la interfaz Element devuelve el ascendiente más cercano al elemento actual (o el propio elemento actual) que coincida con el selector proporcionado por parámetro. 

```javascript
  document.body.closest(selectors)
```

### Manipulando el DOM

* [createElement](https://developer.mozilla.org/es/docs/Web/API/Document/createElement)
En un documento HTML, el método Document.createElement() crea un elemento HTML especificado por su tagName

```javascript
  let newDiv = document.createElement("div");
  let text = document.createTextNode("Hola!¿Qué tal?");
  newDiv.appendChild(text);

  document.body.appendChild(newDiv);
```

* [appendChild](https://developer.mozilla.org/es/docs/Web/API/Node/appendChild)
Agrega un nuevo nodo al final de la lista de un elemento hijo de un elemento padre especificado.

```javascript
  let newDiv = document.createElement("div");
  let text = document.createTextNode("Hola!¿Qué tal?");
  newDiv.appendChild(text);

  document.body.appendChild(newDiv);
```

* [removeChild](https://developer.mozilla.org/es/docs/Web/API/Node/removeChild)
El método Node.removeChild() elimina un nodo hijo del DOM y puede devolver el nodo eliminado.

```javascript
  let div = document.createElement('div');
  div.textContent = 'DIV!!';
  div.style.transition = "all 1s ease";
  document.body.appendChild(div);

  setTimeout(() => {
    div.style.opacity = '0';
    setTimeout(() => {
        document.body.removeChild(div);
    }, 1000)
  }, 3000)
```

* [replaceChild](https://developer.mozilla.org/es/docs/Web/API/Node/replaceChild)
El método Node.replaceChild() reemplaza un nodo hijo del elemento especificado por otro.

```javascript
  <div>
    <strong>hello</strong>
  </div>

  let em = document.createElement('em');
  let strong = document.querySelector('strong');
  let div = document.querySelector('div');
  em.textContent = 'hi';
  div.replaceChild(em, strong);
```

* [cloneNode](https://developer.mozilla.org/es/docs/Web/API/Node/cloneNode)
El método Node.cloneNode() devuelve un duplicado del nodo en el que este método fue llamado.

```javascript
  let p = document.getElementById("para1");
  let p_prime = p.cloneNode(true);
```

* [insertBefore](https://developer.mozilla.org/es/docs/Web/API/Node/insertarAntes)
El método Node.insertBefore() inserta un nodo antes del nodo de referencia como hijo de un nodo padre indicado.

```javascript
  <div>
    <strong>hello</strong>
  </div>
  let em = document.createElement('em');
  let strong = document.querySelector('strong');
  let div = document.querySelector('div');
  em.textContent = 'hi';
  div.insertBefore(em, strong);
```

* [setAttribute](https://developer.mozilla.org/es/docs/Web/API/Element/setAttribute)
Establece el valor de un atributo en el elemento indicado. Si el atributo ya existe, el valor es actualizado, en caso contrario, el nuevo atributo es añadido con el nombre y valor indicado.

```javascript
  Element.setAttribute(name, value);

  <button>Hola Mundo</button>

  let b = document.querySelector("button"); 

  b.setAttribute("name", "helloButton");
  b.setAttribute("disabled", "");
```

* [getAttribute](https://developer.mozilla.org/es/docs/Web/API/Element/getAttribute)
getAttribute() devuelve el valor del atributo especificado en el elemento.

```html
  <div contenteditable=true>hello</div>
```

```javascript
  let div = document.querySelector('div');
  console.log(div.getAttribute('contenteditable'))
```

* [removeAttribute](https://developer.mozilla.org/es/docs/Web/API/Element/removeAttribute)
getAttribute() devuelve el valor del atributo especificado en el elemento.

```javascript
  // <div id="div1" align="left" width="200px"> 
  document.getElementById("div1").removeAttribute("align"); 
  // ahora: <div id="div1" width="200px">
```

* [style](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/style)
Ya que el dom es un objeto podemos acceder a los nodos y manipular sus atributos a travez de la notacion de punto. Para agregar un atributo compuesto de style , lo tendremos que escribir
en camelcase. Tambien podemos usar el atributo __cssText__ del objeto style o tambien podemos agregar utilizando el metodo __setAttribute__

```javascript
  let element = document.querySelector('p');
  element.style.backgroundColor = 'red';

  document.querySelector('p').style.cssText = "color: blue; border: 1px solid black";

  elt.setAttribute("style", "color:red; border: 1px solid blue;");
```

* [getComputedStyle](https://developer.mozilla.org/es/docs/Web/API/Window/getComputedStyle)
Devuelve el estilo computado del elemento. Los estilos computados representan los valores finales

```html
  <div style="background: black"></div>
```

```javascript
  let style = getComputedStyle(document.querySelector('div'));
  console.log(style.background);
```

* [classList](https://developer.mozilla.org/es/docs/Web/API/Element/classList)
La propiedad de sólo lectura Element.classList devuelve una colección activa de DOMTokenList de los atributos de clase del elemento.

```javascript
  // div es una referencia de objeto al elemento <div> con class="foo bar"
  div.classList.remove("foo");
  div.classList.add("anotherclass");

  // si visible está presente la elimina, de lo contrario la añade
  div.classList.toggle("visible");

  // añadir/eliminar visible, dependiendo de la condición, i menor que 10
  div.classList.toggle("visible", i < 10 );

  console.log(div.classList.contains("foo"));

  // añadir o eliminar varias clases
  div.classList.add("foo", "bar");
  div.classList.remove("foo", "bar");

  // reemplazar la clase "foo" por "bar"
  div.classList.replace("foo", "bar");
```

### Eventos

En la programación tradicional, las aplicaciones se ejecutan secuencialmente de principio a fin para producir sus resultados. Sin embargo, en la actualidad el modelo predominante es el de la programación basada en eventos. Los scripts y programas esperan sin realizar ninguna tarea hasta que se produzca un evento. Una vez producido, ejecutan alguna tarea asociada a la aparición de ese evento y cuando concluye, el script o programa vuelve al estado de espera.

JavaScript permite realizar scripts con ambos métodos de programación: secuencial y basada en eventos. Los eventos de JavaScript permiten la interacción entre las aplicaciones JavaScript y los usuarios. Cada vez que se pulsa un botón, se produce un evento. Cada vez que se pulsa una tecla, también se produce un evento. No obstante, para que se produzca un evento no es obligatorio que intervenga el usuario, ya que por ejemplo, cada vez que se carga una página, también se produce un evento.

## Manejadores de Eventos

Podemos manejar los eventos de 3 maneras .

* __Desde el html__
Aca solo html

```html
<input value="Click me" onclick="alert('Click!')" type="button">
```

* __Desde una propiedad DOM__
Aca usamos html + js

```html
  <input id="elem" type="button" value="Click me">
```

```javascript
  function sayThanks() {
    alert('Thanks!');
  }

  elem.onclick = function() {
    alert('Thank you');
  };

  elem.onclick = function() { alert(1); }
  // ...
  elem.onclick = function() { alert(2); } // replaces the previous handler
```

El problema con estos 2 primeros enfoques es que solo podemos agregar un metodo por evento , si quisieramos agregar 2 eventos el ultimo remplazara al anterior. Tambien
tendremos el problema de no poder quitar un evento del element. Para manejar estos problemas el manejador de eventos __addEventListener__

* __addEventListener__
addEventListener() Registra un evento a un objeto en específico. Para registrar más de un eventListener, puedes llamar addEventListener() para el mismo elemento pero con diferentes tipos de eventos o parámetros de captura.

```javascript

```
