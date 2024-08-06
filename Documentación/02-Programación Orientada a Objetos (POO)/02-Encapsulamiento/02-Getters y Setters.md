# Getters y Setters en Java

## Introducción
En Java, los getters y setters son métodos especiales que se utilizan para obtener y modificar los valores de los atributos de una clase. Son parte de una práctica conocida como encapsulamiento, que es fundamental para mantener la integridad y el control de los datos dentro de una clase.

## Getters

### ¿Qué es un Getter?
Un getter es un método que se utiliza para obtener el valor de un atributo privado de una clase. Los getters permiten acceder a los datos de un objeto de forma controlada y segura.

### Sintaxis de un Getter
```java
public class NombreDeLaClase {
    private tipo atributo;

    // Getter
    public tipo getAtributo() {
        return atributo;
    }
}
```

### Ejemplo de Getter
```java
public class Persona {
    private String nombre;

    // Getter para el atributo nombre
    public String getNombre() {
        return nombre;
    }
}

public class Main {
    public static void main(String[] args) {
        Persona persona = new Persona();
        // Persona.nombre = "Juan"; // Incorrecto, atributo privado
        System.out.println(persona.getNombre()); // Correcto, usando el getter
    }
}
```

En este ejemplo, el método `getNombre()` es un getter que permite acceder al valor del atributo `nombre` de la clase `Persona`.

## Setters

### ¿Qué es un Setter?
Un setter es un método que se utiliza para modificar el valor de un atributo privado de una clase. Los setters permiten establecer o actualizar los datos de un objeto de manera controlada.

### Sintaxis de un Setter
```java
public class NombreDeLaClase {
    private tipo atributo;

    // Setter
    public void setAtributo(tipo valor) {
        this.atributo = valor;
    }
}
```

### Ejemplo de Setter
```java
public class Persona {
    private String nombre;

    // Setter para el atributo nombre
    public void setNombre(String nombre) {
        this.nombre = nombre;
    }
}

public class Main {
    public static void main(String[] args) {
        Persona persona = new Persona();
        persona.setNombre("Juan"); // Correcto, usando el setter
        System.out.println(persona.getNombre()); // Correcto, usando el getter
    }
}
```

En este ejemplo, el método `setNombre(String nombre)` es un setter que permite modificar el valor del atributo `nombre` de la clase `Persona`.

## Beneficios de Usar Getters y Setters

1. **Encapsulamiento**: Permiten ocultar los detalles de implementación de la clase y exponer solo lo necesario.
2. **Control de Acceso**: Puedes controlar cómo se accede y modifica los atributos. Por ejemplo, puedes validar datos antes de establecer un valor.
3. **Flexibilidad**: Puedes cambiar la implementación interna de la clase sin afectar a las clases que usan la clase.

## Consideraciones Adicionales
- **Validación**: En los setters, puedes incluir lógica de validación para asegurar que los valores asignados sean válidos.
- **Inmutabilidad**: Si deseas que un objeto sea inmutable, puedes proporcionar solo un getter y no un setter, asegurando que el atributo no pueda cambiar una vez que se ha asignado un valor.

Usar getters y setters es una buena práctica en la programación orientada a objetos que ayuda a mantener el código organizado y facilita el mantenimiento y la evolución del software.
