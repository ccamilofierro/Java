# Buffered Streams (`BufferedReader`, `BufferedWriter`) en Java

## Introducción

En Java, los buffered streams son una mejora sobre los streams básicos, ya que proporcionan un buffer de memoria para almacenar temporalmente los datos antes de realizar operaciones de entrada/salida. Esto puede mejorar significativamente el rendimiento al leer o escribir datos, especialmente cuando se trata de archivos grandes o de operaciones de entrada/salida frecuentes. Las clases `BufferedReader` y `BufferedWriter` se utilizan para leer y escribir texto de manera eficiente mediante el uso de buffers.

## Clase `BufferedReader`

La clase `BufferedReader` se utiliza para leer texto de manera eficiente al agregar un buffer a un flujo de entrada. Esto permite leer grandes bloques de texto en lugar de hacerlo carácter por carácter, lo que mejora el rendimiento.

### Ejemplo de Uso de `BufferedReader`

```java
import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;

public class EjemploBufferedReader {
    public static void main(String[] args) {
        try (BufferedReader lector = new BufferedReader(new FileReader("archivo.txt"))) {
            String linea;
            // Leer líneas del archivo de texto
            while ((linea = lector.readLine()) != null) {
                System.out.println(linea);
            }
        } catch (IOException e) {
            System.out.println("Error al leer el archivo: " + e.getMessage());
        }
    }
}
```

### Métodos Comunes de `BufferedReader`

- `read()`: Lee el siguiente carácter del flujo de entrada.
- `readLine()`: Lee una línea de texto del flujo de entrada.
- `close()`: Cierra el `BufferedReader` y libera los recursos asociados.

## Clase `BufferedWriter`

La clase `BufferedWriter` se utiliza para escribir texto de manera eficiente al agregar un buffer a un flujo de salida. Esto permite escribir grandes bloques de texto en lugar de hacerlo carácter por carácter, lo que mejora el rendimiento.

### Ejemplo de Uso de `BufferedWriter`

```java
import java.io.BufferedWriter;
import java.io.FileWriter;
import java.io.IOException;

public class EjemploBufferedWriter {
    public static void main(String[] args) {
        try (BufferedWriter escritor = new BufferedWriter(new FileWriter("archivo.txt"))) {
            escritor.write("Hola Mundo");
            escritor.newLine();
            escritor.write("Este es un ejemplo de BufferedWriter.");
        } catch (IOException e) {
            System.out.println("Error al escribir en el archivo: " + e.getMessage());
        }
    }
}
```

### Métodos Comunes de `BufferedWriter`

- `write(String str)`: Escribe una cadena de texto en el flujo de salida.
- `newLine()`: Escribe una nueva línea en el flujo de salida.
- `flush()`: Vacía el buffer de salida, asegurando que todos los datos se escriban en el flujo de salida.
- `close()`: Cierra el `BufferedWriter` y libera los recursos asociados.

## Ventajas de Usar Buffered Streams

- **Mejora del Rendimiento**: Al usar buffers, se reducen el número de operaciones de entrada/salida, lo que mejora el rendimiento.
- **Lectura y Escritura Eficiente**: Permite manejar grandes cantidades de datos de manera más eficiente al realizar operaciones en bloques en lugar de caracteres individuales.
- **Conveniencia**: `BufferedReader` y `BufferedWriter` proporcionan métodos convenientes para leer líneas completas y escribir texto formateado.

## Conclusión

Las clases `BufferedReader` y `BufferedWriter` en Java proporcionan una forma eficiente de leer y escribir texto mediante el uso de buffers. Estas clases mejoran el rendimiento al manejar grandes cantidades de datos y proporcionan métodos convenientes para trabajar con texto. Comprender cómo utilizar estas clases es esencial para realizar operaciones de entrada/salida de manera eficiente en aplicaciones Java.
