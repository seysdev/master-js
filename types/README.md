# Tipos de datos
En javascript el tipado es dinámico, se define el tipo en tiempo de ejecucion, en base al valor de la variable. En Javascript existen 7 tipos de datos.

## Primitivos 
* __String__ Cadenas de texto.
* __Number__ Enteros, [flotantes](https://es.wikipedia.org/wiki/Coma_flotante).
* __Boolean__ true y false.
* __null__ Es un valor asignado tiene el valor de “no valor”.
* __undefined__ Una variable a la que no se le ha asignado ningún valor tiene el valor undefined.
* __Symbol__ Un unico valor que no es igual a otro valor.

## De Objeto
Todo lo demas es un tipo objeto.
* __Object__ 

Estos tipos se dividen en dos grupos, Primitivos y de Objeto.

Todos los primitivos no son objetos  y estos no tienen metodos propios. Todos los primitivos son inmutables.

No hay que confundir los primitivos con los contructores de estos. Cada primitivo tiene un constructor u objeto principal. JS sabe que cuando intentas acceder a un método en una primitiva y detrás de la escena, usará el constructor para hacer que un objeto salga de tu primitiva. Una vez que ejecuta el método, ese objeto se recolecta en la basura. (eliminado de la memoria)

## Valores primitivos versus objects
La diferencia mas importante entre estos dos; 

### Primitivos
* El contenido es comparable
* Las propiedades son inmutables
```
let prim1 = '123';
let prim2 = '123';

prim1 === prim2
//true

prim1.length = 1; // try to change property `length`
str.length      // ⇒ no effect
//3
```

### Objects 
* No se puede comparar por valor
* Si puedes comparar por referencia
* Las propiedades son mutables
```
let obj1 = {};  // an empty object
let obj2 = {};  // another empty object
let obj3 = obj1

obj1 === obj2
//false

obj1 === obj3
//true

let obj = {};
obj.foo = 123; // add property `foo`
obj.foo
//123
```

## Categorizar valores usando typeof y instanceof
__Typeof__ lo usamos para verificar los tipos de datos, se usa para los valores primitivos y tambien tenemos instanceof para los __objetos__
```
typeof true
'boolean'
typeof 'abc'
'string'
typeof {} // empty object literal
'object'
typeof [] // empty array literal
'object'
```

```
let arr1 = [];
arr instanceof Array;
// true

let b = new Bar();  // object created by constructor Bar
b instanceof Bar
// true
```

## Conversion de tipos de datos
Para convertir los tipos de datos de un tipo a otro tenemos los siguientes metodos.

### Convertir string a números

* parseInt()
* parseFloat()

```
parseInt("9999.12323213")
// 9999

parseFloat("9999.12323213")
//9999.12323213
```

### Convertir numero a string
* toString()

```
let a = 14;
a.toString();

// "14"
```

### Convertir diferentes tipos
```
let x = false;

Number(x)
// 0
String(x)
// "0"
Boolean(x)
// false
```

## Enlaces de interes 
* [types](https://developer.mozilla.org/es/docs/Web/JavaScript/Guide/Grammar_and_types)
* [types2](https://javascript.info/types)