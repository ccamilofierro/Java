# Sobrecarga de Métodos en Java

## Concepto de Sobrecarga de Métodos
La sobrecarga de métodos en Java permite definir múltiples métodos con el mismo nombre en una clase, pero con diferentes listas de parámetros. Esto facilita la creación de métodos que realizan tareas similares pero con diferentes tipos o números de argumentos.

### Reglas de Sobrecarga
1. **Nombre del Método**: Los métodos sobrecargados deben tener el mismo nombre.
2. **Lista de Parámetros**: Los métodos deben tener diferentes listas de parámetros, es decir, el número, tipo o el orden de los parámetros debe ser diferente.
3. **Tipo de Retorno**: El tipo de retorno no se considera en la sobrecarga, por lo que no es suficiente solo cambiar el tipo de retorno para sobrecargar un método.

### Sintaxis
```java
modificador_de_acceso tipo_de_retorno nombre_del_metodo(tipo_parametro1 nombre_parametro1, tipo_parametro2 nombre_parametro2, ...) {
    // Código a ejecutar
}
```

### Ejemplo de Sobrecarga de Métodos
```java
public class EjemploSobrecarga {

    // Método con un parámetro int
    public void mostrar(int a) {
        System.out.println("Número entero: " + a);
    }

    // Método con un parámetro String
    public void mostrar(String mensaje) {
        System.out.println("Mensaje: " + mensaje);
    }

    // Método con dos parámetros: un int y un String
    public void mostrar(int a, String mensaje) {
        System.out.println("Número entero: " + a + " - Mensaje: " + mensaje);
    }

    public static void main(String[] args) {
        EjemploSobrecarga obj = new EjemploSobrecarga();
        obj.mostrar(10);                // Llama al método con un parámetro int
        obj.mostrar("Hola");            // Llama al método con un parámetro String
        obj.mostrar(10, "Hola");        // Llama al método con dos parámetros
    }
}
```

En este ejemplo, el método `mostrar` está sobrecargado para aceptar diferentes combinaciones de parámetros (`int`, `String`, y ambos). Dependiendo de los argumentos proporcionados al método, se llamará a la versión adecuada del método.

## Beneficios de la Sobrecarga
- **Claridad del Código**: Permite usar el mismo nombre de método para operaciones similares, mejorando la legibilidad del código.
- **Flexibilidad**: Permite crear métodos que manejan diferentes tipos o números de argumentos, facilitando la reutilización del código.

## Consideraciones
- **No Confundir con Sobrescritura**: La sobrecarga de métodos no debe confundirse con la sobrescritura de métodos (overriding), donde un método en una clase derivada reemplaza un método con el mismo nombre en la clase base.
- **Evitar Ambigüedad**: Asegúrate de que la sobrecarga no cause ambigüedad, especialmente si los métodos tienen firmas similares pero no idénticas.

La sobrecarga de métodos es una característica poderosa en Java que te permite diseñar APIs más flexibles y manejables.
