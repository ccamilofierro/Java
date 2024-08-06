# Tipos de Datos Primitivos
Java tiene ocho tipos de datos primitivos que se utilizan para almacenar valores simples y no son objetos. Estos tipos de datos son los bloques de construcción fundamentales para la manipulación de datos en Java.

## int
El tipo `int` se utiliza para almacenar números enteros.

- Tamaño: 32 bits
- Rango: -2^31 a 2^31-1

```java
int edad = 25;
int numeroDeDias = 365;
```

## float
El tipo `float` se utiliza para almacenar números de punto flotante de precisión simple.

- Tamaño: 32 bits
- Rango: Aproximadamente ±3.40282347E+38F (6-7 dígitos decimales de precisión)

```java
float temperatura = 36.6f;
float precio = 19.99f;
```

## boolean
El tipo `boolean` se utiliza para almacenar valores lógicos, que pueden ser `true` o `false`.

- Tamaño: 1 bit (aunque la especificación no define el tamaño exacto)

```java
boolean esMayorDeEdad = true;
boolean tienePermiso = false;
```

## char
El tipo `char` se utiliza para almacenar un solo carácter Unicode.

- Tamaño: 16 bits
- Rango: '\u0000' (o 0) a '\uffff' (o 65,535)

```java
char inicial = 'J';
char simbolo = '$';
```

### Ejemplo de Uso de Tipos de Datos Primitivos
Aquí hay un ejemplo que muestra cómo declarar y utilizar diferentes tipos de datos primitivos en una clase Java:

```java
public class TiposPrimitivos {
    public static void main(String[] args) {
        int edad = 25;
        float temperatura = 36.6f;
        boolean esMayorDeEdad = true;
        char inicial = 'J';

        System.out.println("Edad: " + edad);
        System.out.println("Temperatura: " + temperatura);
        System.out.println("Es mayor de edad: " + esMayorDeEdad);
        System.out.println("Inicial: " + inicial);
    }
}
```

En este ejemplo, se declaran y utilizan variables de los tipos `int`, `float`, `boolean`, y `char` para almacenar y mostrar diferentes tipos de datos.

Con estos conceptos sobre los tipos de datos primitivos, puedes comenzar a manejar datos simples en tus programas Java de manera eficiente.
