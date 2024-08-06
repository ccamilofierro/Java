# Bucles en Java

## Bucle `for`
El bucle `for` se utiliza para ejecutar un bloque de código un número específico de veces. Es ideal cuando conoces el número exacto de iteraciones.

### Sintaxis
```java
for (inicialización; condición; actualización) {
    // Código a ejecutar en cada iteración
}
```

### Ejemplo
```java
for (int i = 0; i < 5; i++) {
    System.out.println("Iteración: " + i);
}
```

En este ejemplo, el bucle `for` comienza con `i` igual a 0. Mientras que `i` sea menor que 5, el código dentro del bucle se ejecutará. Después de cada iteración, `i` se incrementa en 1.

## Bucle `while`
El bucle `while` se utiliza para ejecutar un bloque de código mientras se cumpla una condición específica. Es adecuado cuando no sabes cuántas veces se debe ejecutar el bucle.

### Sintaxis
```java
while (condición) {
    // Código a ejecutar mientras la condición sea verdadera
}
```

### Ejemplo
```java
int i = 0;
while (i < 5) {
    System.out.println("Iteración: " + i);
    i++;
}
```

En este ejemplo, el bucle `while` continuará ejecutándose mientras `i` sea menor que 5. Después de cada iteración, `i` se incrementa en 1.

## Bucle `do-while`
El bucle `do-while` es similar al bucle `while`, pero garantiza que el bloque de código se ejecute al menos una vez antes de verificar la condición.

### Sintaxis
```java
do {
    // Código a ejecutar al menos una vez y mientras la condición sea verdadera
} while (condición);
```

### Ejemplo
```java
int i = 0;
do {
    System.out.println("Iteración: " + i);
    i++;
} while (i < 5);
```

En este ejemplo, el bucle `do-while` ejecuta el bloque de código al menos una vez antes de comprobar si `i` es menor que 5. Después de cada iteración, `i` se incrementa en 1.

Estos bucles te permiten controlar la repetición de bloques de código y son fundamentales para realizar tareas repetitivas de manera eficiente en Java.