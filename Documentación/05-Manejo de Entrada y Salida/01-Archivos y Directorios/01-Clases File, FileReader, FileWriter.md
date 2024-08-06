# Clases `File`, `FileReader`, `FileWriter` en Java

## Introducción

En Java, las clases `File`, `FileReader`, y `FileWriter` son parte del paquete `java.io` y se utilizan para realizar operaciones de entrada/salida de archivos. Estas clases proporcionan métodos para crear, leer, escribir y manipular archivos en el sistema de archivos.

## Clase `File`

La clase `File` se utiliza para representar archivos y directorios en el sistema de archivos. Proporciona métodos para crear, eliminar, y consultar la existencia de archivos y directorios, así como para obtener información sobre ellos.

### Ejemplo de Uso de `File`

```java
import java.io.File;
import java.io.IOException;

public class EjemploFile {
    public static void main(String[] args) {
        // Crear un objeto File que representa un archivo
        File archivo = new File("archivo.txt");

        // Verificar si el archivo existe
        if (archivo.exists()) {
            System.out.println("El archivo existe.");
        } else {
            System.out.println("El archivo no existe.");
            try {
                // Crear el archivo si no existe
                boolean creado = archivo.createNewFile();
                if (creado) {
                    System.out.println("Archivo creado con éxito.");
                } else {
                    System.out.println("No se pudo crear el archivo.");
                }
            } catch (IOException e) {
                System.out.println("Error al crear el archivo: " + e.getMessage());
            }
        }
    }
}
```

### Métodos Comunes de `File`

- `exists()`: Verifica si el archivo o directorio existe.
- `createNewFile()`: Crea un nuevo archivo vacío.
- `delete()`: Elimina el archivo o directorio.
- `length()`: Obtiene el tamaño del archivo en bytes.
- `isDirectory()`: Verifica si el objeto `File` es un directorio.

## Clase `FileReader`

La clase `FileReader` se utiliza para leer datos de un archivo de texto. Proporciona métodos para leer caracteres de un archivo en lugar de bytes, lo que facilita la lectura de datos en formato de texto.

### Ejemplo de Uso de `FileReader`

```java
import java.io.FileReader;
import java.io.IOException;

public class EjemploFileReader {
    public static void main(String[] args) {
        try (FileReader lector = new FileReader("archivo.txt")) {
            int caracter;
            // Leer caracteres del archivo uno por uno
            while ((caracter = lector.read()) != -1) {
                System.out.print((char) caracter);
            }
        } catch (IOException e) {
            System.out.println("Error al leer el archivo: " + e.getMessage());
        }
    }
}
```

### Métodos Comunes de `FileReader`

- `read()`: Lee el siguiente carácter del archivo.
- `read(char[] buffer)`: Lee caracteres del archivo en un buffer.
- `close()`: Cierra el `FileReader` y libera los recursos asociados.

## Clase `FileWriter`

La clase `FileWriter` se utiliza para escribir datos en un archivo de texto. Proporciona métodos para escribir caracteres en un archivo y crear el archivo si no existe.

### Ejemplo de Uso de `FileWriter`

```java
import java.io.FileWriter;
import java.io.IOException;

public class EjemploFileWriter {
    public static void main(String[] args) {
        try (FileWriter escritor = new FileWriter("archivo.txt")) {
            escritor.write("Hola Mundo");
            escritor.write("\nEste es un ejemplo de FileWriter.");
        } catch (IOException e) {
            System.out.println("Error al escribir en el archivo: " + e.getMessage());
        }
    }
}
```

### Métodos Comunes de `FileWriter`

- `write(int c)`: Escribe un solo carácter en el archivo.
- `write(char[] buffer)`: Escribe un array de caracteres en el archivo.
- `write(String str)`: Escribe una cadena de texto en el archivo.
- `flush()`: Vacía el buffer de escritura, asegurando que todos los datos sean escritos en el archivo.
- `close()`: Cierra el `FileWriter` y libera los recursos asociados.

## Conclusión

Las clases `File`, `FileReader`, y `FileWriter` en Java proporcionan una base sólida para la manipulación de archivos en aplicaciones Java. La clase `File` permite representar y manipular archivos y directorios, mientras que `FileReader` y `FileWriter` facilitan la lectura y escritura de datos en archivos de texto, respectivamente. Comprender cómo usar estas clases es esencial para realizar operaciones de entrada/salida en Java de manera efectiva.
