# Bloques Sincronizados en Java

## Introducción

En Java, la sincronización es esencial para gestionar el acceso concurrente a recursos compartidos entre múltiples hilos. Los bloques sincronizados permiten que solo un hilo a la vez ejecute un bloque de código específico, garantizando así que los recursos compartidos no se corrompan o se accedan de manera inconsistente.

## ¿Qué es un Bloque Sincronizado?

Un bloque sincronizado en Java es una sección de código que se ejecuta bajo el control de un monitor. Cuando un hilo entra en un bloque sincronizado, adquiere un bloqueo sobre un objeto específico (el objeto monitor), y ningún otro hilo puede ejecutar un bloque sincronizado en el mismo objeto hasta que el primer hilo haya salido.

### Sintaxis de un Bloque Sincronizado

```java
synchronized (objeto) {
    // Código que se ejecuta de manera sincronizada
}
```

- `objeto`: El objeto sobre el cual se adquiere el bloqueo. Todos los bloques sincronizados que usan el mismo objeto compartirán el mismo monitor.

## Ejemplo de Uso de Bloques Sincronizados

#### Ejemplo Básico

```java
public class Contador {
    private int cuenta = 0;

    public void incrementar() {
        synchronized (this) {
            cuenta++;
        }
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

En este ejemplo, el método `incrementar()` está protegido por un bloque sincronizado que utiliza el objeto `this` como monitor. Esto asegura que solo un hilo pueda incrementar la cuenta a la vez.

## ¿Por qué Usar Bloques Sincronizados?

- **Evitar Condiciones de Carrera**: Los bloques sincronizados previenen que múltiples hilos modifiquen un recurso compartido simultáneamente, evitando inconsistencias y errores.
- **Garantizar la Atomicidad**: Aseguran que una serie de operaciones se realicen de manera atómica, es decir, que se completen sin interrupciones por otros hilos.
- **Controlar el Acceso a Recursos Compartidos**: Permiten coordinar el acceso a recursos críticos para evitar conflictos y garantizar que se realicen correctamente.

## Consideraciones

- **Bloqueo de Objetos**: Los bloques sincronizados utilizan el objeto monitor para controlar el acceso. Asegúrate de que los objetos utilizados como monitores no cambien durante la sincronización.
- **Rendimiento**: El uso excesivo de sincronización puede afectar el rendimiento debido al tiempo que los hilos pasan esperando el bloqueo.
- **Granularidad**: Utiliza la sincronización de manera granular para minimizar el tiempo durante el cual el bloqueo está en efecto, reduciendo así el impacto en el rendimiento.

## Conclusión

Los bloques sincronizados en Java son una herramienta fundamental para manejar la concurrencia y garantizar la integridad de los datos en aplicaciones multihilo. Al usar sincronización, puedes controlar el acceso a recursos compartidos y evitar problemas como las condiciones de carrera, asegurando que las operaciones sobre datos compartidos se realicen de manera segura y consistente.
