# Declaración y Uso de Métodos en Java

## Declaración de Métodos
Los métodos en Java se utilizan para agrupar un conjunto de instrucciones que realizan una tarea específica. Puedes declarar métodos para organizar y reutilizar código. La declaración de un método incluye su nombre, parámetros (si los hay), tipo de retorno y el cuerpo del método.

### Sintaxis
```java
modificador_de_acceso tipo_de_retorno nombre_del_metodo(parametros) {
    // Código a ejecutar
}
```

### Ejemplo
```java
public int sumar(int a, int b) {
    return a + b;
}
```

En este ejemplo, el método `sumar` toma dos parámetros (`a` y `b`) de tipo `int`, suma estos valores y retorna el resultado.

## Uso de Métodos
Para utilizar un método, simplemente llamas al método desde otra parte del código, proporcionando los argumentos necesarios y capturando el valor retornado (si es aplicable).

### Sintaxis para Llamar a un Método
```java
nombre_del_metodo(argumentos);
```

### Ejemplo
```java
public class Calculadora {
    public int sumar(int a, int b) {
        return a + b;
    }
    
    public static void main(String[] args) {
        Calculadora calc = new Calculadora();
        int resultado = calc.sumar(5, 3);
        System.out.println("El resultado de la suma es: " + resultado);
    }
}
```

En este ejemplo, creamos una instancia de la clase `Calculadora` y llamamos al método `sumar` con los argumentos `5` y `3`. El resultado se almacena en la variable `resultado` y se imprime en la consola.

## Métodos sin Retorno
Si un método no necesita retornar un valor, se declara con el tipo de retorno `void`.

### Ejemplo
```java
public void imprimirMensaje(String mensaje) {
    System.out.println(mensaje);
}

public static void main(String[] args) {
    imprimirMensaje("Hola, Mundo!");
}
```

En este caso, el método `imprimirMensaje` recibe un parámetro `mensaje` de tipo `String` y simplemente imprime ese mensaje en la consola. No retorna ningún valor.

## Sobrecarga de Métodos
Java permite la sobrecarga de métodos, lo que significa que puedes tener varios métodos con el mismo nombre pero con diferentes listas de parámetros.

### Ejemplo
```java
public class EjemploSobrecarga {
    public void mostrar(int a) {
        System.out.println("Número entero: " + a);
    }
    
    public void mostrar(String mensaje) {
        System.out.println("Mensaje: " + mensaje);
    }
    
    public static void main(String[] args) {
        EjemploSobrecarga obj = new EjemploSobrecarga();
        obj.mostrar(10);
        obj.mostrar("Hola");
    }
}
```

En este ejemplo, el método `mostrar` está sobrecargado para aceptar diferentes tipos de parámetros (`int` y `String`).

Estos conceptos básicos de métodos te permiten modularizar y organizar tu código en Java, facilitando la reutilización y mantenimiento del mismo.
