# Estructuras de datos

Para manejar estructura de datos en JS tenemos:

* Arrays
* Objetos
* Map y Set

## Arrays

Una  matriz o array es un conjunto ordenado de valores de cualquier tipo, al que se refiere con un nombre y un índice. 
Las siguientes declaraciones crean matrices equivalentes :

```javascript
let arr = new Array(element0, element1, ..., elementN);
let arr = Array(element0, element1, ..., elementN);
let arr = [element0, element1, ..., elementN];

let colores =  new Array(); 
let colores = new Array(10); 
let colores = [];
```

Para acceder a un valor dentro de un array se hace a travez de su indice

```javascript
let colores = ["rojo", "azul ", " verde "] ; 
console.log(colores[1]);
// "azul"
```

Tambien podemos modificar el valor a travez del indice

```javascript
let colores = ["rojo", "azul", "verde "] ; 
colores[0] = "red";
// ["red", "azul", "verde"]
```

### Algunos Metodos de array

Un array es un objeto y como un objeto este tiene metodos asociados que son:

#### toString()

Convierte un array a strings;

```javascript
let fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.toString();
// Banana,Orange,Apple,Mango
```

#### join()

Une todos los elementos en un string, le podemos pasar como parametro el separador de los elementos

```javascript
let fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.join(" * ");
// Banana * Orange * Apple * Mango
```

#### pop()

Remueve el ultimo elemento de un Array

```javascript
let fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.pop();
// ["Banana", "Orange", "Apple"];
```

#### push()

Agrega un nuevo elemento al final del Array

```javascript
let fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.push("Kiwi"); 
// ["Banana", "Orange", "Apple", "Mango", "Kiwi"];
```

#### shitf()

Remueve el primer elemento de un Array

```javascript
let fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.shift();  
// ["Orange", "Apple", "Mango", "Kiwi"];
```

#### unshift()

Agrega un elemento al inicio de un Array

```javascript
let fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.unshift("Lemon");  
// ["Lemon", "Orange", "Apple", "Mango", "Kiwi"];
```

[ver mas metodos de Array](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Array)

## Objetos

Un objeto es una colección de datos relacionados y / o funcionalidad (que generalmente consta de varias variables y funciones, que se denominan propiedades y métodos cuando están dentro de objetos).

Para construir objetos podemos hacerlo de tres maneras,

### Objetos declarativos o literales 

Podemos crear objetos sin necesidad de un constructor o instanciar una clase, para esto solo declaramos el objeto y sus propiedades.

```javascript
const camilo = {
  nombre: 'Camilo',
  edad: 22,
  sexo: 'masculino',
  pasatiempos: ['patinar', 'bailar'],
  hablar: function(){
    return `hola soy ${this.nombre}, y tengo ${this.edad} años`;
  }
}

console.log(camilo);
```

### Objetos construidos

JavaScript es un lenguaje libre de clases, pero tenemos el keyword new, el cual nos permite crear un nuevo objeto, de esta manera podemos utilizar una función que cumpla el rol del constructor.

```javascript
function Persona(nombre, edad, sexo, pasatiempos) {
  this.nombre = nombre;
  this.edad = edad;
  this.sexo = sexo;
  this.pasatiempos = pasatiempos;
  this.hablar = function() {
    return `hola soy ${this.nombre}, y tengo ${this.edad} años`;
  };
}

const camilo = new Persona('camilo', 22, 'masculino', ['patinar', 'bailar']);

console.log(camilo)
```

### Object.create()

El método Object.create() crea un objeto nuevo, utilizando un objeto existente como el prototipo del nuevo objeto creado.

```javascript
const person = {
  isHuman: false,
  printIntroduction: function () {
    console.log(`My name is ${this.name}. Am I human? ${this.isHuman}`);
  }
};

const me = Object.create(person);

me.name = "Matthew"; // "name" is a property set on "me", but not on "person"
me.isHuman = true; // inherited properties can be overwritten

me.printIntroduction();
```

Al iniciar el object podemos configurar los atributos de estos.

```javascript
const prototypeObject = {
  fullName: function(){
    return this.firstName + " " + this.lastName
  }
}

var person = Object.create(prototypeObject, {
  'firstName': {
    value: "Virat",
    writable: true,
    enumerable: true
  },
  'lastName': {
    value: "Kohli",
    writable: true,
    enumerable: true
  }
})
```

Para acceder a las propiedades o modificar esas se puede hacer de 2 maneras

* notación con .
* notación con []

```javascript
const myObj = {
  nombre: 'yeison',
  hablar: function(){
    return `hola soy ${this.nombre}`;
  }
}

console.log(myObj.nombre); //yeison

const propiedad = 'nombre'

console.log(myObj[propiedad]); //yeison
```

### Algunos Metodos de Object

Un Objeto hereda propiedades y metodos a travez de su herencia prototipica y algunos de estos son:

[objetos](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Object)