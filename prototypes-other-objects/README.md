# Prototipos

Prototype es la herencia de atributos y metodos a travez del prototype de los objetos, todo objeto vienen con su prototype. A travez del prototype, podemos heredar atributos y metodos
un objeto que busca un atributo o metodo en su propio prototipo si no lo encuentra, buscara en el prototipo siguiente, si no lo encuentra buscara en el siguiente y asi sucesivamente
hasta encontrarse con un prototipo null.

## Accediendo a los atributos

Tenemos el prototipo de funcion y el prototipo de un objeto literal.

### __proto__

```javascript
    let obj = {}
    console.log(obj.__proto__);
```

### prototype

```javascript
function fn() { }
    console.log(fn.prototype)
    console.log(fn.prototype.__proto__)
```

## Cadena prototipica

La cadena de prototipos se basa en la herencia , esto quiere decir que cuando un atributo se busque en el objeto principal si no se 
encuentra buscara en su herencia o objeto prototipico encadenado a este. Hara esta busqueda hasta encontrarse con el valor null y este valor no tiene herencia y terminara la busqueda.

En javascript el prototipo principal es el objeto, si buscamos el proto de un objeto nos dara null.

```javascript
console.log(Object.prototype)
console.log(Object.prototype.__proto__)
```

La cadena prototipica se referencia de arriba a abajo y el objeto que usamos es el que esta mas abajo

```javascript
 __proto__ === null
|
|
__proto__ === Object.prototype
|
|
{ object literal }
```

## Creando nuestra herencia prototipica

Podemos crear herencia prototipica a travez de prototype de esta manera

```javascript
function Fn() { }
Fn.prototype.print = function () {
    console.log("Calling Fn.prototype's print method");
};
let obj = new Fn();
obj.print();
```

Pero esto no seria igual a esto??

```javascript
function Fn() {
    this.print = function () {
        console.log("Calling the object's print method");
    };
}
var obj = new Fn();
obj.print();
```

En terminos practicos seria lo mismo, pero la gran diferencia es en el performance. Si creamos los metodos dentro de la funcion con 20 metodos e instanciaramos unas mil veces esta funcion
tendriamos mil objetos con 20 mil metodos, en cambio si creamos los 20 metodos con herencia solo tendriamos mil instancias pero con 20 metodos heredados.

### Entonces recapitulando los prototipos son la herencia entre objetos y de esta manera poder usar sus atributos y metodos entre ellos

```javascript
let obj = {};
let arr = [];
    function fn() { }
    console.log(obj.__proto__ === Object.prototype); // -> true
    console.log(arr.__proto__ === Array.prototype); // -> true
    console.log(fn.__proto__ === Function.prototype); // -> true
```

## Constructor

El prototipo de una funcion tiene una propiedad constructor esta apunta a la funcion en si misma. Es util para que nos indique quien creo el objeto.

```javascript
function Fn() { }
    console.log(Fn.prototype.constructor === Fn);
    // -> true
```

## Object Create

A travez de object create podemos crear objectos con herencia prototipica , solo pasandole como primer argumento el objeto a heredar. De esta manera podemos objtener cualquier
objeto y utilizar sus metodos o propiedades.

```javascript
var prototypeObj = {
        testValue: 'Hello!'
    };
    var obj = Object.create(prototypeObj);
    console.log(obj); // -> {}
    console.log(obj.__proto__ === prototypeObj); // -> true
    console.log(obj.testValue); // -> 'Hello!'
```

## Enlaces de interes

* [Master JavaScript Prototypes & Inheritance](https://codeburst.io/master-javascript-prototypes-inheritance-d0a9a5a75c4e)
* [What’s the Difference Between Class & Prototypal Inheritance?](https://medium.com/javascript-scene/master-the-javascript-interview-what-s-the-difference-between-class-prototypal-inheritance-e4cd0a7562e9)
* [A Beginner's Guide to JavaScript's Prototype
](https://tylermcginnis.com/beginners-guide-to-javascript-prototype/)
* [Herencia y la cadena de prototipos](https://developer.mozilla.org/es/docs/Web/JavaScript/Herencia_y_la_cadena_de_protipos)