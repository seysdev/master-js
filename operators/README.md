# Operadores

Los operadores permiten manipular el valor de las variables, realizar operaciones matemáticas con sus valores y comparar diferentes variables. De esta forma, los operadores permiten a los programas realizar cálculos complejos y tomar decisiones lógicas en función de comparaciones y otros tipos de condiciones.

## Operadores de Asignacion

### Asignacion 

Los operadores de asignacion sirven para asignar un valor a una variable.

| Operador abreviado  | Significado |
| ------------- | ------------- |
| x = y  | x = y  |

### Adicion o suma

Para realizar sumas.
| Operador abreviado  | Significado |
| ------------- | ------------- |
| x += y  | x = x + y  |

### Sustraccion o resta

Para realizar restas.
| Operador abreviado  | Significado |
| ------------- | ------------- |
| x -= y  | x = x - y  |

### Multiplicacion

Para realizar multiplicacion.
| Operador abreviado  | Significado |
| ------------- | ------------- |
| x *= y | x = x * y |

### Division

Para realizar divisiones.
| Operador abreviado | Significado |
| ------------- | ------------- |
| x /= y | x = x / y |

### Resto

Para obtener el resto de una division.

| Operador abreviado  | Significado |
| ------------- | ------------- |
| x %= y | x = x % y |

### Exponenciacion o Potencia

Para obtener la potencia.
| Operador abreviado  | Significado |
| ------------- | ------------- |
| x **= y | x = x ** y  |

### Incremento

Valido solo para valores numericos e incrementa los valores uno a uno.

| Operador abreviado  | Significado |
| ------------- | ------------- |
| ++numero | numero + 1 |

### Decremento

Valido solo para valores numericos y decrementa los valores uno a uno.

| Operador abreviado  | Significado |
| ------------- | ------------- |
| --numero | numero - 1 |

## Operadores de comparación

Un operador de comparación compara sus operandos y devuelve un valor lógico en función de si la comparación es verdadera (true) o falsa (false). 
| Operador  | Descripción | Ejemplos |
| ------------- | ------------- | ------------- |
| Igualdad (==) | Devuelve true si ambos operandos son iguales.  | 3 == "3" |
| Desigualdad (!=) | Devuelve true si ambos operandos no son iguales.  | 3 != 4 |
| Estrictamente iguales (===) | Devuelve true si los operandos son iguales y tienen el mismo tipo.  | 3 === "3"; 3 === 3 |
| Estrictamente desiguales (!==) | Devuelve true si los operandos no son iguales y/o no son del mismo tipo.  | 3 !== 3; 3 !== "3" |
| Mayor que (>) | Devuelve true si el operando de la izquierda es mayor que el operando de la derecha.  | 3 > 2 |
| Mayor o igual que (>=) | Devuelve true si el operando de la izquierda es mayor o igual que el operando de la derecha. | 3>=3 |
| Menor que (<) | Devuelve true si el operando de la izquierda es menor que el operando de la derecha.  | 2<3 |
| Menor o igual que (<=) | Devuelve true si el operando de la izquierda es menor o igual que el operando de la derecha.  | 2<=2 |

## Operadores Logicos

| Operador  | Uso | Descripción |
| ------------- | ------------- | ------------- |
| AND (&&) | expr1 && expr2 | Devuelve true si ambos valores son true, en caso contrario devuelve false |
| OR (\|\|) | expr1 \|\| expr2 | devuelve true si alguno de los operandos es true, o false si ambos son false. |
| NOT (!) | !expr | Le cambia el valor de true a false o de false a true |

## Enlaces de interes
[Operadores de comparacion](https://developer.mozilla.org/es/docs/Web/JavaScript/Guide/Expressions_and_Operators#Operadores_de_comparaci%C3%B3n)