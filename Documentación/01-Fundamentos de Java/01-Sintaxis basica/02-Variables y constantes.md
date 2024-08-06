# Variables y Constantes
Las variables son espacios de memoria donde almacenamos datos que pueden cambiar durante la ejecución del programa. Las constantes son similares a las variables, pero su valor no puede cambiar una vez que se les ha asignado.

## Variables
En Java, cada variable tiene un tipo de dato que define qué tipo de datos puede almacenar.

### Declaración de Variables
Para declarar una variable en Java, se especifica el tipo de dato seguido del nombre de la variable. Se puede asignar un valor inicial durante la declaración.

```java
int numero; // Declaración sin inicialización
int edad = 25; // Declaración con inicialización
String nombre = "Juan"; // Declaración de una cadena
double altura = 1.75; // Declaración de un número de coma flotante
boolean esMayor = true; // Declaración de un booleano
```

### Tipos de Variables
Las variables en Java pueden ser de distintos tipos según su ámbito de uso y comportamiento:

- **Variables locales**: Declaradas dentro de un método o un bloque y solo accesibles dentro de ese método o bloque.
- **Variables de instancia**: Declaradas dentro de una clase pero fuera de cualquier método. Se crean cuando se crea un objeto de la clase y cada objeto tiene su propia copia.
- **Variables de clase**: Declaradas con la palabra clave `static` dentro de una clase pero fuera de cualquier método. Solo hay una copia de la variable compartida por todos los objetos de la clase.

### Ejemplo de Uso de Variables
Aquí hay un ejemplo que muestra la declaración y el uso de diferentes tipos de variables en una clase Java:

```java
public class Persona {
    // Variable de clase
    static int numeroDePersonas = 0;

    // Variables de instancia
    String nombre;
    int edad;

    // Constructor
    public Persona(String nombre, int edad) {
        this.nombre = nombre;
        this.edad = edad;
        numeroDePersonas++;
    }

    // Método que utiliza una variable local
    public void mostrarInformacion() {
        String informacion = "Nombre: " + nombre + ", Edad: " + edad;
        System.out.println(informacion);
    }

    public static void main(String[] args) {
        Persona persona1 = new Persona("Juan", 25);
        Persona persona2 = new Persona("Ana", 30);

        persona1.mostrarInformacion();
        persona2.mostrarInformacion();

        System.out.println("Número de personas: " + Persona.numeroDePersonas);
    }
}
```

## Constantes
Las constantes en Java se declaran utilizando la palabra clave `final`. Una vez asignado, el valor de una constante no puede cambiar.

### Declaración de Constantes
Para declarar una constante, se utiliza `final` seguido del tipo de dato y el nombre de la constante. Se debe asignar un valor inicial al momento de la declaración.

```java
final int DIAS_SEMANA = 7;
final double PI = 3.14159;
final String MENSAJE_BIENVENIDA = "Bienvenido a Java";
```

### Ejemplo de Uso de Constantes
Aquí hay un ejemplo que muestra cómo declarar y utilizar constantes en una clase Java:

```java
public class Constantes {
    // Constantes
    public static final int DIAS_SEMANA = 7;
    public static final double PI = 3.14159;
    public static final String MENSAJE_BIENVENIDA = "Bienvenido a Java";

    public static void main(String[] args) {
        System.out.println("Días en una semana: " + DIAS_SEMANA);
        System.out.println("Valor de PI: " + PI);
        System.out.println(MENSAJE_BIENVENIDA);
    }
}
```

En este ejemplo, `DIAS_SEMANA`, `PI` y `MENSAJE_BIENVENIDA` son constantes y sus valores no pueden cambiar durante la ejecución del programa.

Con estos conceptos sobre variables y constantes, puedes manejar datos en tus programas Java de manera eficiente y segura.
