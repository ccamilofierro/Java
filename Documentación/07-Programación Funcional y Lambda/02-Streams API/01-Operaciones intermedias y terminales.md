# Operaciones Intermedias y Terminales en la API de Streams en Java

## Introducción

La API de Streams en Java proporciona un enfoque fluido y funcional para procesar secuencias de elementos. Esta API permite realizar operaciones en colecciones de manera declarativa. Las operaciones en los streams se dividen en dos categorías principales: operaciones intermedias y operaciones terminales.

## Operaciones Intermedias

Las operaciones intermedias son aquellas que transforman o filtran los elementos de un stream y devuelven un nuevo stream. Estas operaciones no se ejecutan de inmediato; en cambio, se realizan de forma perezosa (lazy), lo que significa que no se ejecutan hasta que se realiza una operación terminal.

### Ejemplos de Operaciones Intermedias

1. **`filter`**: Filtra los elementos del stream basándose en una condición.

```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class EjemploFilter {
    public static void main(String[] args) {
        List<String> nombres = Arrays.asList("Ana", "Luis", "Pedro", "María");
        List<String> nombresFiltrados = nombres.stream()
                                               .filter(nombre -> nombre.startsWith("P"))
                                               .collect(Collectors.toList());
        System.out.println(nombresFiltrados); // Imprime [Pedro]
    }
}
```

2. **`map`**: Transforma los elementos del stream aplicando una función.

```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class EjemploMap {
    public static void main(String[] args) {
        List<String> nombres = Arrays.asList("Ana", "Luis", "Pedro", "María");
        List<Integer> longitudes = nombres.stream()
                                          .map(String::length)
                                          .collect(Collectors.toList());
        System.out.println(longitudes); // Imprime [3, 4, 5, 5]
    }
}
```

3. **`distinct`**: Elimina elementos duplicados del stream.

```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class EjemploDistinct {
    public static void main(String[] args) {
        List<Integer> numeros = Arrays.asList(1, 2, 2, 3, 4, 4, 5);
        List<Integer> numerosUnicos = numeros.stream()
                                             .distinct()
                                             .collect(Collectors.toList());
        System.out.println(numerosUnicos); // Imprime [1, 2, 3, 4, 5]
    }
}
```

4. **`sorted`**: Ordena los elementos del stream.

```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class EjemploSorted {
    public static void main(String[] args) {
        List<String> nombres = Arrays.asList("Ana", "Luis", "Pedro", "María");
        List<String> nombresOrdenados = nombres.stream()
                                               .sorted()
                                               .collect(Collectors.toList());
        System.out.println(nombresOrdenados); // Imprime [Ana, Luis, María, Pedro]
    }
}
```

## Operaciones Terminales

Las operaciones terminales son aquellas que desencadenan la ejecución de las operaciones intermedias y producen un resultado, como un valor, una colección o una acción. Una vez que se realiza una operación terminal, el stream no puede ser reutilizado.

### Ejemplos de Operaciones Terminales

1. **`collect`**: Agrupa los elementos del stream en una colección.

```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class EjemploCollect {
    public static void main(String[] args) {
        List<String> nombres = Arrays.asList("Ana", "Luis", "Pedro", "María");
        List<String> nombresLista = nombres.stream()
                                           .collect(Collectors.toList());
        System.out.println(nombresLista); // Imprime [Ana, Luis, Pedro, María]
    }
}
```

2. **`forEach`**: Ejecuta una acción para cada elemento del stream.

```java
import java.util.Arrays;
import java.util.List;

public class EjemploForEach {
    public static void main(String[] args) {
        List<String> nombres = Arrays.asList("Ana", "Luis", "Pedro", "María");
        nombres.stream().forEach(System.out::println);
    }
}
```

3. **`reduce`**: Combina los elementos del stream utilizando una función acumuladora.

```java
import java.util.Arrays;
import java.util.List;
import java.util.Optional;

public class EjemploReduce {
    public static void main(String[] args) {
        List<Integer> numeros = Arrays.asList(1, 2, 3, 4, 5);
        Optional<Integer> suma = numeros.stream()
                                        .reduce((a, b) -> a + b);
        suma.ifPresent(System.out::println); // Imprime 15
    }
}
```

4. **`count`**: Cuenta el número de elementos en el stream.

```java
import java.util.Arrays;
import java.util.List;

public class EjemploCount {
    public static void main(String[] args) {
        List<String> nombres = Arrays.asList("Ana", "Luis", "Pedro", "María");
        long conteo = nombres.stream().count();
        System.out.println(conteo); // Imprime 4
    }
}
```

## Conclusión

Las operaciones intermedias y terminales en la API de Streams de Java permiten realizar procesamiento de datos de manera eficiente y expresiva. Las operaciones intermedias transforman o filtran los elementos del stream y se ejecutan de forma perezosa, mientras que las operaciones terminales desencadenan la ejecución de las operaciones intermedias y producen resultados o efectos colaterales. Entender cómo y cuándo utilizar cada tipo de operación es fundamental para aprovechar al máximo la API de Streams en Java.
