# Uso de Mockito en Pruebas de Integración

## Introducción

Mockito es una popular librería de mocking para Java que se utiliza principalmente en pruebas unitarias para crear objetos simulados y verificar interacciones. Sin embargo, también puede ser útil en pruebas de integración, especialmente cuando se desea controlar o simular el comportamiento de ciertas dependencias externas durante la prueba de componentes integrados.

## Objetivos de Usar Mockito en Pruebas de Integración

- **Simular Comportamiento de Componentes Externos**: Utilizar mocks para simular servicios externos, bases de datos, o APIs durante las pruebas de integración.
- **Controlar el Entorno de Prueba**: Asegurarse de que las pruebas de integración se realicen en un entorno controlado, donde los mocks pueden reemplazar implementaciones reales.
- **Verificar Interacciones**: Confirmar que los componentes interactúan correctamente con los mocks y se comportan según lo esperado.

## Configuración de Mockito en Pruebas de Integración

Para usar Mockito en pruebas de integración, necesitas configurar el entorno de prueba para integrar Mockito con otras herramientas de pruebas y marcos de integración como Spring Boot.

### Ejemplo de Configuración con Spring Boot

#### Dependencias en `pom.xml`

Asegúrate de incluir las dependencias necesarias en tu archivo `pom.xml`:

```xml
<dependency>
    <groupId>org.mockito</groupId>
    <artifactId>mockito-core</artifactId>
    <version>4.8.0</version>
    <scope>test</scope>
</dependency>

<dependency>
    <groupId>org.mockito</groupId>
    <artifactId>mockito-junit-jupiter</artifactId>
    <version>4.8.0</version>
    <scope>test</scope>
</dependency>
```

### Ejemplo de Uso en una Prueba de Integración

Supongamos que tienes una aplicación Spring Boot con un servicio que depende de un repositorio. Puedes usar Mockito para simular el repositorio durante la prueba de integración del servicio.

#### Código de Ejemplo

```java
import org.junit.jupiter.api.Test;
import org.mockito.InjectMocks;
import org.mockito.Mock;
import org.mockito.junit.jupiter.MockitoExtension;
import org.springframework.boot.test.context.SpringBootTest;
import static org.mockito.Mockito.*;
import static org.junit.jupiter.api.Assertions.assertEquals;

@SpringBootTest
@ExtendWith(MockitoExtension.class)
public class IntegrationTest {

    @Mock
    private Repository mockRepository;

    @InjectMocks
    private Service service;

    @Test
    void testServiceIntegration() {
        // Configurar el comportamiento del mock
        when(mockRepository.findById(1)).thenReturn(new Item("Test Item"));

        // Ejecutar la prueba
        Item result = service.getItem(1);

        // Verificar el resultado
        assertEquals("Test Item", result.getName());
    }
}
```

En este ejemplo, `@Mock` se utiliza para crear un mock del repositorio, y `@InjectMocks` para inyectar el mock en el servicio. La prueba verifica que el servicio obtiene el ítem esperado del repositorio simulado.

## Mejoras y Consideraciones

- **Integración con Bases de Datos**: Si estás probando una aplicación que interactúa con bases de datos, considera usar `TestContainers` para proporcionar una base de datos en un contenedor, en lugar de depender solo de mocks.
- **Cobertura de Casos de Uso**: Asegúrate de que tus pruebas de integración cubran todos los casos de uso importantes y no se limiten solo a pruebas de interacción con mocks.
- **Configuración de Contexto de Prueba**: Configura adecuadamente el contexto de la prueba para asegurar que los mocks se comporten correctamente en el entorno de integración.

## Conclusión

Mockito puede ser una herramienta valiosa en las pruebas de integración, especialmente para simular y controlar dependencias externas. Utilizar Mockito de manera efectiva ayuda a asegurar que los componentes integrados funcionen correctamente juntos y que el comportamiento de las dependencias externas sea simulado de manera controlada.
