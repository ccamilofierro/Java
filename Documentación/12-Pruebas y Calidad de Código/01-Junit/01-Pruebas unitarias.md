# JUnit: Pruebas Unitarias

## Introducción a JUnit

JUnit es un framework de pruebas unitarias para Java que facilita la creación y ejecución de pruebas automatizadas. Permite a los desarrolladores verificar que su código funciona correctamente y ayuda a detectar errores de manera temprana durante el desarrollo.

## Configuración de JUnit

Para comenzar a utilizar JUnit en un proyecto Java, debes agregar la dependencia correspondiente en tu archivo de configuración del proyecto. En un proyecto Maven, se añade a `pom.xml`:

### Ejemplo de Dependencia en Maven

```xml
<dependencies>
    <dependency>
        <groupId>org.junit.jupiter</groupId>
        <artifactId>junit-jupiter-api</artifactId>
        <version>5.8.1</version>
        <scope>test</scope>
    </dependency>
    <dependency>
        <groupId>org.junit.jupiter</groupId>
        <artifactId>junit-jupiter-engine</artifactId>
        <version>5.8.1</version>
        <scope>test</scope>
    </dependency>
</dependencies>
```

## Estructura de una Prueba Unitaria

### 1. **Escribir una Clase de Prueba**

Una clase de prueba en JUnit debe estar anotada con `@Test` en cada método que desees ejecutar como una prueba. Además, puedes utilizar anotaciones adicionales como `@BeforeEach` y `@AfterEach` para configurar y limpiar el entorno de prueba.

#### Ejemplo de Clase de Prueba

```java
import org.junit.jupiter.api.AfterEach;
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.assertEquals;

public class CalculatorTest {

    private Calculator calculator;

    @BeforeEach
    void setUp() {
        calculator = new Calculator();
    }

    @AfterEach
    void tearDown() {
        calculator = null;
    }

    @Test
    void testAdd() {
        int result = calculator.add(2, 3);
        assertEquals(5, result, "The addition method should add two numbers correctly.");
    }
}
```

### 2. **Anotaciones Comunes en JUnit**

- **`@Test`**: Marca un método como un método de prueba.
- **`@BeforeEach`**: Ejecuta un método antes de cada método de prueba.
- **`@AfterEach`**: Ejecuta un método después de cada método de prueba.
- **`@BeforeAll`**: Ejecuta un método antes de todas las pruebas en la clase.
- **`@AfterAll`**: Ejecuta un método después de todas las pruebas en la clase.

### 3. **Aserciones**

Las aserciones en JUnit se utilizan para verificar los resultados esperados frente a los resultados reales. Algunas de las aserciones comunes son:

- **`assertEquals(expected, actual)`**: Verifica que dos valores sean iguales.
- **`assertNotEquals(expected, actual)`**: Verifica que dos valores no sean iguales.
- **`assertTrue(condition)`**: Verifica que una condición sea verdadera.
- **`assertFalse(condition)`**: Verifica que una condición sea falsa.

#### Ejemplo de Uso de Aserciones

```java
import static org.junit.jupiter.api.Assertions.assertTrue;

@Test
void testIsEven() {
    boolean result = calculator.isEven(4);
    assertTrue(result, "The number should be even.");
}
```

## Pruebas con Parámetros

JUnit 5 permite realizar pruebas con diferentes conjuntos de datos utilizando la anotación `@ParameterizedTest`. Puedes proporcionar los parámetros a las pruebas mediante anotaciones como `@ValueSource`, `@CsvSource`, o `@MethodSource`.

### Ejemplo de Prueba Parametrizada

```java
import org.junit.jupiter.params.ParameterizedTest;
import org.junit.jupiter.params.provider.ValueSource;

public class NumberTest {

    @ParameterizedTest
    @ValueSource(ints = {1, 2, 3, 4, 5})
    void testIsPositive(int number) {
        assertTrue(number > 0, "Number should be positive.");
    }
}
```

## Manejo de Excepciones

Puedes verificar que una excepción se lanza correctamente utilizando la anotación `@Test` con el parámetro `expected` o mediante el uso de `assertThrows`.

### Ejemplo de Verificación de Excepciones

```java
import static org.junit.jupiter.api.Assertions.assertThrows;

@Test
void testDivideByZero() {
    assertThrows(ArithmeticException.class, () -> {
        calculator.divide(1, 0);
    });
}
```

## Conclusión

JUnit es una herramienta poderosa para la realización de pruebas unitarias en Java. Su uso permite a los desarrolladores verificar la funcionalidad de su código de manera automatizada y eficaz. Con la configuración adecuada y el uso de anotaciones y aserciones, puedes crear pruebas robustas que aseguren la calidad y la fiabilidad de tus aplicaciones.
