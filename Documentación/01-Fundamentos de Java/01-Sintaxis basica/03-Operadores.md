# Operadores en Java

## Operadores Aritméticos
Los operadores aritméticos se utilizan para realizar operaciones matemáticas básicas. Estos operadores permiten realizar suma, resta, multiplicación, división y módulo.

- **+**: Suma. Suma dos operandos.
- **-**: Resta. Resta el segundo operando del primero.
- **\***: Multiplicación. Multiplica dos operandos.
- **/**: División. Divide el primer operando entre el segundo.
- **%**: Módulo. Retorna el residuo de la división del primer operando entre el segundo.

### Ejemplo
```java
int a = 10;
int b = 3;

int suma = a + b; // 13
int resta = a - b; // 7
int multiplicacion = a * b; // 30
int division = a / b; // 3
int modulo = a % b; // 1
```

## Operadores Lógicos
Los operadores lógicos se utilizan para combinar varias expresiones booleanas y retornar un resultado booleano. Son útiles para controlar el flujo del programa basado en condiciones.

- **&&**: AND lógico. Retorna `true` si ambos operandos son `true`.
- **||**: OR lógico. Retorna `true` si al menos uno de los operandos es `true`.
- **!**: NOT lógico. Retorna `true` si el operando es `false`, y viceversa.

### Ejemplo
```java
boolean x = true;
boolean y = false;

boolean and = x && y; // false
boolean or = x || y; // true
boolean not = !x; // false
```

## Operadores Relacionales
Los operadores relacionales se utilizan para comparar dos valores. Estos operadores retornan un valor booleano (`true` o `false`) dependiendo de la relación entre los valores.

- **==**: Igual a. Retorna `true` si ambos operandos son iguales.
- **!=**: Diferente de. Retorna `true` si los operandos no son iguales.
- **>**: Mayor que. Retorna `true` si el primer operando es mayor que el segundo.
- **<**: Menor que. Retorna `true` si el primer operando es menor que el segundo.
- **>=**: Mayor o igual que. Retorna `true` si el primer operando es mayor o igual que el segundo.
- **<=**: Menor o igual que. Retorna `true` si el primer operando es menor o igual que el segundo.

### Ejemplo
```java
int x = 10;
int y = 20;

boolean igual = x == y; // false
boolean diferente = x != y; // true
boolean mayor = x > y; // false
boolean menor = x < y; // true
boolean mayorOigual = x >= y; // false
boolean menorOigual = x <= y; // true