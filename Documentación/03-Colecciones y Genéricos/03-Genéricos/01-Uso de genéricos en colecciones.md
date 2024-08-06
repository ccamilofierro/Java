# Uso de Genéricos en Colecciones

## Introducción

En Java, los genéricos permiten crear clases, interfaces y métodos que pueden operar con diferentes tipos de datos sin necesidad de utilizar tipos de datos específicos. Esto proporciona mayor flexibilidad y seguridad de tipo en tiempo de compilación. El uso de genéricos en colecciones asegura que solo se almacenen y manipulen los tipos de datos esperados, reduciendo errores en tiempo de ejecución.

## ¿Qué Son los Genéricos?

Los genéricos son una característica del lenguaje Java que permite definir clases, interfaces y métodos con un tipo de datos que se especifica en el momento de la instancia. En lugar de usar tipos de datos específicos, se utiliza un parámetro de tipo genérico, lo que permite trabajar con diferentes tipos de datos de manera segura y eficiente.

### Ejemplo de Clase Genérica

A continuación, se muestra un ejemplo simple de una clase genérica:

```java
public class Caja<T> {
    private T contenido;

    public void ponerContenido(T contenido) {
        this.contenido = contenido;
    }

    public T obtenerContenido() {
        return contenido;
    }
}

public class CajaExample {
    public static void main(String[] args) {
        Caja<String> cajaDeTexto = new Caja<>();
        cajaDeTexto.ponerContenido("Hola Mundo");
        System.out.println("Contenido de la caja: " + cajaDeTexto.obtenerContenido());

        Caja<Integer> cajaDeNumero = new Caja<>();
        cajaDeNumero.ponerContenido(123);
        System.out.println("Contenido de la caja: " + cajaDeNumero.obtenerContenido());
    }
}
```

## Uso de Genéricos en Colecciones

Las colecciones en Java, como `List`, `Set` y `Map`, se pueden utilizar con genéricos para asegurar que los elementos almacenados sean del tipo esperado. Esto evita errores comunes relacionados con el tipo de datos y proporciona una manera más segura de trabajar con colecciones.

### Ejemplo de Uso de Genéricos en `List`

Aquí hay un ejemplo de cómo se usan los genéricos con la interfaz `List`:

```java
import java.util.ArrayList;
import java.util.List;

public class ListExample {
    public static void main(String[] args) {
        // Crear una lista de Strings usando genéricos
        List<String> listaNombres = new ArrayList<>();

        // Agregar elementos a la lista
        listaNombres.add("Ana");
        listaNombres.add("Luis");
        listaNombres.add("Carlos");

        // Acceder y mostrar elementos
        for (String nombre : listaNombres) {
            System.out.println("Nombre: " + nombre);
        }
    }
}
```

### Ejemplo de Uso de Genéricos en `Set`

Aquí hay un ejemplo de cómo se usan los genéricos con la interfaz `Set`:

```java
import java.util.HashSet;
import java.util.Set;

public class SetExample {
    public static void main(String[] args) {
        // Crear un conjunto de Strings usando genéricos
        Set<String> conjuntoNombres = new HashSet<>();

        // Agregar elementos al conjunto
        conjuntoNombres.add("Ana");
        conjuntoNombres.add("Luis");
        conjuntoNombres.add("Carlos");

        // Mostrar elementos del conjunto
        for (String nombre : conjuntoNombres) {
            System.out.println("Nombre: " + nombre);
        }
    }
}
```

### Ejemplo de Uso de Genéricos en `Map`

Aquí hay un ejemplo de cómo se usan los genéricos con la interfaz `Map`:

```java
import java.util.HashMap;
import java.util.Map;

public class MapExample {
    public static void main(String[] args) {
        // Crear un mapa de Strings a Strings usando genéricos
        Map<String, String> mapaNombres = new HashMap<>();

        // Agregar pares clave-valor al mapa
        mapaNombres.put("1", "Ana");
        mapaNombres.put("2", "Luis");
        mapaNombres.put("3", "Carlos");

        // Acceder y mostrar valores
        for (Map.Entry<String, String> entrada : mapaNombres.entrySet()) {
            System.out.println("Clave: " + entrada.getKey() + ", Valor: " + entrada.getValue());
        }
    }
}
```

## Ventajas de Usar Genéricos

- **Seguridad de Tipo**: Los genéricos permiten detectar errores de tipo en tiempo de compilación, evitando excepciones en tiempo de ejecución.
- **Eliminación de Castings**: Reduce la necesidad de hacer conversiones de tipo (casting) en tiempo de ejecución.
- **Mayor Legibilidad**: El código se vuelve más legible y fácil de mantener al utilizar tipos explícitos.

## Conclusión

El uso de genéricos en colecciones y en la definición de clases e interfaces proporciona una mayor seguridad y flexibilidad en Java. Al especificar los tipos de datos en tiempo de compilación, se minimizan los errores y se mejora la claridad del código.
