# Excepciones Checked y Unchecked en Java

## Introducción

En Java, las excepciones se dividen en dos categorías principales: excepciones verificadas (checked) y excepciones no verificadas (unchecked). Cada tipo de excepción tiene un comportamiento y requisitos específicos en cuanto a su manejo. Entender la diferencia entre estas dos categorías es crucial para un manejo adecuado de errores en las aplicaciones Java.

## Excepciones Checked

Las excepciones verificadas son aquellas que el compilador requiere que sean manejadas explícitamente en el código. Estas excepciones suelen ser errores que ocurren debido a problemas externos y son predecibles. Si un método puede lanzar una excepción verificada, debe manejarla utilizando un bloque `try-catch` o declararla usando la palabra clave `throws`.

### Ejemplo de Excepción Checked

Un ejemplo común de una excepción verificada es `IOException`, que puede ocurrir durante la operación de entrada/salida.

```java
import java.io.FileReader;
import java.io.IOException;

public class EjemploCheckedException {
    public static void main(String[] args) {
        try {
            FileReader archivo = new FileReader("archivo.txt");
            int caracter = archivo.read();
            archivo.close();
        } catch (IOException e) {
            System.out.println("Error al leer el archivo: " + e.getMessage());
        }
    }
}
```

### Declaración de Excepciones Checked

Si un método puede lanzar una excepción verificada, debe declarar esta excepción en su firma usando la palabra clave `throws`.

```java
import java.io.FileReader;
import java.io.IOException;

public class EjemploCheckedDeclaration {
    public static void main(String[] args) {
        try {
            leerArchivo("archivo.txt");
        } catch (IOException e) {
            System.out.println("Error al leer el archivo: " + e.getMessage());
        }
    }

    public static void leerArchivo(String nombreArchivo) throws IOException {
        FileReader archivo = new FileReader(nombreArchivo);
        int caracter = archivo.read();
        archivo.close();
    }
}
```

## Excepciones Unchecked

Las excepciones no verificadas son aquellas que el compilador no obliga a manejar. Estas excepciones son generalmente errores de programación que pueden ser evitados mediante el código correcto. Se derivan de la clase `RuntimeException` y no necesitan ser declaradas en la firma del método.

### Ejemplo de Excepción Unchecked

Un ejemplo común de una excepción no verificada es `ArithmeticException`, que puede ocurrir durante operaciones matemáticas incorrectas, como la división por cero.

```java
public class EjemploUncheckedException {
    public static void main(String[] args) {
        try {
            int resultado = 10 / 0; // Esto lanzará una excepción ArithmeticException
        } catch (ArithmeticException e) {
            System.out.println("Error: División por cero.");
        }
    }
}
```

## Diferencias Clave

- **Manejo de Excepciones**: Las excepciones verificadas deben ser manejadas explícitamente, ya sea con un bloque `try-catch` o declarando la excepción en la firma del método. Las excepciones no verificadas no requieren manejo explícito.
- **Origen**: Las excepciones verificadas suelen ser errores externos previsibles (como errores de entrada/salida), mientras que las excepciones no verificadas suelen ser errores de programación (como índices fuera de límites o nulidad).
- **Declaración**: Las excepciones verificadas deben ser declaradas en la firma del método con `throws`, mientras que las excepciones no verificadas no requieren esta declaración.

## Conclusión

Comprender la diferencia entre excepciones verificadas y no verificadas es fundamental para un manejo efectivo de errores en Java. Las excepciones verificadas deben ser gestionadas explícitamente, mientras que las excepciones no verificadas son generalmente errores de programación que pueden ser evitados con una lógica de código adecuada. Un manejo correcto de ambas categorías de excepciones contribuye a la robustez y estabilidad de las aplicaciones Java.
