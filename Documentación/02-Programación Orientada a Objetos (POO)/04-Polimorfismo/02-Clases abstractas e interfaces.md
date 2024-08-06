# Clases Abstractas e Interfaces en Java

## Clases Abstractas

### Introducción
Una clase abstracta en Java es una clase que no puede ser instanciada directamente. Se utiliza como una clase base para otras clases que deben implementar o extender sus métodos. Las clases abstractas pueden contener métodos abstractos (métodos sin implementación) y métodos concretos (métodos con implementación).

### Definición de Clase Abstracta
Para definir una clase abstracta, se utiliza la palabra clave `abstract` en la declaración de la clase.

#### Ejemplo de Clase Abstracta
///java
// Clase abstracta
public abstract class Animal {
    protected String nombre;

    public Animal(String nombre) {
        this.nombre = nombre;
    }

    // Método abstracto (sin implementación)
    public abstract void hacerSonido();

    // Método concreto (con implementación)
    public void dormir() {
        System.out.println(nombre + " está durmiendo.");
    }
}

// Clase derivada
public class Perro extends Animal {
    public Perro(String nombre) {
        super(nombre);
    }

    @Override
    public void hacerSonido() {
        System.out.println("El perro ladra.");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal miPerro = new Perro("Rex");
        miPerro.hacerSonido(); // Salida: El perro ladra.
        miPerro.dormir(); // Salida: Rex está durmiendo.
    }
}
///

En este ejemplo, `Animal` es una clase abstracta con un método abstracto `hacerSonido` y un método concreto `dormir`. La clase `Perro` extiende `Animal` e implementa el método abstracto `hacerSonido`.

### Características de las Clases Abstractas

- **No se Pueden Instanciar**: No puedes crear instancias directas de una clase abstracta.
- **Métodos Abstractos**: Deben ser implementados por las clases derivadas.
- **Métodos Concretos**: Pueden ser opcionales en una clase abstracta y proporcionan una implementación predeterminada.
- **Constructores**: Las clases abstractas pueden tener constructores, que son llamados por las subclases.

## Interfaces

### Introducción
Una interfaz en Java es una referencia de tipo que puede contener métodos abstractos (métodos sin implementación) y constantes. A partir de Java 8, las interfaces también pueden contener métodos concretos y métodos predeterminados con implementación. Las interfaces se utilizan para definir un contrato que las clases deben cumplir.

### Definición de Interfaz
Para definir una interfaz, se utiliza la palabra clave `interface`.

#### Ejemplo de Interfaz
///java
// Interfaz
public interface Volador {
    // Método abstracto
    void volar();

    // Método predeterminado
    default void planear() {
        System.out.println("El objeto está planeando.");
    }
}

// Clase que implementa la interfaz
public class Pajaro implements Volador {
    @Override
    public void volar() {
        System.out.println("El pájaro está volando.");
    }
}

public class Main {
    public static void main(String[] args) {
        Volador miPajaro = new Pajaro();
        miPajaro.volar(); // Salida: El pájaro está volando.
        miPajaro.planear(); // Salida: El objeto está planeando.
    }
}
///

En este ejemplo, `Volador` es una interfaz con un método abstracto `volar` y un método predeterminado `planear`. La clase `Pajaro` implementa la interfaz `Volador` y proporciona una implementación para el método `volar`.

### Características de las Interfaces

- **Implementación Múltiple**: Las clases pueden implementar múltiples interfaces, lo que permite simular herencia múltiple.
- **Métodos Abstractos y Predeterminados**: Desde Java 8, las interfaces pueden tener métodos predeterminados con implementación.
- **Constantes**: Los campos en una interfaz son implícitamente `public`, `static`, y `final` (constantes).
- **Implementación Obligatoria**: Las clases que implementan una interfaz deben proporcionar una implementación para todos los métodos abstractos de la interfaz.

## Comparación entre Clases Abstractas e Interfaces

- **Herencia**: Las clases abstractas permiten heredar de una sola clase base, mientras que las interfaces permiten implementar múltiples interfaces.
- **Métodos**: Las clases abstractas pueden contener métodos concretos, mientras que las interfaces, hasta Java 8, solo podían contener métodos abstractos.
- **Uso**: Las clases abstractas son útiles para compartir código entre clases relacionadas, mientras que las interfaces son útiles para definir contratos que pueden ser implementados por clases no relacionadas.

Las clases abstractas y las interfaces son herramientas fundamentales en Java para la programación orientada a objetos, proporcionando flexibilidad en la estructura del código y en la implementación de comportamiento.
