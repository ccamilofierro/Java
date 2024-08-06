# Métodos y Clases Genéricas en Java

## Introducción

En Java, los genéricos permiten crear clases y métodos que pueden operar con diferentes tipos de datos sin necesidad de usar tipos específicos. Esto mejora la reutilización del código y la seguridad de tipo. En esta sección, exploraremos cómo definir y usar métodos y clases genéricas en Java.

## Clases Genéricas

Las clases genéricas son clases que pueden trabajar con diferentes tipos de datos sin necesidad de especificar un tipo concreto al momento de definir la clase. Esto se logra utilizando parámetros de tipo genérico.

### Definición de Clases Genéricas

Para definir una clase genérica, se utiliza un parámetro de tipo entre los signos de menor (`<`) y mayor (`>`). A continuación se muestra un ejemplo:

```java
public class Caja<T> {
    private T contenido;

    // Constructor
    public Caja(T contenido) {
        this.contenido = contenido;
    }

    // Método para poner contenido
    public void ponerContenido(T contenido) {
        this.contenido = contenido;
    }

    // Método para obtener contenido
    public T obtenerContenido() {
        return contenido;
    }
}

public class CajaExample {
    public static void main(String[] args) {
        // Crear una instancia de Caja con tipo String
        Caja<String> cajaDeTexto = new Caja<>("Hola Mundo");
        System.out.println("Contenido de la caja: " + cajaDeTexto.obtenerContenido());

        // Crear una instancia de Caja con tipo Integer
        Caja<Integer> cajaDeNumero = new Caja<>(123);
        System.out.println("Contenido de la caja: " + cajaDeNumero.obtenerContenido());
    }
}
```

## Métodos Genéricos

Los métodos genéricos permiten definir métodos que operan con diferentes tipos de datos sin tener que especificar un tipo concreto. Al igual que con las clases genéricas, se utilizan parámetros de tipo en la definición del método.

### Definición de Métodos Genéricos

Para definir un método genérico, se coloca el parámetro de tipo antes del tipo de retorno del método. Aquí hay un ejemplo de un método genérico que intercambia dos elementos en un arreglo:

```java
public class Utilidades {
    // Método genérico para intercambiar dos elementos en un arreglo
    public static <T> void intercambiar(T[] arreglo, int i, int j) {
        T temp = arreglo[i];
        arreglo[i] = arreglo[j];
        arreglo[j] = temp;
    }
}

public class UtilidadesExample {
    public static void main(String[] args) {
        // Crear un arreglo de Strings
        String[] nombres = {"Ana", "Luis", "Carlos"};

        // Intercambiar elementos en el arreglo
        Utilidades.intercambiar(nombres, 0, 2);

        // Mostrar el arreglo después del intercambio
        for (String nombre : nombres) {
            System.out.println(nombre);
        }

        // Crear un arreglo de Integers
        Integer[] numeros = {1, 2, 3};

        // Intercambiar elementos en el arreglo
        Utilidades.intercambiar(numeros, 0, 2);

        // Mostrar el arreglo después del intercambio
        for (Integer numero : numeros) {
            System.out.println(numero);
        }
    }
}
```

## Ventajas de Usar Genéricos

- **Reutilización del Código**: Los métodos y clases genéricas pueden trabajar con diferentes tipos de datos, evitando la duplicación de código.
- **Seguridad de Tipo**: Permite la verificación de tipos en tiempo de compilación, lo que reduce errores en tiempo de ejecución.
- **Eliminación de Castings**: Reduce la necesidad de conversiones de tipo (casting), lo que simplifica el código y mejora su legibilidad.

## Conclusión

El uso de métodos y clases genéricas en Java proporciona una manera flexible y segura de trabajar con diferentes tipos de datos. Al definir tipos genéricos, se mejora la reutilización del código y se minimizan los errores relacionados con el tipo de datos.
