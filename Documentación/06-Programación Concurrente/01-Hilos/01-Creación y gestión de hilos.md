# Creación y Gestión de Hilos en Java

## Introducción

En Java, los hilos (o threads) permiten la ejecución concurrente de múltiples tareas. La programación multihilo es útil para mejorar el rendimiento de aplicaciones al aprovechar la capacidad de procesamiento de varios núcleos de CPU y para realizar tareas simultáneas sin bloquear el hilo principal de la aplicación. Java proporciona varias formas de crear y gestionar hilos.

## Creación de Hilos

### Usando la Clase `Thread`

Una forma de crear un hilo en Java es extendiendo la clase `Thread` y sobrescribiendo su método `run()`. Luego, se puede crear una instancia de esta clase y llamar al método `start()` para iniciar el hilo.

#### Ejemplo de Uso de `Thread`

```java
public class MiHilo extends Thread {
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

    public static void main(String[] args) {
        MiHilo hilo = new MiHilo();
        hilo.start(); // Inicia el nuevo hilo
    }
}
```

### Usando la Interfaz `Runnable`

Otra forma de crear un hilo es implementando la interfaz `Runnable` y pasando una instancia de esta implementación a un objeto `Thread`. Este enfoque es más flexible y permite que una clase extienda otra clase además de implementar `Runnable`.

#### Ejemplo de Uso de `Runnable`

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

    public static void main(String[] args) {
        Thread hilo = new Thread(new MiTarea());
        hilo.start(); // Inicia el nuevo hilo
    }
}
```

## Gestión de Hilos

### Control de Hilos

- **`start()`**: Inicia la ejecución del hilo.
- **`sleep(long millis)`**: Pausa la ejecución del hilo durante un tiempo especificado en milisegundos.
- **`join()`**: Espera a que el hilo termine su ejecución antes de continuar con el hilo actual.
- **`interrupt()`**: Interrumpe un hilo que está en espera, sueño o bloqueo, lanzando una `InterruptedException`.

#### Ejemplo de Uso de `join()`

```java
public class EjemploJoin {
    public static void main(String[] args) {
        Thread hilo1 = new Thread(() -> {
            for (int i = 0; i < 5; i++) {
                System.out.println("Hilo 1 en ejecución: " + i);
                try {
                    Thread.sleep(1000);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
        });

        Thread hilo2 = new Thread(() -> {
            for (int i = 0; i < 5; i++) {
                System.out.println("Hilo 2 en ejecución: " + i);
                try {
                    Thread.sleep(1000);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
        });

        hilo1.start();
        hilo2.start();

        try {
            hilo1.join(); // Espera a que hilo1 termine
            hilo2.join(); // Espera a que hilo2 termine
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        System.out.println("Todos los hilos han terminado.");
    }
}
```

### Sincronización

Cuando varios hilos acceden a recursos compartidos, puede haber problemas de concurrencia. La sincronización garantiza que solo un hilo pueda acceder a un recurso compartido a la vez.

#### Ejemplo de Sincronización

```java
public class Contador {
    private int cuenta = 0;

    public synchronized void incrementar() {
        cuenta++;
    }

    public int getCuenta() {
        return cuenta;
    }

    public static void main(String[] args) {
        Contador contador = new Contador();

        Runnable tarea = () -> {
            for (int i = 0; i < 1000; i++) {
                contador.incrementar();
            }
        };

        Thread hilo1 = new Thread(tarea);
        Thread hilo2 = new Thread(tarea);

        hilo1.start();
        hilo2.start();

        try {
            hilo1.join();
            hilo2.join();
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        System.out.println("Cuenta final: " + contador.getCuenta());
    }
}
```

## Conclusión

La creación y gestión de hilos en Java permiten realizar tareas concurrentes de manera eficiente. Al usar la clase `Thread` o la interfaz `Runnable`, puedes crear hilos para realizar trabajos simultáneos. La correcta gestión y sincronización de hilos son esenciales para evitar problemas de concurrencia y garantizar el correcto funcionamiento de las aplicaciones multihilo.
