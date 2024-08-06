# Parámetros y Valores de Retorno en Métodos de Java

## Parámetros
Los parámetros son valores que se pasan a un método para que pueda utilizarlos en su procesamiento. Los parámetros permiten que un método trabaje con diferentes datos cada vez que se llama.

### Sintaxis para Parámetros
```java
modificador_de_acceso tipo_de_retorno nombre_del_metodo(tipo_parametro nombre_parametro, tipo_parametro2 nombre_parametro2, ...) {
    // Código a ejecutar
}
```

### Ejemplo
```java
public class Calculadora {
    public int sumar(int a, int b) {
        return a + b;
    }

    public static void main(String[] args) {
        Calculadora calc = new Calculadora();
        int resultado = calc.sumar(5, 3);
        System.out.println("El resultado de la suma es: " + resultado);
    }
}
```

En este ejemplo, el método `sumar` recibe dos parámetros (`a` y `b`) de tipo `int`. Estos parámetros se utilizan dentro del método para calcular la suma de dos números.

## Valores de Retorno
Los valores de retorno son los resultados que un método devuelve al código que lo llamó. El tipo de retorno especifica el tipo de dato que el método devuelve.

### Sintaxis para Valores de Retorno
```java
tipo_de_retorno nombre_del_metodo(parametros) {
    // Código a ejecutar
    return valor_de_retorno;
}
```

### Ejemplo
```java
public class Calculadora {
    public int multiplicar(int a, int b) {
        return a * b;
    }

    public static void main(String[] args) {
        Calculadora calc = new Calculadora();
        int resultado = calc.multiplicar(4, 5);
        System.out.println("El resultado de la multiplicación es: " + resultado);
    }
}
```

En este ejemplo, el método `multiplicar` devuelve el producto de `a` y `b`. El valor retornado se almacena en la variable `resultado` y se imprime en la consola.

## Métodos sin Valores de Retorno
Si un método no necesita devolver ningún valor, se declara con el tipo de retorno `void`. En este caso, el método simplemente realiza una acción sin devolver un resultado.

### Ejemplo
```java
public class Mensajero {
    public void mostrarMensaje(String mensaje) {
        System.out.println(mensaje);
    }

    public static void main(String[] args) {
        Mensajero mensajero = new Mensajero();
        mensajero.mostrarMensaje("Hola, Mundo!");
    }
}
```

En este ejemplo, el método `mostrarMensaje` imprime el mensaje proporcionado en la consola, pero no devuelve ningún valor.

## Consideraciones Adicionales
- **Parámetros por Valor**: En Java, los parámetros se pasan por valor, lo que significa que se pasa una copia del valor al método. Los cambios realizados en los parámetros dentro del método no afectan a las variables originales.
- **Parámetros por Referencia**: Aunque Java no soporta parámetros por referencia directamente, puedes simular este comportamiento utilizando objetos. Los objetos se pasan por referencia, lo que significa que las modificaciones en los objetos dentro del método afectan al objeto original.

Estos conceptos son fundamentales para la creación de métodos en Java, permitiendo que tus métodos sean más flexibles y reutilizables.
