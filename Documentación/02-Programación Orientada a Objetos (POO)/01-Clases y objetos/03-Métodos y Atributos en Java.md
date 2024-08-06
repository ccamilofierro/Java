# Métodos y Atributos en Java

## Atributos

### Definición de Atributos
Los atributos (o propiedades) en Java son variables que pertenecen a una clase. Los atributos definen el estado o las características de los objetos de esa clase. 

### Sintaxis para Definir Atributos
```java
public class NombreDeLaClase {
    // Atributos de la clase
    tipo nombreAtributo;
}
```

### Ejemplo de Atributos
```java
public class Coche {
    // Atributos
    String marca;
    String modelo;
    int año;
}
```

En este ejemplo, la clase `Coche` tiene tres atributos: `marca`, `modelo`, y `año`.

### Modificadores de Acceso
Los atributos pueden tener modificadores de acceso que determinan su visibilidad:
- **`private`**: Solo accesible dentro de la clase.
- **`protected`**: Accesible dentro del paquete y por subclases.
- **`public`**: Accesible desde cualquier lugar.
- **Sin modificador**: Accesible solo dentro del mismo paquete.

## Métodos

### Definición de Métodos
Los métodos en Java son bloques de código que realizan una tarea específica. Los métodos definen el comportamiento de los objetos y pueden manipular los atributos de la clase.

### Sintaxis para Definir un Método
```java
public class NombreDeLaClase {
    // Método de la clase
    public tipoDeRetorno nombreDelMetodo(tipo parametro1, tipo parametro2, ...) {
        // Código del método
    }
}
```

### Ejemplo de Métodos
```java
public class Coche {
    String marca;
    String modelo;
    int año;

    // Método para encender el coche
    public void encender() {
        System.out.println("El coche está encendido.");
    }

    // Método para mostrar información del coche
    public void mostrarInformacion() {
        System.out.println("Marca: " + marca + ", Modelo: " + modelo + ", Año: " + año);
    }
}
```

En este ejemplo, la clase `Coche` tiene dos métodos: `encender` y `mostrarInformacion`. El método `encender` no recibe parámetros y no devuelve ningún valor, mientras que `mostrarInformacion` tampoco recibe parámetros y no devuelve ningún valor.

### Modificadores de Acceso
Los métodos también pueden tener modificadores de acceso:
- **`private`**: Solo accesible dentro de la clase.
- **`protected`**: Accesible dentro del paquete y por subclases.
- **`public`**: Accesible desde cualquier lugar.
- **Sin modificador**: Accesible solo dentro del mismo paquete.

### Métodos con Valor de Retorno
Los métodos pueden devolver un valor, lo que permite a los métodos proporcionar información al código que los llama.

#### Ejemplo de Método con Valor de Retorno
```java
public class Calculadora {
    // Método para sumar dos números
    public int sumar(int a, int b) {
        return a + b;
    }
}

public class Main {
    public static void main(String[] args) {
        Calculadora calc = new Calculadora();
        int resultado = calc.sumar(5, 3);
        System.out.println("Resultado de la suma: " + resultado);
    }
}
```

En este ejemplo, el método `sumar` de la clase `Calculadora` devuelve la suma de dos números enteros.

## Métodos Estáticos
Los métodos estáticos pertenecen a la clase en lugar de a las instancias de la clase. Se pueden llamar sin crear un objeto de la clase.

### Ejemplo de Método Estático
```java
public class Utilidades {
    // Método estático para imprimir un mensaje
    public static void imprimirMensaje(String mensaje) {
        System.out.println(mensaje);
    }
}

public class Main {
    public static void main(String[] args) {
        // Llamar al método estático sin crear un objeto de la clase Utilidades
        Utilidades.imprimirMensaje("Hola, mundo!");
    }
}
```

En este ejemplo, el método `imprimirMensaje` es estático y se puede llamar directamente a través de la clase `Utilidades`.

## Consideraciones Adicionales
- **Encapsulamiento**: Se recomienda usar modificadores de acceso para proteger los atributos y proporcionar métodos `getter` y `setter` para acceder y modificar los atributos de manera segura.
- **Documentación**: Utiliza comentarios y documentación para describir el propósito de los métodos y atributos, lo que facilita la comprensión y el mantenimiento del código.

Comprender y utilizar correctamente métodos y atributos es fundamental para diseñar clases efectivas y organizadas en Java.
