# Map en Java: `HashMap` y `TreeMap`

## Introducción

En Java, la interfaz `Map` es parte del paquete `java.util` y representa una colección de pares clave-valor. Cada clave está asociada con un valor, y una clave no puede estar duplicada en el mapa. Las implementaciones más comunes de la interfaz `Map` son `HashMap` y `TreeMap`. Cada una ofrece características específicas y ventajas según el uso requerido.

## `HashMap`

`HashMap` es una implementación de la interfaz `Map` que utiliza una tabla hash para almacenar las claves y valores. Ofrece un acceso rápido a los elementos basado en la clave y no garantiza el orden de los elementos.

### Características de `HashMap`

- **Sin Orden**: No garantiza ningún orden para las claves y los valores.
- **Acceso Rápido**: Proporciona operaciones rápidas de inserción, eliminación y búsqueda (O(1) promedio).
- **Permite Claves y Valores Nulos**: Acepta una clave nula y valores nulos.

### Ejemplo de Uso de `HashMap`
```java
import java.util.HashMap;

public class HashMapExample {
    public static void main(String[] args) {
        // Crear una instancia de HashMap
        HashMap<String, String> mapaNombres = new HashMap<>();

        // Agregar pares clave-valor al mapa
        mapaNombres.put("1", "Ana");
        mapaNombres.put("2", "Luis");
        mapaNombres.put("3", "Carlos");

        // Acceder a un valor usando una clave
        System.out.println("Nombre con clave 1: " + mapaNombres.get("1"));

        // Recorrer el mapa
        for (String clave : mapaNombres.keySet()) {
            System.out.println("Clave: " + clave + ", Valor: " + mapaNombres.get(clave));
        }

        // Eliminar un par clave-valor
        mapaNombres.remove("2");

        // Mostrar el mapa después de la eliminación
        System.out.println("Mapa después de la eliminación: " + mapaNombres);
    }
}
```

## `TreeMap`

`TreeMap` es otra implementación de la interfaz `Map` que utiliza un árbol rojo-negro para almacenar las claves y valores. Proporciona un mapa ordenado en el que las claves están organizadas en un orden específico (generalmente orden natural o basado en un comparador).

### Características de `TreeMap`

- **Ordenado**: Mantiene las claves en un orden específico, basado en el orden natural de las claves o en un comparador proporcionado.
- **Acceso Más Lento**: Las operaciones de inserción, eliminación y búsqueda son más lentas en comparación con `HashMap` (O(log n)).
- **No Permite Claves Nulas**: No acepta claves nulas, pero permite valores nulos.

### Ejemplo de Uso de `TreeMap`
```java
import java.util.TreeMap;

public class TreeMapExample {
    public static void main(String[] args) {
        // Crear una instancia de TreeMap
        TreeMap<String, String> mapaNombres = new TreeMap<>();

        // Agregar pares clave-valor al mapa
        mapaNombres.put("1", "Ana");
        mapaNombres.put("2", "Luis");
        mapaNombres.put("3", "Carlos");

        // Acceder a un valor usando una clave
        System.out.println("Nombre con clave 1: " + mapaNombres.get("1"));

        // Recorrer el mapa
        for (String clave : mapaNombres.keySet()) {
            System.out.println("Clave: " + clave + ", Valor: " + mapaNombres.get(clave));
        }

        // Eliminar un par clave-valor
        mapaNombres.remove("2");

        // Mostrar el mapa después de la eliminación
        System.out.println("Mapa después de la eliminación: " + mapaNombres);
    }
}
```

## Comparación entre `HashMap` y `TreeMap`

- **Orden de las Claves**:
  - `HashMap`: No garantiza ningún orden para las claves.
  - `TreeMap`: Mantiene las claves en un orden específico (orden natural o basado en un comparador).

- **Rendimiento**:
  - `HashMap`: Ofrece operaciones rápidas de inserción, eliminación y búsqueda (O(1) promedio).
  - `TreeMap`: Ofrece operaciones ordenadas y más lentas (O(log n)).

- **Uso de Claves y Valores Nulos**:
  - `HashMap`: Acepta una clave nula y valores nulos.
  - `TreeMap`: No acepta claves nulas, pero permite valores nulos.

- **Iteración**:
  - `HashMap`: La iteración sobre las claves y valores no sigue un orden específico.
  - `TreeMap`: La iteración sigue el orden definido por el árbol.

Ambas implementaciones de `Map` tienen usos y beneficios específicos. La elección entre `HashMap` y `TreeMap` dependerá de si necesitas un mapa ordenado o si el rendimiento en operaciones básicas es tu principal preocupación.
