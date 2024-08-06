# Apache Commons y Google Guava en Java

## Introducción

En el ecosistema Java, las bibliotecas Apache Commons y Google Guava son ampliamente utilizadas para ofrecer utilidades adicionales que mejoran la funcionalidad y la productividad en el desarrollo. Estas bibliotecas proporcionan herramientas y utilidades que simplifican tareas comunes y ayudan a escribir código más limpio y eficiente.

## Apache Commons

Apache Commons es un proyecto de la Fundación Apache que proporciona una serie de bibliotecas de utilidades para diferentes aspectos de la programación en Java. Algunas de las bibliotecas más destacadas son:

### Apache Commons Lang

Esta biblioteca amplía las funcionalidades del paquete `java.lang`, proporcionando métodos adicionales para trabajar con strings, números, objetos y más.

#### Ejemplo de Uso

```java
import org.apache.commons.lang3.StringUtils;

public class EjemploCommonsLang {
    public static void main(String[] args) {
        String cadena = "   hola mundo   ";
        String cadenaLimpia = StringUtils.trim(cadena);
        System.out.println(cadenaLimpia); // Imprime "hola mundo"
    }
}
```

### Apache Commons Collections

Proporciona clases adicionales para trabajar con colecciones y ofrece implementaciones útiles de interfaces de colecciones, como listas, mapas y conjuntos.

#### Ejemplo de Uso

```java
import org.apache.commons.collections4.CollectionUtils;
import java.util.ArrayList;
import java.util.List;

public class EjemploCommonsCollections {
    public static void main(String[] args) {
        List<String> lista1 = new ArrayList<>();
        List<String> lista2 = new ArrayList<>();
        lista1.add("A");
        lista2.add("B");

        List<String> combinada = new ArrayList<>(CollectionUtils.union(lista1, lista2));
        System.out.println(combinada); // Imprime [A, B]
    }
}
```

## Google Guava

Google Guava es una biblioteca de Google que proporciona una serie de utilidades para la programación en Java. Ofrece herramientas para colecciones, cachés, concurrencia, IO y más.

### Guava Collections

Guava ofrece varias colecciones avanzadas que no están disponibles en la biblioteca estándar de Java, como `Multiset`, `Multimap` y `BiMap`.

#### Ejemplo de Uso

```java
import com.google.common.collect.ArrayListMultimap;
import com.google.common.collect.Multimap;

public class EjemploGuavaCollections {
    public static void main(String[] args) {
        Multimap<String, String> multimap = ArrayListMultimap.create();
        multimap.put("fruta", "manzana");
        multimap.put("fruta", "banana");

        System.out.println(multimap); // Imprime {fruta=[manzana, banana]}
    }
}
```

### Guava Cache

Guava proporciona una implementación de caché en memoria que es fácil de usar y configurar. Permite almacenar y recuperar objetos con políticas de expiración y tamaños máximos.

#### Ejemplo de Uso

```java
import com.google.common.cache.Cache;
import com.google.common.cache.CacheBuilder;
import java.util.concurrent.TimeUnit;

public class EjemploGuavaCache {
    public static void main(String[] args) {
        Cache<String, String> cache = CacheBuilder.newBuilder()
                                                 .expireAfterWrite(10, TimeUnit.MINUTES)
                                                 .maximumSize(100)
                                                 .build();

        cache.put("clave", "valor");
        String valor = cache.getIfPresent("clave");
        System.out.println(valor); // Imprime "valor"
    }
}
```

## Conclusión

Apache Commons y Google Guava proporcionan herramientas poderosas que extienden las capacidades estándar de Java. Utilizar estas bibliotecas puede simplificar el desarrollo, mejorar el rendimiento y proporcionar funcionalidades adicionales que no están disponibles en la biblioteca estándar de Java.
