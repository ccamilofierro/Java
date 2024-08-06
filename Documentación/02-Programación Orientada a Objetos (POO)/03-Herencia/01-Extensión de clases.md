# Extensión de Clases en Java

## Introducción
La extensión de clases en Java se refiere a la capacidad de crear nuevas clases que heredan atributos y métodos de una clase existente. Esto permite reutilizar código y extender el comportamiento de una clase base. En Java, la herencia se logra utilizando la palabra clave `extends`.

## Clases Base y Clases Derivadas

### Clase Base
Una clase base es la clase de la cual se hereda. Define atributos y métodos que pueden ser reutilizados por otras clases.

### Clase Derivada
Una clase derivada (o subclase) es una clase que hereda de una clase base. Puede utilizar los atributos y métodos de la clase base y también puede agregar sus propios atributos y métodos adicionales.

## Sintaxis de la Extensión de Clases
Para extender una clase en Java, se utiliza la palabra clave `extends` seguida del nombre de la clase base.

### Ejemplo de Extensión de Clases
```java
// Clase base
public class Animal {
    protected String nombre;

    public void hacerSonido() {
        System.out.println("El animal hace un sonido.");
    }
}

// Clase derivada
public class Perro extends Animal {
    public void ladrar() {
        System.out.println("El perro está ladrando.");
    }
}

public class Main {
    public static void main(String[] args) {
        Perro miPerro = new Perro();
        miPerro.nombre = "Rex"; // Acceso al atributo protegido de la clase base
        miPerro.hacerSonido(); // Método heredado de la clase base
        miPerro.ladrar(); // Método específico de la clase derivada
    }
}
```

En este ejemplo, `Perro` extiende la clase `Animal`. La clase `Perro` hereda el atributo `nombre` y el método `hacerSonido` de la clase `Animal`, y también define su propio método `ladrar`.

## Reglas de Herencia

1. **Herencia Simple**: Java admite herencia simple, lo que significa que una clase puede heredar de una sola clase base. La herencia múltiple (heredar de varias clases) no está permitida en Java.
   
2. **Constructores**: Los constructores no se heredan. Sin embargo, la clase derivada puede llamar a los constructores de la clase base utilizando la palabra clave `super`.

3. **Sobrescritura de Métodos**: Una subclase puede sobrescribir (override) métodos de la clase base para proporcionar una implementación específica. Para sobrescribir un método, la firma del método en la subclase debe coincidir con la firma del método en la clase base.

4. **Palabra Clave `super`**: La palabra clave `super` se utiliza para referirse a miembros de la clase base desde la subclase. Puedes usar `super` para llamar a métodos y constructores de la clase base.

### Ejemplo de Sobrescritura de Métodos
```java
// Clase base
public class Animal {
    public void hacerSonido() {
        System.out.println("El animal hace un sonido.");
    }
}

// Clase derivada
public class Gato extends Animal {
    @Override
    public void hacerSonido() {
        System.out.println("El gato maúlla.");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal miAnimal = new Gato();
        miAnimal.hacerSonido(); // Salida: El gato maúlla.
    }
}
```

En este ejemplo, la clase `Gato` sobrescribe el método `hacerSonido` de la clase base `Animal`, proporcionando una implementación específica para los gatos.

## Consideraciones Adicionales
- **Polimorfismo**: La herencia permite el uso de polimorfismo, donde una variable de tipo de clase base puede referirse a un objeto de una clase derivada.
- **Acceso a Miembros**: Solo los miembros `public` y `protected` de la clase base son accesibles en la subclase. Los miembros `private` no son accesibles directamente.

La extensión de clases es una característica fundamental en la programación orientada a objetos que permite construir jerarquías de clases y reutilizar código de manera eficiente.
