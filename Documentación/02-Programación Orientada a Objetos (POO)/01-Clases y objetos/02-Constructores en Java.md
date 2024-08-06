# Constructores en Java

## ¿Qué es un Constructor?
Un constructor es un método especial en una clase que se llama automáticamente cuando se crea un objeto de esa clase. Su propósito principal es inicializar los atributos del objeto. Un constructor tiene el mismo nombre que la clase y no tiene tipo de retorno, ni siquiera `void`.

### Características de los Constructores
- **Nombre**: El nombre del constructor debe ser igual al nombre de la clase.
- **Tipo de Retorno**: Los constructores no tienen tipo de retorno.
- **Llamada Automática**: Se llaman automáticamente cuando se crea un objeto de la clase.

## Tipos de Constructores

### 1. Constructor por Defecto
El constructor por defecto es un constructor que no recibe parámetros. Java proporciona automáticamente un constructor por defecto si no defines ninguno en tu clase.

#### Ejemplo de Constructor por Defecto
```java
public class Coche {
    String marca;
    String modelo;

    // Constructor por defecto
    public Coche() {
        marca = "Desconocida";
        modelo = "Desconocido";
    }
}

public class Main {
    public static void main(String[] args) {
        // Crear un objeto usando el constructor por defecto
        Coche miCoche = new Coche();
        System.out.println("Marca: " + miCoche.marca);
        System.out.println("Modelo: " + miCoche.modelo);
    }
}
```

En este ejemplo, el constructor por defecto de la clase `Coche` inicializa los atributos `marca` y `modelo` con valores predeterminados.

### 2. Constructor con Parámetros
Un constructor con parámetros permite inicializar los atributos de una clase con valores específicos proporcionados en el momento de la creación del objeto.

#### Ejemplo de Constructor con Parámetros
```java
public class Coche {
    String marca;
    String modelo;

    // Constructor con parámetros
    public Coche(String marca, String modelo) {
        this.marca = marca;
        this.modelo = modelo;
    }
}

public class Main {
    public static void main(String[] args) {
        // Crear un objeto usando el constructor con parámetros
        Coche miCoche = new Coche("Toyota", "Corolla");
        System.out.println("Marca: " + miCoche.marca);
        System.out.println("Modelo: " + miCoche.modelo);
    }
}
```

En este ejemplo, el constructor con parámetros de la clase `Coche` inicializa los atributos `marca` y `modelo` con los valores proporcionados.

## Sobrecarga de Constructores
Java permite la sobrecarga de constructores, lo que significa que puedes definir múltiples constructores en una clase con diferentes listas de parámetros. Esto proporciona flexibilidad en la creación de objetos.

#### Ejemplo de Sobrecarga de Constructores
```java
public class Coche {
    String marca;
    String modelo;
    int año;

    // Constructor por defecto
    public Coche() {
        marca = "Desconocida";
        modelo = "Desconocido";
        año = 0;
    }

    // Constructor con dos parámetros
    public Coche(String marca, String modelo) {
        this.marca = marca;
        this.modelo = modelo;
        año = 0;
    }

    // Constructor con tres parámetros
    public Coche(String marca, String modelo, int año) {
        this.marca = marca;
        this.modelo = modelo;
        this.año = año;
    }
}

public class Main {
    public static void main(String[] args) {
        // Crear objetos usando diferentes constructores
        Coche coche1 = new Coche();
        Coche coche2 = new Coche("Honda", "Civic");
        Coche coche3 = new Coche("Ford", "Mustang", 2023);
        
        System.out.println("Coche 1 - Marca: " + coche1.marca + ", Modelo: " + coche1.modelo + ", Año: " + coche1.año);
        System.out.println("Coche 2 - Marca: " + coche2.marca + ", Modelo: " + coche2.modelo + ", Año: " + coche2.año);
        System.out.println("Coche 3 - Marca: " + coche3.marca + ", Modelo: " + coche3.modelo + ", Año: " + coche3.año);
    }
}
```

En este ejemplo, la clase `Coche` tiene tres constructores sobrecargados, permitiendo crear objetos con diferentes combinaciones de atributos.

## Consideraciones Adicionales
- **Inicialización de Atributos**: Los constructores son útiles para garantizar que los atributos de un objeto estén inicializados correctamente.
- **Construcción de Objetos**: Puedes usar constructores para proporcionar diferentes formas de inicializar objetos, mejorando la flexibilidad y la legibilidad del código.

Los constructores son una parte esencial de la programación orientada a objetos en Java, facilitando la creación y configuración de objetos de manera eficiente.
