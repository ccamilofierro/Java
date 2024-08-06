# Mocking y Stubbing en Pruebas Unitarias

## Introducción

En las pruebas unitarias, el mocking y el stubbing son técnicas utilizadas para simular el comportamiento de objetos dependientes, lo que permite aislar la unidad de código que se está probando. Estas técnicas ayudan a verificar el comportamiento del código en diferentes escenarios y a mejorar la fiabilidad y la cobertura de las pruebas.

## Stubbing

El stubbing se refiere a la creación de objetos simulados (stubs) que devuelven resultados predefinidos para llamadas de métodos. Se utiliza para controlar el comportamiento de los objetos dependientes y proporcionar datos específicos a las pruebas.

### Ejemplo de Stubbing

Supongamos que tienes una clase `Service` que depende de un repositorio `Repository`. Puedes usar stubbing para definir el comportamiento del repositorio durante las pruebas.

#### Configuración del Entorno

Asegúrate de incluir una librería de mocking como Mockito en tu proyecto.

### Ejemplo con Mockito

```xml
<dependency>
    <groupId>org.mockito</groupId>
    <artifactId>mockito-core</artifactId>
    <version>4.8.0</version>
    <scope>test</scope>
</dependency>
```

#### Código de Ejemplo

```java
import static org.mockito.Mockito.*;
import static org.junit.jupiter.api.Assertions.assertEquals;

public class ServiceTest {

    @Test
    void testServiceWithStubbedRepository() {
        // Crear un mock del repositorio
        Repository mockRepository = mock(Repository.class);

        // Configurar el comportamiento del mock
        when(mockRepository.findById(1)).thenReturn(new Item("Test Item"));

        // Inyectar el mock en el servicio
        Service service = new Service(mockRepository);

        // Ejecutar la prueba
        Item result = service.getItem(1);
        assertEquals("Test Item", result.getName());
    }
}
```

En este ejemplo, el `Repository` es simulado con un stub que devuelve un `Item` específico cuando se llama al método `findById`.

## Mocking

El mocking se refiere a la creación de objetos simulados (mocks) que permiten verificar cómo se interactúa con ellos. Se utiliza para comprobar que se están realizando las interacciones esperadas entre objetos, como llamadas a métodos y la cantidad de veces que se han llamado.

### Ejemplo de Mocking

#### Código de Ejemplo

```java
import static org.mockito.Mockito.*;
import static org.junit.jupiter.api.Assertions.assertTrue;

public class ServiceTest {

    @Test
    void testServiceWithMocking() {
        // Crear un mock del repositorio
        Repository mockRepository = mock(Repository.class);

        // Configurar el comportamiento del mock
        when(mockRepository.findById(1)).thenReturn(new Item("Test Item"));

        // Inyectar el mock en el servicio
        Service service = new Service(mockRepository);

        // Ejecutar la prueba
        service.processItem(1);

        // Verificar la interacción con el mock
        verify(mockRepository).findById(1);
    }
}
```

En este ejemplo, se crea un mock del `Repository` y se verifica que el método `findById` sea llamado con el parámetro `1` durante la ejecución del método `processItem` del servicio.

## Diferencias entre Stubbing y Mocking

- **Stubbing**: Se centra en definir el comportamiento de los métodos de los objetos simulados. Se usa para proporcionar respuestas predefinidas a las llamadas de métodos.
- **Mocking**: Se centra en verificar las interacciones con los objetos simulados. Se usa para asegurarse de que ciertos métodos sean llamados con los parámetros esperados y en la cantidad de veces esperada.

## Herramientas para Mocking y Stubbing

Las principales librerías para mocking y stubbing en Java son:

- **Mockito**: Es una de las librerías más populares para mocking y stubbing en pruebas unitarias en Java. Permite crear mocks, stubs y verificar interacciones de manera sencilla.
- **EasyMock**: Otra librería para mocking y stubbing que proporciona una API similar a Mockito.
- **JMockit**: Ofrece funcionalidades avanzadas para mocking y stubbing, así como para la creación de objetos espías.

## Conclusión

El mocking y el stubbing son técnicas esenciales en el desarrollo de pruebas unitarias que te permiten aislar las unidades de código y controlar sus dependencias. Utilizando herramientas como Mockito, puedes crear pruebas más robustas y verificar el comportamiento de tu código de manera efectiva.
