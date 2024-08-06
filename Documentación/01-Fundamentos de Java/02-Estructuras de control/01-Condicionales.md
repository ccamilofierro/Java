# Condicionales en Java

## Estructura `if`
La estructura `if` permite ejecutar un bloque de código si se cumple una condición específica.

### Sintaxis
```java
if (condición) {
    // Código a ejecutar si la condición es verdadera
}
```

### Ejemplo
```java
int edad = 18;

if (edad >= 18) {
    System.out.println("Eres mayor de edad.");
}
```

## Estructura `else if`
La estructura `else if` se utiliza para especificar una nueva condición si la condición en el `if` inicial no se cumple. Puedes tener múltiples bloques `else if` en una estructura `if`.

### Sintaxis
```java
if (condición1) {
    // Código a ejecutar si la condición1 es verdadera
} else if (condición2) {
    // Código a ejecutar si la condición2 es verdadera
} else {
    // Código a ejecutar si ninguna de las condiciones anteriores es verdadera
}
```

### Ejemplo
```java
int edad = 16;

if (edad >= 18) {
    System.out.println("Eres mayor de edad.");
} else if (edad >= 13) {
    System.out.println("Eres un adolescente.");
} else {
    System.out.println("Eres un niño.");
}
```

## Estructura `switch`
La estructura `switch` permite seleccionar uno de muchos bloques de código a ejecutar basado en el valor de una expresión. Es útil cuando tienes múltiples condiciones que se basan en el valor de una variable.

### Sintaxis
```java
switch (expresión) {
    case valor1:
        // Código a ejecutar si expresión == valor1
        break;
    case valor2:
        // Código a ejecutar si expresión == valor2
        break;
    // Puedes agregar más casos
    default:
        // Código a ejecutar si ninguna de las condiciones anteriores se cumple
}
```

### Ejemplo
```java
int dia = 3; // Representa el día de la semana

switch (dia) {
    case 1:
        System.out.println("Lunes");
        break;
    case 2:
        System.out.println("Martes");
        break;
    case 3:
        System.out.println("Miércoles");
        break;
    case 4:
        System.out.println("Jueves");
        break;
    case 5:
        System.out.println("Viernes");
        break;
    case 6:
        System.out.println("Sábado");
        break;
    case 7:
        System.out.println("Domingo");
        break;
    default:
        System.out.println("Día inválido");
}
```

En este ejemplo, el valor de `dia` se compara con cada `case`. Si hay una coincidencia, se ejecuta el bloque correspondiente y el `break` evita que el flujo continúe a los siguientes `case`. Si no hay coincidencia, se ejecuta el bloque `default`.

Estos constructores condicionales te permiten tomar decisiones y controlar el flujo de tu programa basado en diferentes condiciones.
