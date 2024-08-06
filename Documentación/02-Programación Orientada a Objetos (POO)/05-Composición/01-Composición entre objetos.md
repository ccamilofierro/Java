# Relación "has-a" entre Objetos en Java

## Introducción

En la programación orientada a objetos, la relación "has-a" (también conocida como composición) describe una relación entre objetos en la que un objeto contiene o está compuesto por otros objetos. Esta relación es uno de los pilares del diseño orientado a objetos y se utiliza para modelar la forma en que los objetos interactúan y se organizan en una aplicación.

## Definición de la Relación "has-a"

La relación "has-a" se refiere a la composición de objetos. Esto significa que una clase puede tener referencias a otros objetos como sus atributos. Es una forma de expresar que un objeto "tiene" otro objeto.

### Ejemplo de Relación "has-a"

#### Ejemplo en Código
```java
// Clase que representa un Motor
public class Motor {
    private String tipo;

    public Motor(String tipo) {
        this.tipo = tipo;
    }

    public String getTipo() {
        return tipo;
    }
}

// Clase que representa un Coche
public class Coche {
    private Motor motor; // Relación "has-a"

    public Coche(Motor motor) {
        this.motor = motor;
    }

    public void mostrarDetalles() {
        System.out.println("Tipo de motor: " + motor.getTipo());
    }
}

public class Main {
    public static void main(String[] args) {
        Motor motorV8 = new Motor("V8");
        Coche miCoche = new Coche(motorV8);
        miCoche.mostrarDetalles(); // Salida: Tipo de motor: V8
    }
}
```

En este ejemplo, la clase `Coche` tiene una relación "has-a" con la clase `Motor`. Un coche tiene un motor, por lo que se crea una instancia de `Motor` como atributo de la clase `Coche`. Esta relación se establece mediante la inclusión de un objeto `Motor` en la clase `Coche`.

## Ventajas de la Composición

1. **Reusabilidad**: La composición permite reutilizar componentes y objetos en diferentes contextos. Puedes crear diferentes clases que contengan una instancia del mismo tipo de objeto, promoviendo la reutilización del código.

2. **Modularidad**: Facilita la creación de sistemas modulares y bien organizados, donde cada clase se encarga de una responsabilidad específica.

3. **Flexibilidad**: Permite cambiar el comportamiento de un objeto en tiempo de ejecución al modificar la composición de objetos, sin necesidad de heredar de una clase base.

4. **Encapsulamiento**: Mejora el encapsulamiento al ocultar los detalles internos del objeto compuesto, proporcionando una interfaz clara y sencilla.

## Comparación con la Herencia

- **Herencia**: Representa una relación "is-a" (es un tipo de) en la que una subclase hereda de una superclase. Por ejemplo, un `Perro` "es un tipo de" `Animal`.
  
- **Composición**: Representa una relación "has-a" (tiene un) en la que un objeto contiene o está compuesto por otros objetos. Por ejemplo, un `Coche` "tiene un" `Motor`.

## Ejemplo Adicional

#### Ejemplo de Composición con Varias Clases
```java
// Clase que representa una Dirección
public class Direccion {
    private String calle;
    private String ciudad;

    public Direccion(String calle, String ciudad) {
        this.calle = calle;
        this.ciudad = ciudad;
    }

    public String getDireccionCompleta() {
        return calle + ", " + ciudad;
    }
}

// Clase que representa una Persona
public class Persona {
    private String nombre;
    private Direccion direccion; // Relación "has-a"

    public Persona(String nombre, Direccion direccion) {
        this.nombre = nombre;
        this.direccion = direccion;
    }

    public void mostrarInformacion() {
        System.out.println("Nombre: " + nombre);
        System.out.println("Dirección: " + direccion.getDireccionCompleta());
    }
}

public class Main {
    public static void main(String[] args) {
        Direccion direccion = new Direccion("123 Calle Principal", "Ciudad Ejemplo");
        Persona persona = new Persona("Juan Pérez", direccion);
        persona.mostrarInformacion();
    }
}
```

En este ejemplo, la clase `Persona` tiene una relación "has-a" con la clase `Direccion`. Una persona tiene una dirección, por lo que se crea una instancia de `Direccion` como atributo de la clase `Persona`.

La relación "has-a" es esencial para diseñar sistemas modulares y flexibles en la programación orientada a objetos, permitiendo una organización eficiente de los objetos y sus interacciones.
