# Function 

Son un conjunto de sentencias que realizan una tarea o calculan un valor.
Para definir una funcion se utiliza la palabra reservada function seguido del nombre de la funcion y seguido de parentesis donde definimos los argumentos a recibir.

```javascript
function square(number) {
  return number * number;
}
```

## Exprecion de funcion

Si bien la declaración de la función anterior es sintácticamente una sentencia, las funciones pueden también ser creadas por una expresión de función. Tal función puede ser anónima; no debe tener un nombre. Por ejemplo.

```javascript
let sumar = function(a) {
    return a + 2;
}

sumar(2); // 4

let sumar = function sumar() {
    return a + 2;
}
```

## Recursividad

La recursividad consiste en funciones que se llaman a sí mismas, evitando el uso de bucles y otros iteradores.

Uno ejemplo fácil de ver y que se usa a menudo es el cálculo del factorial de un número entero. El factorial de un número se define como ese número multiplicado por el anterior, éste por el anterior, y así sucesivamente hasta llegar a 1. Así, por ejemplo, el factorial del número 5 sería: 5x4x3x2x1 = 120.

usando bucles seria:

```javascript
function factorial(n){
  let res = 1;
  for(let i=n; i>=1; i--){
    res = res * i;
  }
  return res;
}
```

usando recursividad seria:

```javascript
function factorial(n) {
    if (n<=1) return 1;
    return n* factorial(n-1);
}
```

## Closures

Los closures son funciones anidadas que nos permiten tener acceso a variables externas y manipular estas variables externas si necesidad de poner en riesgo nuestras funciones internas, ya que por cada llamada  

Los clousures es una funcion que devuelve funciones , que nos permite manipular el ambito externo sin poner en riesgo nuestro ambito interno. Un clousure esta pensado para que se adapte a distintos ambitos.

```javascript
let createPet = function(name) {
  let sex;
  
  return {
    setName: function(newName) {
      name = newName;
    },
    getName: function() {
      return name;
    },
    getSex: function() {
      return sex;
    },
    setSex: function(newSex) {
      if(typeof newSex == "string" && (newSex.toLowerCase() == "male" || newSex.toLowerCase() == "female")) {
        sex = newSex;
      }
    }
  }
}

let pet = createPet("Vivie");
pet.getName();                  // Vivie

pet.setName("Oliver");
pet.setSex("male");
pet.getSex();                   // male
pet.getName();                  // Oliver
```

## Argumentos

Los argumentos de una función son mantenidos en un objeto similar a un array. Dentro de una función, los argumentos pasados a la misma pueden ser direccionados de la siguiente forma:

```javascript
arguments[i]
```

### ES6

### Parametros por defecto

```javascript
function multiply(a, b = 1) {
  return a*b;
}
multiply(5); // 5
```

### Parametros rest

La syntaxis de parámetros rest (en inglés) nos permite respresentar un número indefinido de argumentos en forma de array. 

```javascript
function multiply(multiplier, ...theArgs) {
  return theArgs.map(x => multiplier * x);
}

var arr = multiply(2, 1, 2, 3);
console.log(arr); // [2, 4, 6]
```

## Funciones Flecha

Una expresión de función flecha (también conocida como función flecha gruesa o fat arrow function en inglés) tiene una sintaxis más corta comparada con las expresiones de función y no tiene su propio this, arguments, super o new.target. Las funciones flecha toman el this de su contenedor o si este no tiene sera undefined.

```javascript
Sintaxis Básica

(param1, param2, …, paramN) => { sentencias }
(param1, param2, …, paramN) => expresion

```

## Entendiendo el this

La clave para entender el comportamiento de this, es tener claro donde se invoca( el contexto de la funcion), para saber qué objeto le asigna.

### Caso 1

```javascript
let yo = {
  nombre: 'sebastian',
  edad: 22,
  hablar: function () {
    console.log(this.nombre);
  }
};

yo.hablar(); // sebastian
```

this, hace referencia al objeto, que contiene el método donde se invoca.

### Caso 2

En este caso, existe una función que recibe un objeto como parámetro, y le agrega el método hablar, luego, se ejecuta la función sobre dos objetos.

```javascript
let decirNombre = function(obj) {
  obj.hablar = function() {
  console.log(this.nombre);
  };
};

const Mateo = {
  nombre: ‘Mateo’,
  edad: 22
};

const juan = {
  nombre: ‘Juan’,
  edad: 25
};

decirNombre(juan);
decirNombre(Mateo);

juan.hablar(); // Juan
Mateo.hablar(); // Mateo
```

This en este caso hace referencia al objeto que se añade este método.

### Caso 3

```javascript
let Persona = function (nombre, edad, madre) {
  return {
    nombre: nombre,
    edad: edad,
    hablar: function() {
      console.log(this.nombre);
    },
    madre: {
      nombre: madre,
      hablar: function() {
        console.log(this.nombre);
      }
    }
  };
};

const ana = Persona(‘Ana’, 30, ‘Clara’);

ana.hablar(); // Ana
ana.madre.hablar(); // Clara
```

### Asignación con new

Otro caso, es cuando invocamos this en un constructor , como el siguiente ejemplo:

```javascript
let Animal = function(color, nombre, tipo) {
  this.color = color;
  this.nombre = nombre;
  this.tipo = tipo;
}

const bipa = new Animal(‘gris’, ‘Bipa’, ‘Felino’);
```

En este caso, this hace referencia al objeto que se instanciando.
