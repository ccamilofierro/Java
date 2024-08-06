# Streams (`InputStream`, `OutputStream`) en Java

## Introducción

En Java, los streams son una forma fundamental de realizar operaciones de entrada y salida de datos. Las clases `InputStream` y `OutputStream` son las clases base para la lectura y escritura de datos en forma de bytes, respectivamente. Estos streams son útiles para manejar datos binarios y trabajar con archivos, redes, y otros tipos de entradas y salidas de datos.

## Clase `InputStream`

La clase `InputStream` es una clase abstracta que proporciona métodos para leer datos de un flujo de entrada. Las clases que extienden `InputStream` implementan la funcionalidad específica para leer datos de diversas fuentes, como archivos o redes.

### Ejemplo de Uso de `InputStream`

```java
import java.io.FileInputStream;
import java.io.IOException;
import java.io.InputStream;

public class EjemploInputStream {
    public static void main(String[] args) {
        try (InputStream entrada = new FileInputStream("archivo.bin")) {
            int dato;
            // Leer datos del flujo de entrada byte por byte
            while ((dato = entrada.read()) != -1) {
                System.out.print((char) dato);
            }
        } catch (IOException e) {
            System.out.println("Error al leer el archivo: " + e.getMessage());
        }
    }
}
```

### Métodos Comunes de `InputStream`

- `read()`: Lee el siguiente byte de datos del flujo de entrada. Devuelve -1 si se llega al final del flujo.
- `read(byte[] buffer)`: Lee bytes del flujo de entrada en un array de bytes.
- `skip(long n)`: Salta un número específico de bytes en el flujo de entrada.
- `close()`: Cierra el flujo de entrada y libera los recursos asociados.

## Clase `OutputStream`

La clase `OutputStream` es una clase abstracta que proporciona métodos para escribir datos en un flujo de salida. Las clases que extienden `OutputStream` implementan la funcionalidad específica para escribir datos en diversas salidas, como archivos o redes.

### Ejemplo de Uso de `OutputStream`

```java
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.OutputStream;

public class EjemploOutputStream {
    public static void main(String[] args) {
        try (OutputStream salida = new FileOutputStream("archivo.bin")) {
            String datos = "Hola Mundo";
            // Escribir datos en el flujo de salida byte por byte
            for (byte b : datos.getBytes()) {
                salida.write(b);
            }
        } catch (IOException e) {
            System.out.println("Error al escribir en el archivo: " + e.getMessage());
        }
    }
}
```

### Métodos Comunes de `OutputStream`

- `write(int b)`: Escribe un solo byte de datos en el flujo de salida.
- `write(byte[] buffer)`: Escribe un array de bytes en el flujo de salida.
- `flush()`: Vacía el buffer de salida, asegurando que todos los datos se escriban en el flujo de salida.
- `close()`: Cierra el flujo de salida y libera los recursos asociados.

## Diferencias entre `InputStream` y `OutputStream`

- **Dirección de los Datos**: `InputStream` se utiliza para leer datos (entrada), mientras que `OutputStream` se utiliza para escribir datos (salida).
- **Métodos de Operación**: Aunque ambos proporcionan métodos para leer y escribir bytes, `InputStream` está orientado a la lectura y `OutputStream` a la escritura.
- **Uso en Archivos y Redes**: Ambas clases se utilizan para trabajar con archivos y otros flujos de datos, pero su funcionalidad específica varía según si se está leyendo o escribiendo datos.

## Conclusión

Las clases `InputStream` y `OutputStream` en Java son fundamentales para el manejo de datos en forma de bytes. `InputStream` proporciona métodos para leer datos de un flujo de entrada, mientras que `OutputStream` permite escribir datos en un flujo de salida. Comprender cómo utilizar estas clases es esencial para trabajar con datos binarios y realizar operaciones de entrada/salida en aplicaciones Java.
