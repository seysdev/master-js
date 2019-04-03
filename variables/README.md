# Variables
Las variables se usan como nombres simbólicos para valores en tu aplicación. Los nombres de las variables, llamados identificadores, se rigen por ciertas reglas.

Un identificador en JavaScript tiene que empezar con una letra, un guión bajo (_) o un símbolo de dólar ($); los valores subsiguientes pueden ser números. Debido a que JavaScript diferencia entre mayúsculas y minúsculas, las letras incluyen tanto desde la "A" hasta la "Z" (mayúsculas) como de la "a" hasta la "z".

Para declarar variables podemos usar 

* __var__
Declara una variable, inicializándola opcionalmente a un valor.
```
var name = "sebastian";
```

* __let__
Declara una variable local en un bloque de ámbito, inicializándola opcionalmente a un valor.

```
let name = "sebastian";
```

* __const__
Declara una constante de sólo lectura en un bloque de ámbito.
```
const name = "sebastian";
```

## Scope de una variable

El scope __(ámbito o alcance)__ de una variable es el contexto en el cual la variable existe, este nos indica en qué partes del programa podemos acceder a esa variable o si tenemos acceso a la misma. En JavaScript existen dos tipos de scope: local y global, cada uno tiene sus propias reglas operación y mejores prácticas, conocerlas nos ayudará a escribir código de mayor calidad.

### Scope Global
Toda variable que se declare fuera de una función tiene un scope global, es decir, puede ser accedida desde cualquier punto del programa, todos la pueden ver y modificar.La ventaja es que se pueden declarar de manera fácil y podemos compartir datos con diferentes componentes de la aplicación. Sin embargo, las variables declaradas en global scope rápidamente pueden ser causa de problemas, principalmente la colisión de nombres.

```
var suma = 0;
var i = 0;
 
function calculaSuma() {
  for (i = 1; i <= 10; i++) {
    suma += i;		
  }
	
  console.log(suma);
}
 
function calculaPromedio() {
  for (i = 1; i <= 10; i++) {
    suma += i		
  }
	
  console.log(suma / 10);
}
 
calculaSuma(); // 45
// Olvidé hacer suma igual a 0
calculaPromedio(); // 11 ???
```

La mejor recomendación es reducir al mínimo la declaración de variables globales, por ejemplo, bibliotecas y frameworks como jQuery o Angular JS exponen su funcionalidad a través de un único objeto ($ y angular respectivamente).

Todos las variables declaradas a nivel global también son expuestas mediante el objeto global, que es el primer valor asignado a la palabra reservada this. En los navegadores este objeto global también está asignado a la variable window. Por lo tanto hay dos formas de declarar variables con scope global, usando la palabra reservada var, o asignándolas como propiedades del objeto global:

```
var miVariable = 123;
console.log(this.miVariable); // 123
this.miVariable = 456;
console.log(miVariable); // 456
 
window.foo = 123;
console.log(foo); // 123
console.log(this.foo); // 123
```

### Scope Local
Este tipo de scope aplica para las variables declaradas dentro de una función y serán accesibles durante toda la ejecución de dicha función. A continuación refactorizamos el código del primer ejemplo para usar solo variables locales y obtener los resultados correctos:

```
function calculaSumaLocal() {
  var suma = 0;
  for (var i = 1; i <= 10; i++) {
    suma += i;		
  }
	
  console.log(suma);
}
 
function calculaPromedioLocal() {
  var suma = 0;
  for (var i = 1; i <= 10; i++) {
    suma += i		
  }
	
  console.log(suma / 10);
}
 
calculaSumaLocal(); // 55
calculaPromedioLocal(); // 5.5
```

En un programa de JavaScript solo hay una cosa más problemática que una variable global, y esa es una variable global que pensábamos que era local. Esto ocurre cuando declaramos una variable local pero olvidamos la palabra reservada var, en vez de que haya un error de variable no declarada como en otros lenguajes, esa variable se convierte en global sin darnos cuenta.

```
function mostrarMensaje() {
  mensaje = "Hola Mundo"; // Variable global
  console.log(mensaje);
}
 
mostrarMensaje();
```

Conocer los tipos de scope y sus reglas nos permitirá detectar errores de una manera más efectiva, de forma resumida podemos decir que una variable declarada dentro de una función es local, en caso contrario es global, y debemos preferir las variables locales sobre las globales.


## El problema de usar var
Las  declaraciones de variables con var, donde sea que ocurran, son procesadas antes de que cualquier otro código sea ejecutado. Entonces declarar una variable en cualquier parte del código es equivalente a declararla al inicio del mismo. 

__Efecto de elevacion__
```
var name = "jose";
function hola() {
 alert(name)
}
// jose


var name = "jose";
function hola() {
 alert(name)
 var name ="pepe";
}

hola();
// undefined

```
Javascript lo interpreta asi.
```
var name = "jose";
function hola() {
 alert(name)
}
// jose


var name = "jose";
function hola() {
 var name;
 alert(name)
 name ="pepe";
}

hola();
// undefined
```


## let al rescate
let permite declarar variables limitando su alcance (scope) al bloque, declaración, o expresión donde se está usando. Lo anterior diferencia  let de la palabra reservada var , la cual define una variable global o local en una función sin importar el ámbito del bloque. let a diferencia de var no eleva las variables y respeta el contexto de la declaracion en bloque.
```
function varTest() {
  var x = 31;
  if (true) {
    var x = 71;  // ¡misma variable!
    console.log(x);  // 71
  }
  console.log(x);  // 71
}

function letTest() {
  let x = 31;
  if (true) {
    let x = 71;  // variable diferente
    console.log(x);  // 71
  }
  console.log(x);  // 31
}

if (x > y) {
  let gamma = 12.7 + y;
  i = gamma * x;
}
```

En el nivel superior de un programa y funciones, let , a diferencia de var, no crea una propiedad en el objeto global, por ejemplo:

```
var x = 'global';
let y = 'global';
console.log(this.x); // "global"
console.log(this.y); // undefined
```

## Uso de const
Las variables constantes presentan un ámbito de bloque (block scope) tal y como lo hacen las variables definidas usando la instrucción let, con la particularidad de que el valor de una constante no puede cambiarse a través de la reasignación. Las constantes no se pueden redeclarar.

Utilizamos const cuando queremos que un valor no cambie en el tiempo.
```
const a = 7;
document.writeln("a es " + a + ".");

```


## Enlaces de interes 
* [var](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Sentencias/var)
* [let](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Sentencias/let)
* [const](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Sentencias/const)

