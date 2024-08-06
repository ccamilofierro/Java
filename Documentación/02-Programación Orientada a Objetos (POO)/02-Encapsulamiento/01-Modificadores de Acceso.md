# Modificadores de Acceso en Java

## Introducción a los Modificadores de Acceso
Los modificadores de acceso en Java controlan la visibilidad y el acceso a clases, métodos y atributos. Determinan desde dónde se puede acceder a una clase, método o atributo específico. Los tres modificadores de acceso principales son `private`, `public`, y `protected`.

## Modificadores de Acceso

### 1. `private`
El modificador `private` restringe el acceso a los miembros de una clase (atributos y métodos) solo dentro de esa misma clase. Los miembros `private` no son accesibles desde fuera de la clase, ni siquiera desde las clases heredadas.

#### Ejemplo de `private`
```java
public class Persona {
    // Atributo privado
    private String nombre;

    // Método privado
    private void mostrarNombre() {
        System.out.println("Nombre: " + nombre);
    }

    // Método público para acceder al atributo privado
    public void establecerNombre(String nombre) {
        this.nombre = nombre;
    }

    // Método público para acceder al método privado
    public void mostrarInformacion() {
        mostrarNombre();
    }
}

public class Main {
    public static void main(String[] args) {
        Persona persona = new Persona();
        persona.establecerNombre("Juan");
        persona.mostrarInformacion(); // Correcto, llama a un método público que usa un método privado
        // persona.mostrarNombre(); // Incorrecto, muestra error: método privado
    }
}
```

En este ejemplo, el atributo `nombre` y el método `mostrarNombre` son privados y solo pueden ser accedidos dentro de la clase `Persona`. Los métodos públicos `establecerNombre` y `mostrarInformacion` permiten acceder a estos miembros privados de manera controlada.

### 2. `public`
El modificador `public` permite que los miembros de una clase sean accesibles desde cualquier otra clase en cualquier paquete. Los miembros `public` tienen la máxima visibilidad.

#### Ejemplo de `public`
```java
public class Coche {
    // Atributo público
    public String modelo;

    // Método público
    public void encender() {
        System.out.println("El coche está encendido.");
    }
}

public class Main {
    public static void main(String[] args) {
        Coche miCoche = new Coche();
        miCoche.modelo = "Toyota"; // Correcto, atributo público
        miCoche.encender(); // Correcto, método público
    }
}
```

En este ejemplo, el atributo `modelo` y el método `encender` de la clase `Coche` son públicos y se pueden acceder desde cualquier otra clase.

### 3. `protected`
El modificador `protected` permite que los miembros de una clase sean accesibles dentro del mismo paquete y por clases que heredan de la clase en cuestión, incluso si estas clases están en paquetes diferentes.

#### Ejemplo de `protected`
```java
public class Animal {
    // Atributo protegido
    protected String nombre;

    // Método protegido
    protected void hacerSonido() {
        System.out.println("El animal hace un sonido.");
    }
}

public class Perro extends Animal {
    public void mostrarInformacion() {
        nombre = "Rex"; // Correcto, atributo protegido
        hacerSonido(); // Correcto, método protegido
    }
}

public class Main {
    public static void main(String[] args) {
        Perro miPerro = new Perro();
        miPerro.mostrarInformacion(); // Correcto, accede a miembros protegidos
    }
}
```

En este ejemplo, el atributo `nombre` y el método `hacerSonido` son protegidos, por lo que son accesibles desde la subclase `Perro` incluso si está en un paquete diferente.

## Consideraciones Adicionales
- **Encapsulamiento**: Usar `private` para atributos y proporcionar métodos `public` para acceder a ellos (getters y setters) es una práctica común para mantener el encapsulamiento.
- **Visibilidad**: Elegir el modificador de acceso adecuado depende del nivel de visibilidad que deseas para los miembros de tu clase.

Comprender y utilizar correctamente los modificadores de acceso es esencial para controlar la visibilidad y la seguridad de los datos en tus programas Java.
