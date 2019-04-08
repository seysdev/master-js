# Loops

Los bucles ofrecen una manera rápida y sencilla de hacer algo repetidamente.

Las sentencias para bucles disponibles en JavaScript son:

* sentencia for
* sentencia do...while
* sentencia while
* sentencia break
* sentencia continue
* sentencia for...in
* sentencia for...of

## for

Un bucle for se repite hasta que la condición especificada se evalúa como false. El bucle for en JavaScript es similar al de Java y C. Una sentencia for se muestra como sigue:

```javascript
for ([expresionInicial]; [condicion]; [expresionIncremento])
  sentencia

for (let i = 0; i < 10; i++) {
    console.log('i', i);
}  
```

## do while

La sentencia do...while se repite hasta que la condición especificada que se evalúa sea false. El loop do while iterara al menos una vez luego de evaluar la sentencia.

```javascript
do
  sentencia
while (condicion);

do {
  i += 1;
  console.log(i);
} while (i < 5);
```

## while
Una sentencia while ejecuta sus sentencias mientras la condición sea evaluada como verdadera. Una sentencia while tiene el siguiente aspecto:

```javascript
while (condicion)
  sentencia

n = 0;
x = 0;
while (n < 3) {
  n++;
  x += n;
}
```

## break

Use la sentencia break para salir de un bucle, o switch.

```javascript
for (let i = 0; i < 10; i++) {
  if (i === 3) {

  }
}
```

## continue

La sentencia continue puede usarse para reiniciar una sentencia while, do-while, for, la sentencia continue salta al siguiente ciclo.

```javascript
let text = '';
for (let i = 0; i < 10; i++) {
  if (i === 3) { continue; }
  text += "The number is " + i + "<br>";
}
```

## for in

La sentencia for...in itera una variable especificada sobre todas las propiedades enumerables de un objeto. 

```javascript
for (variable in objeto) {
  sentencias
}

let car = {
    model: 'camaro',
    year: 1980
}
for (let i in car) {
  console.log(i, car[i]);
}
```

## for of

La sentencia for...of itera sobre los valores de las propiedades a diferencia de for in que lo hace sobre las propiedades.

```javascript
for (variable of objeto) {
  sentencia
}

let arr = [3, 5, 7];

for (let i in arr) {
   console.log(i); // logs "0", "1", "2", "foo"
}

for (let i of arr) {
   console.log(i); // logs "3", "5", "7"
}
```

## Enlaces de interes

* [loops](https://developer.mozilla.org/es/docs/Web/JavaScript/Guide/Bucles_e_iteraci%C3%B3n)