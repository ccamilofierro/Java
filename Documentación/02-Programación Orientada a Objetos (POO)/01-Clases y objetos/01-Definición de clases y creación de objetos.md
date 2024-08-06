# Definición de Clases y Creación de Objetos en Java

## Definición de Clases
En Java, una clase es una plantilla para crear objetos. Define atributos (propiedades) y métodos (comportamientos) que los objetos creados a partir de la clase tendrán.

### Sintaxis para Definir una Clase
```java
public class NombreDeLaClase {
    // Atributos (propiedades) de la clase
    tipo nombreAtributo;

    // Métodos (comportamientos) de la clase
    public void nombreDelMetodo() {
        // Código del método
    }
}
```

### Ejemplo de Definición de Clase
```java
public class Persona {
    // Atributos
    String nombre;
    int edad;

    // Método
    public void saludar() {
        System.out.println("Hola, mi nombre es " + nombre + " y tengo " + edad + " años.");
    }
}
```

En este ejemplo, la clase `Persona` tiene dos atributos (`nombre` y `edad`) y un método (`saludar`) que utiliza estos atributos para imprimir un saludo en la consola.

## Creación de Objetos
Una vez que se ha definido una clase, se pueden crear objetos (instancias) de esa clase. Los objetos son entidades concretas que tienen su propio estado y comportamiento definidos por la clase.

### Sintaxis para Crear un Objeto
```java
NombreDeLaClase nombreDelObjeto = new NombreDeLaClase();
```

### Ejemplo de Creación de Objetos
```java
public class Main {
    public static void main(String[] args) {
        // Crear un objeto de la clase Persona
        Persona persona1 = new Persona();
        
        // Inicializar los atributos del objeto
        persona1.nombre = "Juan";
        persona1.edad = 25;
        
        // Llamar al método del objeto
        persona1.saludar();
    }
}
```

En este ejemplo, se crea un objeto `persona1` de la clase `Persona`. Se inicializan los atributos del objeto (`nombre` y `edad`) y se llama al método `saludar` para imprimir un saludo en la consola.

## Constructor de Clases
Los constructores son métodos especiales que se utilizan para inicializar objetos. Se llaman automáticamente cuando se crea un objeto de la clase.

### Sintaxis del Constructor
```java
public class NombreDeLaClase {
    // Constructor
    public NombreDeLaClase(tipo parametro1, tipo parametro2) {
        // Inicialización de atributos
    }
}
```

### Ejemplo de Constructor
```java
public class Persona {
    String nombre;
    int edad;

    // Constructor
    public Persona(String nombre, int edad) {
        this.nombre = nombre;
        this.edad = edad;
    }

    public void saludar() {
        System.out.println("Hola, mi nombre es " + nombre + " y tengo " + edad + " años.");
    }
}

public class Main {
    public static void main(String[] args) {
        // Crear un objeto de la clase Persona utilizando el constructor
        Persona persona1 = new Persona("Ana", 30);
        
        // Llamar al método del objeto
        persona1.saludar();
    }
}
```

En este ejemplo, el constructor de la clase `Persona` inicializa los atributos `nombre` y `edad` cuando se crea un objeto de la clase.

Estos conceptos te permitirán definir y utilizar clases y objetos en Java, facilitando la creación de programas organizados y modulares.
