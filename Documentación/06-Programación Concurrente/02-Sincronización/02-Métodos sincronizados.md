# Métodos Sincronizados en Java

## Introducción

En Java, los métodos sincronizados proporcionan una manera de asegurar que solo un hilo a la vez pueda acceder a un método específico de un objeto. Esto es útil para proteger los datos compartidos en un entorno multihilo y evitar condiciones de carrera.

## ¿Qué es un Método Sincronizado?

Un método sincronizado es un método que se ejecuta bajo el control de un monitor. Cuando un hilo llama a un método sincronizado, adquiere un bloqueo sobre el objeto que invoca el método (en el caso de métodos de instancia) o sobre la clase (en el caso de métodos estáticos). Mientras un hilo tiene este bloqueo, otros hilos no pueden ejecutar ningún otro método sincronizado en el mismo objeto o clase hasta que el bloqueo sea liberado.

### Sintaxis de un Método Sincronizado

#### Método de Instancia

```java
public synchronized void metodoSincronizado() {
    // Código que se ejecuta de manera sincronizada
}
```

#### Método Estático

```java
public static synchronized void metodoSincronizadoEstatico() {
    // Código que se ejecuta de manera sincronizada
}
```

- **Método de Instancia**: Sincroniza sobre el objeto actual (`this`). Solo un hilo puede ejecutar un método sincronizado en un objeto en particular a la vez.
- **Método Estático**: Sincroniza sobre la clase (el objeto `Class` asociado a la clase). Solo un hilo puede ejecutar un método sincronizado estático en una clase a la vez.

## Ejemplo de Uso de Métodos Sincronizados

#### Ejemplo Básico

```java
public class Contador {
    private int cuenta = 0;

    public synchronized void incrementar() {
        cuenta++;
    }

    public synchronized int getCuenta() {
        return cuenta;
    }

    public static synchronized void metodoEstatico() {
        // Código para método sincronizado estático
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

En este ejemplo, los métodos `incrementar()` y `getCuenta()` están sincronizados. Esto asegura que solo un hilo pueda incrementar la cuenta o obtener el valor de la cuenta a la vez.

## ¿Por qué Usar Métodos Sincronizados?

- **Protección de Datos**: Garantizan que los datos compartidos se modifiquen de manera segura, evitando que múltiples hilos accedan o modifiquen los mismos datos simultáneamente.
- **Simplicidad**: Facilitan la sincronización al permitir que la lógica de sincronización se defina a nivel de método, sin necesidad de usar bloques sincronizados manualmente.

## Consideraciones

- **Bloqueo de Objetos**: Los métodos sincronizados utilizan el objeto monitor para controlar el acceso. Los métodos sincronizados estáticos utilizan el monitor de la clase, mientras que los métodos de instancia utilizan el monitor del objeto.
- **Rendimiento**: La sincronización puede afectar el rendimiento si no se utiliza adecuadamente, ya que puede causar que los hilos se bloqueen y esperen.
- **Granularidad**: La sincronización de métodos puede ser menos flexible que los bloques sincronizados, ya que se aplica a todo el método. En algunos casos, puede ser más eficiente sincronizar solo las secciones críticas del código.

## Conclusión

Los métodos sincronizados en Java proporcionan una forma sencilla y efectiva para manejar la sincronización en aplicaciones multihilo. Al asegurar que solo un hilo pueda acceder a un método específico a la vez, puedes proteger los datos compartidos y evitar problemas como las condiciones de carrera, asegurando la integridad y consistencia de la aplicación.
