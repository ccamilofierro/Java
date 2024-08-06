# Sintaxis de Expresiones Lambda en Java

## Introducción

Las expresiones lambda, introducidas en Java 8, permiten escribir código más conciso y legible al representar implementaciones de interfaces funcionales. Son especialmente útiles en el contexto de la programación funcional y se utilizan comúnmente en la API de Streams y en el manejo de eventos.

## ¿Qué es una Expresión Lambda?

Una expresión lambda es una forma de definir una implementación anónima de una interfaz funcional (una interfaz con un solo método abstracto) de manera más compacta. Las expresiones lambda eliminan la necesidad de crear clases anónimas o implementaciones explícitas para interfaces funcionales.

### Sintaxis de una Expresión Lambda

La sintaxis general de una expresión lambda es:

```java
(parámetros) -> { cuerpo }
```

- **`parámetros`**: La lista de parámetros que el método de la interfaz funcional acepta. Puede ser una lista vacía, un solo parámetro (sin paréntesis) o varios parámetros (con paréntesis).
- **`->`**: El operador lambda que separa la lista de parámetros del cuerpo.
- **`cuerpo`**: El bloque de código que implementa el método de la interfaz funcional. Puede ser una sola expresión o un bloque de código.

#### Ejemplos

1. **Expresión Lambda con una sola expresión**

```java
// Interfaz funcional
@FunctionalInterface
interface Operacion {
    int aplicar(int a, int b);
}

// Uso de expresión lambda
Operacion suma = (a, b) -> a + b;
System.out.println(suma.aplicar(5, 3)); // Imprime 8
```

2. **Expresión Lambda con un bloque de código**

```java
// Interfaz funcional
@FunctionalInterface
interface Mensaje {
    void mostrar(String mensaje);
}

// Uso de expresión lambda
Mensaje mostrarMensaje = (mensaje) -> {
    System.out.println("Mensaje: " + mensaje);
};
mostrarMensaje.mostrar("Hola Mundo"); // Imprime "Mensaje: Hola Mundo"
```

3. **Expresión Lambda con un solo parámetro (sin paréntesis)**

```java
// Interfaz funcional
@FunctionalInterface
interface Saludo {
    void saludar(String nombre);
}

// Uso de expresión lambda
Saludo saludo = nombre -> System.out.println("Hola, " + nombre);
saludo.saludar("Juan"); // Imprime "Hola, Juan"
```

4. **Expresión Lambda con múltiples parámetros**

```java
// Interfaz funcional
@FunctionalInterface
interface Comparador {
    boolean comparar(String a, String b);
}

// Uso de expresión lambda
Comparador esIgual = (a, b) -> a.equals(b);
System.out.println(esIgual.comparar("hola", "hola")); // Imprime true
```

## Consideraciones

- **Tipos de Parámetros**: Si hay un solo parámetro y su tipo se puede inferir, los paréntesis pueden omitirse. Si hay más de un parámetro, los paréntesis son obligatorios.
- **Tipo de Retorno**: En el caso de una sola expresión, el tipo de retorno se infiere automáticamente. Si el cuerpo es un bloque de código, es necesario usar `return` para especificar el valor de retorno.
- **Ámbito**: Las expresiones lambda pueden acceder a variables locales efectivamente finales (es decir, variables cuyo valor no cambia después de ser inicializado) y a variables de instancia de la clase que contiene la expresión lambda.

## Conclusión

Las expresiones lambda en Java simplifican el trabajo con interfaces funcionales y permiten escribir código más limpio y expresivo. Su sintaxis compacta y su integración con la API de Streams y otras funcionalidades de Java 8 y posteriores facilitan la programación funcional y el procesamiento de datos en paralelo.
