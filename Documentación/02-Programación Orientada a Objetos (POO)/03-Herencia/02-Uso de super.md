# Uso de `super` en Java

## Introducción
En Java, la palabra clave `super` se utiliza para referirse a los miembros (atributos y métodos) de la clase base desde una subclase. Es útil para acceder a métodos y atributos que han sido sobrescritos o para invocar el constructor de la clase base desde la subclase.

## Uso de `super`

### 1. Acceso a Atributos y Métodos de la Clase Base

Cuando una subclase tiene un atributo o método con el mismo nombre que en la clase base, puedes usar `super` para referenciar el atributo o método de la clase base.

#### Ejemplo de Acceso a Atributos
```java
public class Animal {
    protected String nombre = "Animal";

    public void hacerSonido() {
        System.out.println("El animal hace un sonido.");
    }
}

public class Perro extends Animal {
    private String nombre = "Perro";

    public void mostrarNombres() {
        System.out.println("Nombre en la clase base: " + super.nombre);
        System.out.println("Nombre en la clase derivada: " + this.nombre);
    }
}

public class Main {
    public static void main(String[] args) {
        Perro miPerro = new Perro();
        miPerro.mostrarNombres();
    }
}
```

En este ejemplo, `super.nombre` accede al atributo `nombre` de la clase base `Animal`, mientras que `this.nombre` accede al atributo `nombre` de la clase derivada `Perro`.

### 2. Llamada a Métodos Sobrescritos

Cuando un método en la subclase sobrescribe un método en la clase base, puedes usar `super` para llamar al método de la clase base desde la subclase.

#### Ejemplo de Llamada a Métodos
```java
public class Animal {
    public void hacerSonido() {
        System.out.println("El animal hace un sonido.");
    }
}

public class Gato extends Animal {
    @Override
    public void hacerSonido() {
        super.hacerSonido(); // Llama al método de la clase base
        System.out.println("El gato maúlla.");
    }
}

public class Main {
    public static void main(String[] args) {
        Gato miGato = new Gato();
        miGato.hacerSonido();
    }
}
```

En este ejemplo, `super.hacerSonido()` llama al método `hacerSonido` de la clase base `Animal` antes de ejecutar el código adicional en la subclase `Gato`.

### 3. Invocación de Constructores de la Clase Base

Puedes usar `super` para invocar el constructor de la clase base desde el constructor de la subclase. Esto es útil para inicializar los atributos de la clase base.

#### Ejemplo de Invocación de Constructores
```java
public class Animal {
    public Animal(String nombre) {
        System.out.println("Constructor de Animal: " + nombre);
    }
}

public class Perro extends Animal {
    public Perro(String nombre) {
        super(nombre); // Llama al constructor de la clase base
        System.out.println("Constructor de Perro: " + nombre);
    }
}

public class Main {
    public static void main(String[] args) {
        Perro miPerro = new Perro("Rex");
    }
}
```

En este ejemplo, `super(nombre)` llama al constructor de la clase base `Animal`, permitiendo la inicialización del atributo `nombre` antes de ejecutar el código en el constructor de la subclase `Perro`.

## Consideraciones Adicionales
- **Uso en Herencia Múltiple**: Java no admite herencia múltiple de clases, por lo que `super` solo se utiliza para acceder a la clase base directa.
- **Acceso a Miembros Privados**: Los miembros `private` de la clase base no son accesibles mediante `super`, solo los miembros `protected` y `public`.

La palabra clave `super` es una herramienta poderosa en Java para manejar la herencia y el acceso a miembros de la clase base, facilitando la reutilización del código y la extensión de funcionalidades.
