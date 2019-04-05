# Control de Flujo
Javascript soporta un conjunto compacto de sentencias, específicamente para el manejo de flujo, que puedes usar para incorporar mayor interactividad a tus aplicaciones.

## Sentencias condicionales
Una sentencia condicional es un conjunto de comandos que se ejecutan si una condición es verdadera. JavaScript soporta dos sentencias condicionales: if...else y switch

### if...else
Se utiliza la sentencia if para comprobar si la condición lógica es verdadera. Se utiliza la opción else para ejecutar un sentencia si la condición es falsa.
```
if (condición) {
    sentencia_1;
} else { 
    sentencia_2;
}
```

También puedes componer sentencias más complejas usando else if para tener múltiples condiciones, como se muestra a continuación:
```
if (condición_1) {
  sentencia_1;
} else if (condición_2) {
  sentencia_2;
} else if (condición_n) {
  sentencia_n;
} else {
  ultima_sentencia;
} 
```

### Switch
Una sentencia switch permite a un programa evaluar una expresión e intentar igualar el valor de dicha expresión a una etiqueta de caso (case). Si se encuentra una coincidencia, el programa ejecuta la sentencia asociada. Una sentencia switch se describe como se muestra a continuación:
```
switch (expresión) {
  case etiqueta_1:
    sentencias_1
    [break;]
  case etiqueta_2:
    sentencias_2
    [break;]
    ...
  default:
    sentencias_por_defecto
    [break;]
}
```

### Operador ternario
El operador condicional (ternario) es el único operador en JavaScript que tiene tres operandos. Este operador se usa con frecuencia como atajo para la instrucción if.
```
condición ? expr1 : expr2 

age > 18 ? location.assign("continue.html") : stop = true;

age > 18 ? (
    alert("OK, puedes continuar."),
    location.assign("continue.html")
) : (
    stop = true,
    alert("Disculpa, eres menor de edad!")
);
```


## Sentencias de manejo de excepciones
Puedes lanzar excepciones usando la sentencia throw y manejarlas usando las sentencias try...catch.

### Excepciones con Throw
La forma más sencilla para lanzar errores es utilizando throw. Este comando permite enviar al navegador un evento similar al que se produce cuando ocurre algún imprevisto o nos encontramos ante un tipo inesperado de datos. El lenguaje permite enviar todo tipo de elementos, incluyendo texto, números, valores booleanos o incluso objetos. Sin embargo, la opción más usual es enviar el objeto nativo Error:
```
function mySum(){
  var result = 0,
  l = arguments.length;
  if( l > 10 ) throw console.error( 'Too much arguments!' );
    for( var x = 0; x < l; x++ ){
    result += arguments[x];
  }
  return result;
}
 
console.log( mySum( 3, 4, 34, 5, 7, 8, 1, 32 ) );  // 94
console.log( mySum( 3, 4, 34, 5, 7, 8, 1, 32, 3, 5, 8 ) );  // Error: Too much arguments
// El resto del código, será ignorado tras lanzar la excepción...
// ...
// ...
```

### Excepciones con Try / Catch
Try … Catch corresponde a un tipo de estructura de control Javascript con la que comprobar el flujo de un programa frente a comportamientos inesperados. La diferencia entre esta estructura y la anterior es que mientras throw detiene completamente la ejecución, catch realiza una acción determinada frente a los errores para proseguir después con el flujo definido.
```
function checkPassword( my_string ){
  var msg = {};
  try {
    if( my_string.length < 6 ) throw 'SHORT';
    if( my_string.length > 10 ) throw 'LONG';
    msg.status = 'Pass Validated';
  } catch( err ) {
    if( err == 'SHORT' ) msg.status = 'Pass is too short';
    if( err == 'LONG' ) msg.status = 'Pass is too long';
  } finally {
    console.log( 'Password evaluated: ' + msg.status );
  }
}
 
checkPassword( '1234' ); // Password evaluated: Pass is too short
checkPassword( '12345678901' ); // Password evaluated: Pass is too long
checkPassword( '12345678' ); // Password evaluated: Pass Validated
 
console.log( 'The execution continues here... ' );

```

## Enlaces de interes
* [control de flujo](https://developer.mozilla.org/es/docs/Web/JavaScript/Guide/Control_de_flujo_y_manejo_de_errores)
* [excepciones](http://www.etnassoft.com/2011/01/30/excepciones-en-javascript/)