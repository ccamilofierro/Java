# Filtrado, Mapeo y Reducción de Datos en la API de Streams en Java

## Introducción

En la API de Streams en Java, las operaciones de filtrado, mapeo y reducción son fundamentales para procesar y manipular datos de manera eficiente. Estas operaciones permiten transformar, seleccionar y combinar datos de formas muy expresivas.

## Filtrado

El filtrado se utiliza para seleccionar elementos de un stream que cumplen con una condición específica. La operación `filter` permite crear un nuevo stream que contiene solo los elementos que satisfacen el predicado proporcionado.

### Ejemplo de Filtrado

```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class EjemploFiltrado {
    public static void main(String[] args) {
        List<String> nombres = Arrays.asList("Ana", "Luis", "Pedro", "María");
        List<String> nombresFiltrados = nombres.stream()
                                               .filter(nombre -> nombre.length() > 4)
                                               .collect(Collectors.toList());
        System.out.println(nombresFiltrados); // Imprime [Pedro, María]
    }
}
```

## Mapeo

El mapeo se usa para transformar los elementos de un stream en otros valores mediante la operación `map`. Esta operación aplica una función a cada elemento del stream, produciendo un nuevo stream con los resultados de la función.

### Ejemplo de Mapeo

```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class EjemploMapeo {
    public static void main(String[] args) {
        List<String> nombres = Arrays.asList("Ana", "Luis", "Pedro", "María");
        List<String> nombresEnMayusculas = nombres.stream()
                                                  .map(String::toUpperCase)
                                                  .collect(Collectors.toList());
        System.out.println(nombresEnMayusculas); // Imprime [ANA, LUIS, PEDRO, MARÍA]
    }
}
```

## Reducción

La reducción se utiliza para combinar los elementos de un stream en un único valor. La operación `reduce` aplica una función acumuladora a los elementos del stream para producir un resultado agregado. Esta operación es útil para calcular valores como sumas, productos, o concatenaciones.

### Ejemplo de Reducción

```java
import java.util.Arrays;
import java.util.List;
import java.util.Optional;

public class EjemploReduccion {
    public static void main(String[] args) {
        List<Integer> numeros = Arrays.asList(1, 2, 3, 4, 5);
        Optional<Integer> suma = numeros.stream()
                                        .reduce((a, b) -> a + b);
        suma.ifPresent(System.out::println); // Imprime 15
    }
}
```

## Combinación de Operaciones

A menudo, se combinan las operaciones de filtrado, mapeo y reducción en una secuencia de operaciones para lograr un procesamiento de datos más complejo.

### Ejemplo de Combinación

```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class EjemploCombinacion {
    public static void main(String[] args) {
        List<String> nombres = Arrays.asList("Ana", "Luis", "Pedro", "María");
        int longitudTotal = nombres.stream()
                                   .filter(nombre -> nombre.length() > 3)
                                   .map(String::length)
                                   .reduce(0, Integer::sum);
        System.out.println(longitudTotal); // Imprime 18
    }
}
```

## Conclusión

El filtrado, mapeo y reducción son operaciones esenciales en la API de Streams en Java, que permiten transformar y combinar datos de manera eficiente. Estas operaciones facilitan el procesamiento de datos de forma declarativa y expresiva, mejorando la legibilidad y mantenibilidad del código.
