# Uso de `Function`, `Predicate`, `Consumer`, `Supplier` en Java

## Introducción

En Java, las interfaces funcionales `Function`, `Predicate`, `Consumer` y `Supplier` son parte del paquete `java.util.function` y son fundamentales para la programación funcional. Estas interfaces proporcionan formas estándar de trabajar con funciones, predicados, consumidores y proveedores de datos, facilitando la manipulación de datos y la programación basada en lambdas.

## `Function`

La interfaz `Function<T, R>` representa una función que toma un argumento de tipo `T` y devuelve un resultado de tipo `R`. Se utiliza para aplicar transformaciones a los datos.

### Ejemplo de `Function`

```java
import java.util.function.Function;

public class EjemploFunction {
    public static void main(String[] args) {
        Function<String, Integer> longitud = String::length;
        Integer longitudDeCadena = longitud.apply("Hola Mundo");
        System.out.println(longitudDeCadena); // Imprime 10
    }
}
```

## `Predicate`

La interfaz `Predicate<T>` representa un predicado que toma un argumento de tipo `T` y devuelve un valor booleano. Se utiliza para evaluar condiciones sobre los datos.

### Ejemplo de `Predicate`

```java
import java.util.function.Predicate;

public class EjemploPredicate {
    public static void main(String[] args) {
        Predicate<String> esLargo = str -> str.length() > 5;
        boolean resultado = esLargo.test("Hola Mundo");
        System.out.println(resultado); // Imprime true
    }
}
```

## `Consumer`

La interfaz `Consumer<T>` representa una operación que toma un argumento de tipo `T` y no devuelve ningún resultado. Se utiliza para realizar operaciones sobre los datos, como imprimir o modificar estados.

### Ejemplo de `Consumer`

```java
import java.util.function.Consumer;

public class EjemploConsumer {
    public static void main(String[] args) {
        Consumer<String> imprimir = System.out::println;
        imprimir.accept("Hola Mundo"); // Imprime Hola Mundo
    }
}
```

## `Supplier`

La interfaz `Supplier<T>` representa una función que no toma argumentos y devuelve un resultado de tipo `T`. Se utiliza para proporcionar valores, como generadores o proveedores de datos.

### Ejemplo de `Supplier`

```java
import java.util.function.Supplier;

public class EjemploSupplier {
    public static void main(String[] args) {
        Supplier<String> proveedor = () -> "Hola Mundo";
        String mensaje = proveedor.get();
        System.out.println(mensaje); // Imprime Hola Mundo
    }
}
```

## Combinación de Interfaces Funcionales

Estas interfaces se pueden combinar para realizar operaciones más complejas en Java Streams.

### Ejemplo de Combinación

```java
import java.util.Arrays;
import java.util.List;
import java.util.function.Function;
import java.util.function.Predicate;
import java.util.function.Consumer;
import java.util.function.Supplier;
import java.util.stream.Collectors;

public class EjemploCombinacion {
    public static void main(String[] args) {
        List<String> nombres = Arrays.asList("Ana", "Luis", "Pedro", "María");

        Predicate<String> esLargo = nombre -> nombre.length() > 3;
        Function<String, String> enMayusculas = String::toUpperCase;
        Consumer<String> imprimir = System.out::println;
        Supplier<String> proveedor = () -> "Lista de Nombres";

        System.out.println(proveedor.get());

        nombres.stream()
               .filter(esLargo)
               .map(enMayusculas)
               .forEach(imprimir);
    }
}
```

## Conclusión

Las interfaces funcionales `Function`, `Predicate`, `Consumer` y `Supplier` son herramientas poderosas en Java para trabajar con funciones, condiciones, operaciones y provisión de datos. Utilizar estas interfaces facilita el desarrollo de código más modular y reutilizable, especialmente cuando se trabaja con la API de Streams y programación funcional.
