# ES6

## Variables

A travez de es6 la definicion de variables cambio, dandonos un alcance de bloque y evitando la elevacion o hoisting de las variables, se agregaron nuevas formas de definir valores utilizando las palabras reservadas __let__ y __const__.

## [let](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Sentencias/let)

let nos permite declarar variables y que estas respeten el alcance de bloque donde fueron declaradas, tambien las variables let no tienen elevacion y de esta manera no hay problemas de
sobre escritura de valores y tampoco tienen alcance global solo viven en el contexto de bloque donde fueron declaradas. Para acceder a las variables primero tenemos que declararlas si no estaremos entrando al TDZ(The Temporal Dead Zone) y tendremos un error de definicion.

```javascript
 /* with var */
    // window global
    var el = "sebas"; // window.el  // sebas

    // hoisting
    var name = "sebastian"
    function fn() {
        console.log(name) // undefined
        var name = "jose luis";
    }

    // scope
    function varTest() {
        var x = 31;
        if (true) {
            var x = 71;  // ¡misma variable!
            console.log(x);  // 71
        }
        console.log(x);  // 71
    }

 /* with let */
    // window global
    let el = "sebas"; // window.el // undefined

    // hoisting
    let name = "sebastian"
    function fn() {
        console.log(name) // name is not defined
        let name = "jose luis";
    }

    // scope
    function letTest() {
    let x = 31;
        if (true) {
            let x = 71;  // variable diferente
            console.log(x);  // 71
        }
        console.log(x);  // 31
    }
```

## [const](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Sentencias/const)

Las variables tipo const tienen el mismo comportamiento que las tipo let, la diferencia es que estas son variables inmutables. Esto quiere decir que no se pueden sobre escribir.
Las constantes se les tiene que definir un valor al momento de declararlas.

```javascript
    const a = 7;
```

## Strings

Se agregaron metodos para manejar substrings

### Metodos

* includes()
* startsWith()
* endsWith()
* repeat()

```javascript
let msg = "Hello world!";

console.log(msg.startsWith("Hello"));       // true
console.log(msg.endsWith("!"));             // true
console.log(msg.includes("o"));             // true
console.log("x".repeat(3));         // "xxx"
```

### Template Strings

Los template string nos dan soporte multilinea, tambien podemos agregar variables y hacer operaciones aprovechando la interpolacion de estas. Para poder definir las variables y realizar operaciones las tendremos que hacer dentro de la plantilla __${}__ ;

```javascript
    let a = 10;
    let b = 2;
    let name = 'sebastian';
    `Hola mi nombre es ${name} y la suma es = ${ a + b}` // Hola mi nombre es sebastian y la suma es = 12
```

## Functions

Es6 nos trae nuevas caracteristicas para el manejo de funciones entre estas estan:

### Argumentos por defecto

Podemos definir argumentos por defecto en la declaracion de estos, estos pueden ser cualquier tipo de valor, desde valores primitivos, hasta objetos y funciones.

```javascript
function makeRequest(url, timeout = 2000, callback = function() {}) {}
```

### Parametros rest

A travez de los parametros rest podemos obtener los argumentos restantes. Estos nos permiten representar un número indefinido de argumentos como un array.
Practicamente genera un array en base a una lista de valores.

```javascript
   function fn(...arg) {
       console.log(arg.length)
   }

   fn(1,2,3);

   function foo(a,b, ...rest) {
       console.log(a, b, rest.length)
   }

   foo(1,2,3,4,5);
```

### Destructuracion de los parametros rest

Los parámetros rest pueden ser desestructurados, eso significa que sus datos pueden ser desempaquetados dentro de distintas variables.

```javascript
function f(...[a, b, c]) {
  return a + b + c;
}

f(1)          // NaN (b y c son indefinidos)
f(1, 2, 3)    // 6
f(1, 2, 3, 4) // 6 (el cuarto parámetro no está desestructurado)
```

### Spread Operator
El operador spread genera una lista de valores a partir de un array, se podria decir que es la operacion contraria de parametros rest.
Spread operator tambien utiliza la connotacion de los "...", como los diferenciamos?? . La diferencia esta que los parametros rest lo usas en la cabezera de una funcion y
spread operator se utiliza al invocar.

```javascript
let miArray = [2, 5, 7, 1, 9];
let minimo =Math.min(...miArray); // Genera una lista de valores a partir de un array
```

### new.target

La propiedad new.target te permite detectar si una función o constructor fue llamado usando el operador new.

```javascript
function Foo() {
  if (!new.target) throw 'Foo() debe ser llamado con new';
  console.log('Foo instanciado con new');
}
```

### Arrow Functions

La expresión de función flecha tiene una sintaxis más corta que una expresión de función convencional y no vincula sus propios this, arguments, super, o new.target. Las funciones flecha siempre son anónimas. Estas funciones son funciones no relacionadas con métodos y no pueden ser usadas como constructores. El this al que apunta sera al this del padre mas cercano.

```javascript
// multiple parameters
const multiplyES6 = (x, y) => { return x * y };

// single parameter
const multiplyES6 = (x, y) => x * y;

// no parameters
var docLogEs6 = () => { console.log(document); };
```

## Objects

### Definicion inicial corta

Con es6 si el atributo y el valor tienen el mismo nombre podemos simplificarlo a un solo identificador.

```javascript
// es5
function createPerson(name, age) {
    return {
        name: name,
        age: age
    };
}

// es6
function createPerson(name, age) {
    return {
        name,
        age
    };
}
```

### Metodos concizos

Podemos escribir de manera mas corta la definicion de funciones en los objetos.

```javascript
let person = {
    name: "Nicholas",
    sayName: function() {
        console.log(this.name);
    }
};

let person = {
    name: "Nicholas",
    sayName() {
        console.log(this.name);
    }
};
```

### Metodos
Es6 nos trae nuevos metodos

* Object.is()

El método Object.is() determina si dos valores son iguales.

```javascript
Object.is('foo', 'foo');     // true
Object.is(window, window);   // true

Object.is('foo', 'bar');     // false
Object.is([], []);           // false

var test = { a: 1 };
Object.is(test, test);       // true

Object.is(null, null);       // true

// Special Cases
Object.is(0, -0);            // false
Object.is(-0, -0);           // true
Object.is(NaN, 0/0);         // true
```

* [Object​.assign()](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Object/assign)

El método Object.assign() se utiliza para copiar los valores de todas la propiedades de uno o más objetos fuente a un objeto destino.
Las propiedades en el objeto destino serán sobrescritas por las propiedades en las fuentes si tienen la misma clave.
__Object.assign(destino, ...fuentes)__

```javascript
let obj = { name: 'sebas', lastname: 'yabiku', age: 32}
let obj2 = { name: 'jose', likefood: 'pizza', pet: 'rocky'}

let obj3 = Object.assign(obj, obj2)
console.log(obj3) // {name: "jose", lastname: "yabiku", age: 32, likefood: "pizza", pet: "rocky"}


let obj = { name: 'sebas', lastname: 'yabiku', age: 32}
let obj2 = { name: 'jose', likefood: 'pizza', pet: 'rocky'}
let obj3 = { name: 'hector', likefood: 'burguer', pet: 'gardfield'}

let obj4 = Object.assign(obj, obj2, obj3);
console.log(obj4) // {name: "hector", lastname: "yabiku", age: 32, likefood: "burguer", pet: "gardfield"}
```

### Prototype

* Object​.set​PrototypeOf()

Nos ayuda a crear nuestra herencia prototipica

```javascript
let obj1 = {
  method1() {
    console.log('obj1')
  },
  method2() {
   console.log('obj2')
  }
}

let obj2 = {
  method3() {
    console.log('obj3')
  },
  method4() {
   console.log('obj4')
  }
}

let obj3 = Object.setPrototypeOf(obj1,obj2)

//obj3
    method1: ƒ method1()
    method2: ƒ method2()
    __proto__:
        method3: ƒ method3()
        method4: ƒ method4()
        __proto__: Object
```

* super

Super nos ayuda a poder alcanzar a los propiedades y metodos del padre.

```javascript
var obj1 = {
  method1() {
    console.log('method 1');
  }
}

var obj2 = {
  method2() {
   super.method1();
  }
}

Object.setPrototypeOf(obj2, obj1);
obj2.method2(); // logs "method 1"

// prototype
function Father() {
  this.sayHello = function() { console.log('hola padre')}
}

function Son() {
  this.sayHello = function() {
    //return console.log(Object.getPrototypeOf(this).sayHello.call(this))
    return super.sayHello() + ", como estas!";
  };
}

Son.prototype = new Father();

let son = new Son() // hola padre como estas
```

## [Destructuring](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Operadores/Destructuring_assignment)

La sintaxis de destructuring assignment es una expresión de JavaScript que hace posible la extracción de datos de arreglos u objetos usando una sintaxis que equivale a la construcción de arreglos y objetos literales.

```javascript
/*
*Objects*
*/
const obj = { first: 'Jane', last: 'Doe' };
const {first, last} = obj; // first = 'Jane'; last = 'Doe'

const {first: f, last: l} = obj; // f = 'Jane'; l = 'Doe'
const {a, b} = {a:1, b:2}

// objetos anidados
var metadata = {
    title: "Scratchpad",
    translations: [
       {
        locale: "de",
        localization_tags: [ ],
        last_edit: "2014-04-14T08:43:37",
        url: "/de/docs/Tools/Scratchpad",
        title: "JavaScript-Umgebung"
       }
    ],
    url: "/en-US/docs/Tools/Scratchpad"
};

var { title: englishTitle, translations: [{ title: localeTitle }] } = metadata;

// loops
var people = [
  {
    name: "Mike Smith",
    family: {
      mother: "Jane Smith",
      father: "Harry Smith",
      sister: "Samantha Smith"
    },
    age: 35
  },
  {
    name: "Tom Jones",
    family: {
      mother: "Norah Jones",
      father: "Richard Jones",
      brother: "Howard Jones"
    },
    age: 25
  }
];

for (var {name: n, family: { father: f } } of people) {
  console.log("Name: " + n + ", Father: " + f);
}
```

```javascript
/*
*Arrays*
*/
var foo = ["uno", "dos", "tres"];

// sin destructuración
var uno  = foo[0];
var dos  = foo[1];
var tres = foo[2]; // asignación en tres lineas

var [uno, dos, tres] = foo; // asignación en una sola linea

let [a, b, ...rest] = [1, 2, 3, 4, 5];

// arrays anidados
const sample = [['1', '2,', '3'], ['4', '5,', '6']]
let [[a], [b]] = sample;
console.log(a, b); // "1" "4"

// loops
const arr = ['a', 'b'];
for (const [index, element] of arr.entries()) {
    console.log(index, element);
}
// Output:
// 0 a
// 1 b

/* cambiando orden de variables */
var a = 1;
var b = 3;

[a, b] = [b, a];


// omitir valores
let colors = [ "red", "green", "blue" ];

let [ , , thirdColor ] = colors;

console.log(thirdColor);

// valores por defecto
let colors = [ "red" ];

let [ firstColor, secondColor = "green" ] = colors;
console.log(firstColor);        // "red"
console.log(secondColor);       // "green"
```

```javascript
/*
*Mixed*
*/
const obj = { a: [{ foo: 123, bar: 'abc' }, {}], b: true };
const { a: [{foo: f}] } = obj; // f = 123

let node = {
        type: "Identifier",
        name: "foo",
        loc: {
            start: {
                line: 1,
                column: 1
            },
            end: {
                line: 1,
                column: 4
            }
        },
        range: [0, 3]
    };

let {
    loc: { start },
    range: [ startIndex ]
} = node;

console.log(start.line);        // 1
console.log(start.column);      // 1
console.log(startIndex);        // 0
```

```javascript
/*
*Destructured parameters*
*/

// without destructuring
function setCookie(name, value, options) {

    options = options || {};

    let secure = options.secure,
        path = options.path,
        domain = options.domain,
        expires = options.expires;
}

setCookie("type", "js", {
    secure: true,
    expires: 60000
});


// destructuring
function setCookie(name, value, { secure, path, domain, expires }) {
}

setCookie("type", "js", {
    secure: true,
    expires: 60000
});

// other way
function setCookie(name, value, options) {
    let { secure, path, domain, expires } = options;
}

// default parameters
function setCookie(name, value,
    {
        secure = false,
        path = "/",
        domain = "example.com",
        expires = new Date(Date.now() + 360000000)
    } = {}
) {
}
```

## [Symbol](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Symbol)

Symbol es un tipo de datos cuyos valores son únicos e immutables. Dichos valores pueden ser utilizados como identificadores (claves) de las propiedades de los objetos.  Cada valor del tipo Symbol tiene asociado un valor del tipo String o Undefined que sirve únicamente como descripción del símbolo. El objetivo de los simbolos es de crear atributos privados.

```javascript
// cada vez que quiera ingresar al valor de firstName tendre que usar el simbolo
let firstName = Symbol();
let person = {};

person[firstName] = "Sebastian";
console.log(person[firstName]);     // "Nicholas"

// sin usar simbolo y poniendo una referencia de nombre, igual podriamos acceder al objeto.
let first = "name";
let person2 = {};
person2[first] = "Sebastian";
```

La funcion symbol acepta un parametro para identificarlo, un simbolo nunca sera igual a otro.

```javascript
let firstName = Symbol("first name");
let person = {};

person[firstName] = "Sebastian";

console.log("first name" in person);        // false
console.log(person[firstName]);             // "Sebastian"
console.log(firstName);                     // "Symbol(first name)"

function Animal(animal) {
  this.type = Symbol('animal');  
  this.name = animal;
  this[this.type] = animal;  

  console.log('animal symbol', this[this.type]);
}

```

Los simbolos se comportan como una constante pero nos dan una mayor flexibilidad

```javascript
const directions = {
  UP   : Symbol( ‘UP’ ),
  DOWN : Symbol( ‘DOWN’ ),
  LEFT : Symbol( ‘LEFT’ ),
  RIGHT: Symbol( ‘RIGHT’ )
};
```

## Sets and Maps

## [Sets](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Set)

El objeto Set te permite almacenar valores únicos de cualquier tipo, incluso valores primitivos u objetos de referencia.
Los objetos Set son colecciones de valores. Se puede iterar sus elementos en el orden de su inserción. Un valor en un Set sólo puede estar una vez; éste es único en la colección Set.
El objeto set es una coleccion de elementos unicos.

```javascript
let set = new Set();
set.add(5);
set.add("5");

console.log(set.size);    // 2
```

Set al almacenar solamente valores unicos, podriamos hacer lo siguiente

```javascript
function eliminateDuplicates(items) {
    return [...new Set(items)];
}

let numbers = [1, 2, 3, 3, 3, 4, 5],
    noDuplicates = eliminateDuplicates(numbers);
```

### Metodos

* __[add](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set/add):__ Agrega un nuevo elemento con el valor dado al objeto Set. Devuelve el objeto Set.

```javascript
const set1 = new Set();

set1.add(42);
set1.add(42);
set1.add(13);

for (let item of set1) {
  console.log(item);
  // expected output: 42
  // expected output: 13
}

```

* __[size](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set/size):__ Retorna la cantidad de elementos del objeto Set

```javascript
const set1 = new Set();
var object1 = Object.create(null);

set1.add(42);
set1.add('forty two');
set1.add('forty two');
set1.add(object1);

console.log(set1.size);
// expected output: 3
```

* __[clear](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set/clear):__ Remueve todos los elementos de un objeto Set

```javascript
const set1 = new Set();
set1.add(1);
set1.add('foo');

console.log(set1.size);
// expected output: 2

set1.clear();

console.log(set1.size);
// expected output: 0
```

* __[delete](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set/delete)__ Elimina el elemento especificado

```javascript
const set1 = new Set();
set1.add({x: 10, y: 20}).add({x: 20, y: 30});

// Delete any point with `x > 10`.
set1.forEach(function(point){
  if (point.x > 10) {
    set1.delete(point);
  }
});

console.log(set1.size);
// expected output: 1
```

* __[entries](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set/entries)__ El método entries () devuelve un nuevo objeto Iterator que contiene una matriz de [valor, valor] para cada elemento en el objeto Set, en orden de inserción. Para los objetos Set no hay una clave como en los objetos Map. Sin embargo, para mantener la API similar al objeto Map, cada entrada tiene el mismo valor para su clave y valor aquí, de modo que se devuelve una matriz [valor, valor].

```javascript
const set1 = new Set();
set1.add(42);
set1.add('forty two');

const iterator1 = set1.entries();

for (let entry of iterator1) {
  console.log(entry);
  // expected output: [42, 42]
  // expected output: ["forty two", "forty two"]
}
```

* __[forEach](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set/forEach)__  Ejecuta una funcion por cada valor del elemento Set

```javascript
function logSetElements(value1, value2, set) {
  console.log('s[' + value1 + '] = ' + value2);
}

new Set(['foo', 'bar', undefined]).forEach(logSetElements);

// expected output: "s[foo] = foo"
// expected output: "s[bar] = bar"
// expected output: "s[undefined] = undefined"
```

* __[has](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set/has)__ El metodo has devuelve un valor booleano indicando si el valor existe.

```javascript
const set1 = new Set([1, 2, 3, 4, 5]);

console.log(set1.has(1));
// expected output: true

console.log(set1.has(5));
// expected output: true

console.log(set1.has(6));
// expected output: false
```

* __[values](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set/values)__ Retorna un iterador object que contiene los valores de cada elemento en el orden de insercion de Set.

```javascript
const set1 = new Set();
set1.add(42);
set1.add('forty two');

var iterator1 = set1.values();

console.log(iterator1.next().value);
// expected output: 42

console.log(iterator1.next().value);
// expected output: "forty two"
```

* __[[@@iterator]](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set/@@iterator)__ Nos permite iterar el objeto Set

```javascript
const set1 = new Set();

set1.add(42);
set1.add('forty two');

const iterator1 = set1[Symbol.iterator]();

console.log(iterator1.next().value);
// expected output: 42

console.log(iterator1.next().value);
// expected output: "forty two"
```

## [WeakSet](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/WeakSet)

Los objetos WeakSet son colecciones de objetos. Un objecto en WeakSet solo puede ser agregado una vez; Esto quiere decir que es unico en la coleccion WeakSet, a diferencia de set WeakSet no puede almacenar mas que objetos no soporta otros tipos

### Metodos

* __[add](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/WeakSet/add)__ El método add () agrega un nuevo objeto al final de un objeto WeakSet.

```javascript
const weakset1 = new WeakSet();
const object1 = {};

weakset1.add(object1);
console.log(weakset1.has(object1));
// expected output: true
```

* __[delete](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/WeakSet/delete)__ El metodo delete remueve el elemento especificado

```javascript
const weakset1 = new WeakSet();
const object1 = {};

weakset1.add(object1);

console.log(weakset1.has(object1));
// expected output: true

weakset1.delete(object1);

console.log(weakset1.has(object1));
// expected output: false
```

* __[has](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/WeakSet/has)__ Retorna un booleano si el objeto existe.

```javascript
const weakset1 = new WeakSet();
const object1 = {};
const object2 = {};

weakset1.add(object1);

console.log(weakset1.has(object1));
// expected output: true

console.log(weakset1.has(object2));
// expected output: false
```

## [Map](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Map)

El objeto Map almacena pares clave/valor. Cualquier valor (tanto objetos como valores primitivos) pueden ser usados como clave o valor.

Un objeto Map puede iterar sobre sus elementos en orden de inserción. Un bucle for..of devolverá un array de [clave, valor] en cada iteración.

Las claves de un mapa pueden ser de cualquier tipo.

```javascript
 const map = new Map(); // create an empty Map
 const KEY = {};
 map.set(KEY, 123);
 map.get(KEY)
```

### Metodos

Los metodos de map son los mismos de Set

## [WeakMap](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/WeakMap)

El objeto WeakMap es una colección de pares clave/valor en la que las claves solo pueden ser objetos y los valores pueden ser de cualquier tipo.

```javascript
var wm1 = new WeakMap(),
    wm2 = new WeakMap(),
    wm3 = new WeakMap();
var o1 = {},
    o2 = function(){},
    o3 = window;

wm1.set(o1, 37);
wm1.set(o2, "azerty");
wm2.set(o1, o2); // un valor puede ser cualquier cosa, incluidos objetos o funciones
wm2.set(o3, undefined);
wm2.set(wm1, wm2); // claves y valores pueden ser objetos cualesquiera. !Incluso WeakMaps!

wm1.get(o2); // "azerty"
wm2.get(o2); // undefined, porque no hay valor para o2 en wm2
wm2.get(o3); // undefined, porque es es el valor del conjunto
wm1.has(o2); // true
wm2.has(o2); // false
wm2.has(o3); // true (incluso si el valor es 'undefined')

wm3.set(o1, 37);
wm3.get(o1); // 37

wm1.has(o1);   // true
wm1.delete(o1);
wm1.has(o1);   // false
```

### Metodos

Todas las instancias de WeakMap heredan de WeakMap.prototype.

* __[delete](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/WeakMap/delete)__ Elimina un elemento especifico de un WeakMap

```javascript
const weakmap1 = new WeakMap();
const object1 = {};

weakmap1.set(object1, 42);

console.log(weakmap1.delete(object1));
// expected output: true

console.log(weakmap1.has(object1));
// expected output: false
```

* __[get](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/WeakMap/get)__ Retorna un elemento especifico

```javascript
const weakmap1 = new WeakMap();
const object1 = {};
const object2 = {};

weakmap1.set(object1, 42);

console.log(weakmap1.get(object1));
// expected output: 42

console.log(weakmap1.get(object2));
// expected output: undefined
```

* __[has](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/WeakMap/has)__ Retorna un boolean indicando si existe el elemento

```javascript
const weakmap1 = new WeakMap();
const object1 = {};
const object2 = {};

weakmap1.set(object1, 'foo');

console.log(weakmap1.has(object1));
// expected output: true

console.log(weakmap1.has(object2));
// expected output: false
```

* __[set](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/WeakMap/set)__  Agrega un nuevo elemento

```javascript
const weakmap1 = new WeakMap();
const object1 = {};
const object2 = {};

weakmap1.set(object1, 'foo');
weakmap1.set(object2, 'bar');

console.log(weakmap1.get(object1));
//expected output: "foo"

console.log(weakmap1.get(object2));
//expected output: "bar"
```

## Arrays

Es6 trae nuevos metodos para la creacion y manejo de arrays

### Metodos

* __[Array.of()](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Array/of)__ El método Array.of() crea una nueva instancia Array con un número variable de elementos pasados como argumento, independientemente del número o del tipo.

```javascript
Array.of(7);       // [7]
Array.of(1, 2, 3); // [1, 2, 3]

Array(7);          // [ , , , , , , ]
Array(1, 2, 3);    // [1, 2, 3]
```

* __[Array.from()](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Array/from)__ El método Array.from() crea una nueva instancia de Array a partir de un objeto iterable.

```javascript
console.log(Array.from('foo'));
// expected output: Array ["f", "o", "o"]

console.log(Array.from([1, 2, 3], x => x + x));
// expected output: Array [2, 4, 6]
```

* __[find()](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Array/find)__ El método find() devuelve el valor del primer elemento del array que cumple la función de prueba proporcionada. En cualquier otro caso se devuelve undefined.

```javascript
var array1 = [5, 12, 8, 130, 44];

var found = array1.find(function(element) {
  return element > 10;
});

console.log(found);
// expected output: 12
```

* __[findIndex()](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Array/findIndex)__ El método findIndex() devuelve el índice del primer elemento de un array que cumpla con la función de prueba proporcionada. En caso contrario devuelve -1.

```javascript
var array1 = [5, 12, 8, 130, 44];

function isLargeNumber(element) {
  return element > 13;
}

console.log(array1.findIndex(isLargeNumber));
// expected output: 3

```

* __[fill](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Array/fill)__ El método fill() rellena todos los elementos de un arreglo desde el índice start hasta el índice end, con el valor estático de value.

```javascript
var array1 = [1, 2, 3, 4];

// fill with 0 from position 2 until position 4
console.log(array1.fill(0, 2, 4));
// expected output: [1, 2, 0, 0]

// fill with 5 from position 1
console.log(array1.fill(5, 1));
// expected output: [1, 5, 5, 5]

console.log(array1.fill(6));
// expected output: [6, 6, 6, 6]
```

* __[copyWithin](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Array/copyWithin)__ El método copyWithin() transfiere una copia  plana de una sección a otra dentro del mismo array ( o contexto similar ), sin modificar su propiedad length y lo devuelve.

```javascript
var array1 = ['a', 'b', 'c', 'd', 'e'];

// copy to index 0 the element at index 3
console.log(array1.copyWithin(0, 3, 4));
// expected output: Array ["d", "b", "c", "d", "e"]

// copy to index 1 all elements from index 3 to the end
console.log(array1.copyWithin(1, 3));
// expected output: Array ["d", "d", "e", "d", "e"]
```

## Modulos

Los modulos son piezas de código que podemos escribir en ficheros independientes. Los módulos pueden tener código, como clases, funciones, objetos o simples datos primitivos, que se puede importar desde otros archivos.

Con la palabra __"export"__ consigues exponer algún miembro del módulo, para que se pueda usar desde fuera. Con la palabra __"import"__ consigues traerte algo exportado por un módulo independiente.

* __[export](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Sentencias/export)__ Con la palabra reservador export podemos exportar los elementos que deseemos.

```javascript
// example 1
// export for default lib.js
export default function() { console.log('default')}
import m import 'lib.js';

// example 2
function cube(x) {
  return x * x * x;
}
const foo = Math.PI + Math.SQRT2;
var graph = {
    options:{
        color:'white',
        thickness:'2px'
    },
    draw: function(){
        console.log('From graph draw function');
    }
}
export { cube, foo, graph };

// example 3
export { import1 as name1, import2 as name2 }
```

* __[import](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Sentencias/import)__ La sentencia import se usa para importar funciones que han sido exportadas desde un módulo externo.

```javascript
import {myExport} from '/modules/my-module.js';
import {foo, bar} from "my-module.js";
import {reallyReallyLongModuleExportName as shortName}
  from '/modules/my-module.js';

import '/modules/my-module.js';

import myDefault from '/modules/my-module.js';
import * as myModule from '/modules/my-module.js';

```

## [Classes](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Classes)

Las clases de javascript, introducidas en ECMAScript 2015, son una mejora sintáctica sobre la herencia basada en prototipos de JavaScript. La sintaxis de las clases no introduce un nuevo modelo de herencia orientada a objetos en JavaScript. Las clases de JavaScript proveen una sintaxis mucho más clara y simple para crear objetos y lidiar con la herencia.

```javascript
class Poligono {
  constructor (height, width) {
    this.height = height;
    this.width = width;
  }
  // Getter
  get   area  ()   {
     return this.calcArea();
   }
  // Método
  calcArea () {
    return this.height * this.width ;
  }
}

const cuadrado = new Poligono (10, 10);

console.log(cuadrado.area); // 100 
```

### Izado (Hoisting)

Las clases no son izadas como las funciones, osea primero tenemos que declarar nuestras clases y luego recien usarlas.

```javascript
const p = new Poligono(); // ReferenceError

class Poligono {}
```

### Metodos estaticos

La palabra clave static define un método estático para una clase. Los métodos estáticos son llamados sin instanciar su clase y no pueden ser llamados mediante una instancia de clase. Los métodos estáticos son a menudo usados para crear funciones de utilidad para una aplicación.

```javascript
class Punto {
  constructor ( x , y ){
    this.x = x;
    this.y = y;
  }

  static distancia ( a , b) {
    const dx = a.x - b.x;
    const dy = a.y - b.y;

    return Math.sqrt ( dx * dx + dy * dy );
  }
}

const p1 = new Punto(5, 5);
const p2 = new Punto(10, 10);

console.log (Punto.distancia(p1, p2)); // 7.0710678118654755
```

### Herencia

La palabra clave extends es usada en declaraciones de clase o expresiones de clase para crear una clase hija.

```javascript
class Animal {
  constructor(nombre) {
    this.nombre = nombre;
  }

  hablar() {
    console.log(this.nombre + ' hace un ruido.');
  }
}

class Perro extends Animal {
  hablar() {
    console.log(this.nombre + ' ladra.');
  }
}
```

También se pueden extender las clases tradicionales basadas en funciones:

```javascript
function Animal (nombre) {
  this.nombre = nombre;
}
Animal.prototype.hablar = function () {
  console.log(this.nombre + 'hace un ruido.');
}

class Perro extends Animal {
  hablar() {
    super.hablar();
    console.log(this.nombre + ' ladra.');
  }
}

var p = new Perro('Mitzie');
p.hablar();
```

### Super

La palabra clave super es usada para llamar funciones del objeto padre.

```javascript
class Gato {
  constructor(nombre) {
    this.nombre = nombre;
  }

  hablar() {
    console.log(this.nombre + ' hace ruido.');
  }
}

class Leon extends Gato {
  hablar() {
    super.hablar();
    console.log(this.nombre + ' maulla.');
  }
}
```

## Programacion Asincrona

Que es asincrono ? Un evento o funcion asincrona es algo que no sabemos cuando se va resolver , puede resolverse ahora como mañana o nunca. Para poder manejar eventos asincronos tenemos los
objetos [promise](https://developer.mozilla.org/es/docs/Web/JavaScript/Guide/Usar_promesas) y a estos objetos le encadenamos funciones [callback](https://developer.mozilla.org/es/docs/Glossary/Callback_function) para poder resolver los estados de este ojbeto promise.

### Promise

El objeto Promise (Promesa) es usado para computaciones asíncronas. Una promesa representa un valor que puede estar disponible ahora, en el futuro, o nunca.

Los estados de una promesa son

* __pendiente (pending)__: estado inicial, no cumplida o rechazada.
* __cumplida (fulfilled)__: significa que la operación se completó satisfactoriamente.
* __rechazada (rejected)__: significa que la operación falló.

Con los metodos __[then](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Promise/then)__ y __[catch](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Promise/catch)__ podemos manejar las promesas y estos pueden ser encadenados ya que devuelven una promesa tambien.

### Sintaxis

Las promesas se crean inicializando el objeto Promise, estos tienen 2 parametros, __resolve__ y __reject__.

```javascript
new Promise( /* ejecutor */ function(resolver, rechazar) {} );
```

### Metodos

Una vez inicializado el objeto podemos acceder a sus metodos.

* [all()](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Promise/all)

El método Promise.all(iterable) devuelve una promesa que termina correctamente cuando todas las promesas en el argumento iterable han sido concluídas con éxito, o bien rechaza la petición con el motivo pasado por la primera promesa que es rechazada.

* [race()](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Promise/race)

El método Promise.race(iterable) retorna una promesa que se cumplirá o no tan pronto como una de las promesas del argumento iterable se cumpla o se rechace, con el valor o razón de rechazo de ésta.

* [reject()](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Promise/reject)

El método Promise.reject(reason) retorna un objeto Promise que es rechazado por la razón específicada.

* [resolve()](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Promise/resolve)

El método Promise.resolve(value) retorna un objeto Promise que es resuelto con el valor dado. Si el valor es una promise, esa promise es devuelta; si el valor es un thenable (si tiene un método "then"), el valor devuelto le seguirá a ese thenable, adoptando su estado; de otro modo la promise devuelta estará completada con el valor.

* [then()](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Promise/then)

El método then() retorna una Promesa. Recibe dos argumentos: funciones callback  para los casos de éxito y fallo de Promise.

```javascript
var promise1 = new Promise(function(resolve, reject) {
  resolve('Success!');
});

promise1.then(function(value) {
  console.log(value);
  // expected output: "Success!"
});
```

* [catch()](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Promise/catch)

El método catch() retorna una Promise y solo se ejecuta en los casos en los que la promesa se marca como Reject. Se comporta igual que al llamar Promise.prototype.then(undefined, onRejected) (de hecho, al llamar obj.catch(onRejected) internamente llama a obj.then(undefined, onRejected)).

```javascript
var promise1 = new Promise(function(resolve, reject) {
  throw 'Uh-oh!';
});

promise1.catch(function(error) {
  console.log(error);
});
// expected output: Uh-oh!
```

* [async()](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Sentencias/funcion_asincrona) La declaración de función async define una función asíncrona, la cual devuelve un objeto AsyncFunction. Este nos devuelve una promesa resuelta. Async se asegura que lo que devuelve la funcion sea una promesa.

```javascript
async function f() {
  return 1;
}

f().then(alert); // 1

async function f() {
  return Promise.resolve(1);
}

f().then(alert); // 1
```

* [await](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Operadores/await)

El operador await es usado para esperar a una Promise. Sólo puede ser usado dentro de una función async function. Await espera hasta que la promesa sea resuelta. Await pausa la ejecucion
de la funcion hasta q todas las promesas se cumplan.

```javascript
async function f() {

  let promise = new Promise((resolve, reject) => {
    setTimeout(() => resolve("done!"), 1000)
  });

  let result = await promise; // wait till the promise resolves (*)

  alert(result); // "done!"
}

f();
```

## [Fetch](https://developer.mozilla.org/es/docs/Web/API/Fetch_API/Utilizando_Fetch)

La API Fetch proporciona una interfaz JavaScript para acceder y manipular partes del canal HTTP, como peticiones y respuestas. También provee un método global fetch() que proporciona una forma fácil y lógica de obtener recursos de forma asíncrona por la red.

```javascript
fetch('http://example.com/movies.json')
  .then(function(response) {
    return response.json();
  })
  .then(function(myJson) {
    console.log(myJson);
  });
```