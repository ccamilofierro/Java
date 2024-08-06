# Declaración, Inicialización y Recorrido de Arrays en Java

## Introducción

Un array (o arreglo) en Java es una estructura de datos que permite almacenar una colección de elementos del mismo tipo. Los arrays en Java son objetos que contienen una secuencia de elementos, y cada elemento puede ser accedido mediante un índice. 

## Declaración de Arrays

La declaración de un array en Java consiste en especificar el tipo de datos que el array va a contener y el nombre del array.

### Ejemplo de Declaración
```java
// Declaración de un array de enteros
int[] numeros;

// Declaración de un array de cadenas
String[] nombres;
```

## Inicialización de Arrays

Después de declarar un array, debes inicializarlo para asignar memoria y establecer su tamaño. La inicialización se realiza usando el operador `new`, seguido del tipo de datos y el tamaño del array.

### Ejemplo de Inicialización
```java
// Inicialización de un array de enteros con 5 elementos
int[] numeros = new int[5];

// Inicialización de un array de cadenas con valores
String[] nombres = {"Ana", "Luis", "Carlos", "Marta"};
```

## Asignación de Valores a Arrays

Puedes asignar valores a los elementos de un array utilizando su índice. Los índices en los arrays comienzan en 0.

### Ejemplo de Asignación de Valores
```java
// Inicialización de un array de enteros
int[] numeros = new int[5];

// Asignación de valores a los elementos del array
numeros[0] = 10;
numeros[1] = 20;
numeros[2] = 30;
numeros[3] = 40;
numeros[4] = 50;

// Inicialización y asignación de valores en una sola línea
String[] nombres = {"Ana", "Luis", "Carlos", "Marta"};
```

## Recorrido de Arrays

Para recorrer un array y acceder a sus elementos, puedes usar un bucle `for`, `for-each`, o `while`.

### Ejemplo de Recorrido con Bucle `for`
```java
int[] numeros = {10, 20, 30, 40, 50};

for (int i = 0; i < numeros.length; i++) {
    System.out.println("Elemento en el índice " + i + ": " + numeros[i]);
}
```

### Ejemplo de Recorrido con Bucle `for-each`
```java
String[] nombres = {"Ana", "Luis", "Carlos", "Marta"};

for (String nombre : nombres) {
    System.out.println("Nombre: " + nombre);
}
```

### Ejemplo de Recorrido con Bucle `while`
```java
int[] numeros = {10, 20, 30, 40, 50};
int i = 0;

while (i < numeros.length) {
    System.out.println("Elemento en el índice " + i + ": " + numeros[i]);
    i++;
}
```

## Consideraciones

- **Índices**: Los índices en un array comienzan en 0 y terminan en `length - 1`.
- **Longitud**: Puedes obtener la longitud de un array usando la propiedad `length` (no es un método).
- **Arrays Multidimensionales**: Los arrays en Java pueden ser multidimensionales, como matrices (arrays de arrays). La declaración y el acceso a elementos son similares a los arrays unidimensionales, pero con más índices.

### Ejemplo de Array Multidimensional
```java
// Declaración e inicialización de una matriz de enteros
int[][] matriz = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};

// Recorrido de una matriz con bucles anidados
for (int i = 0; i < matriz.length; i++) {
    for (int j = 0; j < matriz[i].length; j++) {
        System.out.print(matriz[i][j] + " ");
    }
    System.out.println();
}
```

Los arrays son una estructura de datos fundamental en Java, proporcionando un medio eficiente para almacenar y manipular conjuntos de datos del mismo tipo.
