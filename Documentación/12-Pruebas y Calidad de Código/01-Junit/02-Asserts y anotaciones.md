# Aserciones y Anotaciones en JUnit

## Aserciones

Las aserciones en JUnit se utilizan para verificar si los resultados obtenidos en las pruebas coinciden con los resultados esperados. JUnit proporciona varias aserciones para diferentes tipos de comparaciones y validaciones.

### Tipos de Aserciones

1. **`assertEquals(expected, actual)`**

   Verifica que el valor esperado sea igual al valor real.

   #### Ejemplo

   ```java
   import static org.junit.jupiter.api.Assertions.assertEquals;

   @Test
   void testAdd() {
       Calculator calculator = new Calculator();
       int result = calculator.add(2, 3);
       assertEquals(5, result, "La suma de dos números debería ser correcta.");
   }
   ```

2. **`assertNotEquals(expected, actual)`**

   Verifica que el valor esperado no sea igual al valor real.

   #### Ejemplo

   ```java
   import static org.junit.jupiter.api.Assertions.assertNotEquals;

   @Test
   void testSubtract() {
       Calculator calculator = new Calculator();
       int result = calculator.subtract(5, 3);
       assertNotEquals(1, result, "La resta de dos números no debería dar el valor 1.");
   }
   ```

3. **`assertTrue(condition)`**

   Verifica que la condición dada sea verdadera.

   #### Ejemplo

   ```java
   import static org.junit.jupiter.api.Assertions.assertTrue;

   @Test
   void testIsEven() {
       Calculator calculator = new Calculator();
       boolean result = calculator.isEven(4);
       assertTrue(result, "El número debería ser par.");
   }
   ```

4. **`assertFalse(condition)`**

   Verifica que la condición dada sea falsa.

   #### Ejemplo

   ```java
   import static org.junit.jupiter.api.Assertions.assertFalse;

   @Test
   void testIsOdd() {
       Calculator calculator = new Calculator();
       boolean result = calculator.isOdd(4);
       assertFalse(result, "El número no debería ser impar.");
   }
   ```

5. **`assertNull(actual)`**

   Verifica que el valor real sea `null`.

   #### Ejemplo

   ```java
   import static org.junit.jupiter.api.Assertions.assertNull;

   @Test
   void testGetNull() {
       Calculator calculator = new Calculator();
       Object result = calculator.getNullObject();
       assertNull(result, "El objeto debería ser nulo.");
   }
   ```

6. **`assertNotNull(actual)`**

   Verifica que el valor real no sea `null`.

   #### Ejemplo

   ```java
   import static org.junit.jupiter.api.Assertions.assertNotNull;

   @Test
   void testGetNonNull() {
       Calculator calculator = new Calculator();
       Object result = calculator.getNonNullObject();
       assertNotNull(result, "El objeto no debería ser nulo.");
   }
   ```

7. **`assertThrows(expectedType, executable)`**

   Verifica que se lance una excepción del tipo esperado.

   #### Ejemplo

   ```java
   import static org.junit.jupiter.api.Assertions.assertThrows;

   @Test
   void testDivideByZero() {
       Calculator calculator = new Calculator();
       assertThrows(ArithmeticException.class, () -> {
           calculator.divide(1, 0);
       }, "Debería lanzar ArithmeticException.");
   }
   ```

## Anotaciones

JUnit utiliza varias anotaciones para definir el comportamiento de las pruebas y la configuración del entorno de prueba.

### Anotaciones Comunes

1. **`@Test`**

   Marca un método como un método de prueba que debe ser ejecutado por el framework JUnit.

   #### Ejemplo

   ```java
   import org.junit.jupiter.api.Test;

   public class CalculatorTest {

       @Test
       void testAddition() {
           // Test logic here
       }
   }
   ```

2. **`@BeforeEach`**

   Se ejecuta antes de cada método de prueba. Se utiliza para configurar el entorno antes de cada prueba.

   #### Ejemplo

   ```java
   import org.junit.jupiter.api.BeforeEach;

   public class CalculatorTest {

       private Calculator calculator;

       @BeforeEach
       void setUp() {
           calculator = new Calculator();
       }
   }
   ```

3. **`@AfterEach`**

   Se ejecuta después de cada método de prueba. Se utiliza para limpiar el entorno después de cada prueba.

   #### Ejemplo

   ```java
   import org.junit.jupiter.api.AfterEach;

   public class CalculatorTest {

       private Calculator calculator;

       @AfterEach
       void tearDown() {
           calculator = null;
       }
   }
   ```

4. **`@BeforeAll`**

   Se ejecuta una vez antes de todas las pruebas en la clase. Se utiliza para configurar recursos que se comparten entre todas las pruebas.

   #### Ejemplo

   ```java
   import org.junit.jupiter.api.BeforeAll;

   public class CalculatorTest {

       @BeforeAll
       static void initAll() {
           // Initialize shared resources here
       }
   }
   ```

5. **`@AfterAll`**

   Se ejecuta una vez después de todas las pruebas en la clase. Se utiliza para limpiar recursos compartidos.

   #### Ejemplo

   ```java
   import org.junit.jupiter.api.AfterAll;

   public class CalculatorTest {

       @AfterAll
       static void tearDownAll() {
           // Clean up shared resources here
       }
   }
   ```

6. **`@Disabled`**

   Marca un método de prueba o una clase como deshabilitado, es decir, no se ejecutará.

   #### Ejemplo

   ```java
   import org.junit.jupiter.api.Disabled;
   import org.junit.jupiter.api.Test;

   public class CalculatorTest {

       @Disabled
       @Test
       void testDisabled() {
           // This test will not run
       }
   }
   ```

7. **`@ParameterizedTest`**

   Se utiliza para ejecutar el mismo test con diferentes conjuntos de datos. Permite pruebas parametrizadas.

   #### Ejemplo

   ```java
   import org.junit.jupiter.params.ParameterizedTest;
   import org.junit.jupiter.params.provider.ValueSource;

   public class NumberTest {

       @ParameterizedTest
       @ValueSource(ints = {1, 2, 3, 4, 5})
       void testIsPositive(int number) {
           assertTrue(number > 0, "El número debería ser positivo.");
       }
   }
   ```

## Conclusión

Las aserciones y anotaciones en JUnit proporcionan un marco robusto para escribir y organizar pruebas unitarias en Java. Las aserciones permiten verificar el comportamiento esperado de tu código, mientras que las anotaciones facilitan la configuración y el control del entorno de prueba. Utilizar estas herramientas de manera efectiva te ayudará a mantener la calidad y la confiabilidad de tus aplicaciones.
