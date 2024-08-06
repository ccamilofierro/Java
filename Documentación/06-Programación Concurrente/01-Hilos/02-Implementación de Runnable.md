# Implementación de `Runnable` en Java

## Introducción

En Java, la interfaz `Runnable` es una forma de crear y manejar hilos de manera flexible. Implementar `Runnable` permite que una clase se concentre en realizar una tarea específica sin necesidad de extender la clase `Thread`. Esto es útil cuando se desea que una clase extienda otra clase además de ejecutar código en un hilo separado.

## Implementación de `Runnable`

Para utilizar la interfaz `Runnable`, debes seguir estos pasos:

1. **Implementar la Interfaz `Runnable`**: Crea una clase que implemente la interfaz `Runnable` y sobreescribe su método `run()`, que contiene el código que se ejecutará en el hilo.

2. **Crear un Objeto `Thread`**: Pasa una instancia de tu clase `Runnable` a un objeto `Thread`.

3. **Iniciar el Hilo**: Llama al método `start()` del objeto `Thread` para comenzar la ejecución del hilo.

### Ejemplo de Implementación de `Runnable`

#### Definición de la Clase `Runnable`

```java
public class MiTarea implements Runnable {
    @Override
    public void run() {
        // Código que se ejecutará en el nuevo hilo
        for (int i = 0; i < 5; i++) {
            System.out.println("Hilo en ejecución: " + i);
            try {
                Thread.sleep(1000); // Pausa el hilo por 1 segundo
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }
}
```

#### Creación y Ejecución del Hilo

```java
public class EjemploRunnable {
    public static void main(String[] args) {
        // Crear una instancia de MiTarea
        MiTarea tarea = new MiTarea();
        
        // Crear un objeto Thread con la instancia de MiTarea
        Thread hilo = new Thread(tarea);
        
        // Iniciar el hilo
        hilo.start();
    }
}
```

## Ventajas de Usar `Runnable`

- **Flexibilidad**: Permite que una clase extienda otra clase además de implementar `Runnable`, ya que no se requiere heredar de `Thread`.
- **Separación de Responsabilidades**: Mantiene el código de la tarea separada de la lógica de gestión del hilo.
- **Reusabilidad**: Puedes reutilizar la misma instancia de `Runnable` en diferentes hilos si es necesario.

## Ejemplo Adicional: Múltiples Hilos con `Runnable`

Puedes crear múltiples hilos a partir de la misma instancia de `Runnable` o instancias diferentes, permitiendo la ejecución concurrente de múltiples tareas.

```java
public class EjemploMultiplesHilos {
    public static void main(String[] args) {
        Runnable tarea = () -> {
            for (int i = 0; i < 5; i++) {
                System.out.println("Hilo en ejecución: " + i);
                try {
                    Thread.sleep(1000);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
        };

        // Crear y iniciar varios hilos
        Thread hilo1 = new Thread(tarea);
        Thread hilo2 = new Thread(tarea);
        Thread hilo3 = new Thread(tarea);

        hilo1.start();
        hilo2.start();
        hilo3.start();
    }
}
```

## Conclusión

La interfaz `Runnable` en Java proporciona una forma flexible y eficiente para crear y gestionar hilos. Al implementar `Runnable`, puedes concentrarte en la tarea que debe ejecutarse en el hilo sin tener que preocuparte por la gestión del hilo directamente. Esto permite una mejor organización del código y una mayor reutilización de las tareas.
