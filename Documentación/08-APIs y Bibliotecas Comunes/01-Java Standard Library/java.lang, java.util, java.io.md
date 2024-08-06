# Paquetes `java.lang`, `java.util`, `java.io` en Java

## Introducción

Java proporciona una rica biblioteca de clases y paquetes que facilitan el desarrollo de aplicaciones. Entre estos, los paquetes `java.lang`, `java.util` y `java.io` son fundamentales y ofrecen una amplia gama de clases y funcionalidades.

## `java.lang`

El paquete `java.lang` contiene clases fundamentales que son esenciales para el desarrollo de cualquier aplicación Java. Estas clases están disponibles automáticamente en todos los programas Java y no necesitan ser importadas explícitamente.

### Clases Importantes en `java.lang`

- **`Object`**: La clase base de todas las clases en Java. Proporciona métodos fundamentales como `toString()`, `equals()`, `hashCode()`, etc.
- **`String`**: Representa cadenas de caracteres. Proporciona métodos para manipular y operar con cadenas de texto.
- **`Math`**: Proporciona métodos estáticos para realizar operaciones matemáticas básicas, como cálculos de trigonometría, exponenciación, etc.
- **`System`**: Contiene métodos y variables de clase para el acceso a recursos del sistema, como la entrada/salida y las propiedades del sistema.

### Ejemplo de Uso de `java.lang`

```java
public class EjemploLang {
    public static void main(String[] args) {
        String mensaje = "Hola Mundo";
        System.out.println(mensaje.toUpperCase()); // Imprime HOLA MUNDO
    }
}
```

## `java.util`

El paquete `java.util` proporciona una colección de clases y utilidades que son útiles para trabajar con datos y estructuras de datos más complejas.

### Clases Importantes en `java.util`

- **`ArrayList`**: Una implementación de lista dinámica que permite almacenar y manipular colecciones de objetos.
- **`HashMap`**: Una implementación de mapa que permite almacenar pares clave-valor con acceso rápido.
- **`Date`**: Representa fechas y horas. Aunque ha sido reemplazada en gran parte por la nueva API de fechas en `java.time`, sigue siendo útil para algunas operaciones.
- **`Collections`**: Una clase de utilidades que proporciona métodos estáticos para trabajar con colecciones, como ordenación y búsqueda.

### Ejemplo de Uso de `java.util`

```java
import java.util.ArrayList;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

public class EjemploUtil {
    public static void main(String[] args) {
        List<String> lista = new ArrayList<>();
        lista.add("Ana");
        lista.add("Luis");

        Map<String, Integer> mapa = new HashMap<>();
        mapa.put("Ana", 25);
        mapa.put("Luis", 30);

        System.out.println(lista); // Imprime [Ana, Luis]
        System.out.println(mapa); // Imprime {Ana=25, Luis=30}
    }
}
```

## `java.io`

El paquete `java.io` proporciona clases para la manipulación de entrada y salida (I/O) de datos. Esto incluye operaciones de lectura y escritura de archivos, así como la manipulación de flujos de datos.

### Clases Importantes en `java.io`

- **`File`**: Representa un archivo o directorio en el sistema de archivos. Proporciona métodos para crear, eliminar, y obtener información sobre archivos y directorios.
- **`FileReader`**: Permite la lectura de caracteres desde un archivo.
- **`FileWriter`**: Permite la escritura de caracteres en un archivo.
- **`BufferedReader`**: Proporciona una forma eficiente de leer caracteres de un flujo de entrada, mejorando el rendimiento mediante buffering.
- **`BufferedWriter`**: Proporciona una forma eficiente de escribir caracteres en un flujo de salida mediante buffering.

### Ejemplo de Uso de `java.io`

```java
import java.io.File;
import java.io.FileWriter;
import java.io.IOException;

public class EjemploIO {
    public static void main(String[] args) {
        File archivo = new File("ejemplo.txt");

        try (FileWriter escritor = new FileWriter(archivo)) {
            escritor.write("Hola Mundo");
            System.out.println("Archivo escrito exitosamente.");
        } catch (IOException e) {
            System.err.println("Error al escribir el archivo: " + e.getMessage());
        }
    }
}
```

## Conclusión

Los paquetes `java.lang`, `java.util` y `java.io` proporcionan las bases para la mayoría de las operaciones fundamentales en Java. Desde la manipulación de datos básicos y estructuras de datos hasta la gestión de entrada/salida, estas bibliotecas son esenciales para el desarrollo de aplicaciones en Java.
