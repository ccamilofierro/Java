# Sobreescritura de Métodos en Java

## Introducción
La sobrescritura de métodos (method overriding) en Java es un mecanismo que permite a una subclase proporcionar una implementación específica de un método que ya está definido en su clase base. Esto es una característica fundamental de la herencia en la programación orientada a objetos y permite a las subclases definir o modificar el comportamiento de métodos heredados.

## Reglas de Sobreescritura

1. **Firma del Método**: El método sobrescrito en la subclase debe tener la misma firma (nombre, tipo de retorno y parámetros) que el método en la clase base.
2. **Modificadores de Acceso**: El modificador de acceso del método sobrescrito debe ser el mismo o más accesible que el del método en la clase base. Por ejemplo, un método `protected` en la clase base puede ser sobrescrito como `protected` o `public` en la subclase, pero no puede ser `private`.
3. **Tipo de Retorno**: El tipo de retorno del método sobrescrito debe ser el mismo o un subtipo del tipo de retorno del método en la clase base.
4. **Excepciones**: El método sobrescrito no puede lanzar nuevas excepciones que no sean lanzadas por el método en la clase base. Puede lanzar las mismas excepciones o una excepción más específica.

## Sintaxis de la Sobreescritura

### Ejemplo de Sobreescritura de Métodos
```java
// Clase base
public class Animal {
    public void hacerSonido() {
        System.out.println("El animal hace un sonido.");
    }
}

// Clase derivada
public class Gato extends Animal {
    @Override
    public void hacerSonido() {
        System.out.println("El gato maúlla.");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal miAnimal = new Gato();
        miAnimal.hacerSonido(); // Salida: El gato maúlla.
    }
}
```

En este ejemplo, la clase `Gato` sobrescribe el método `hacerSonido` de la clase base `Animal`. Cuando se llama al método `hacerSonido` en una instancia de `Gato`, se ejecuta la implementación de `Gato`, no la de `Animal`.

## Uso de la Anotación `@Override`

### ¿Qué es `@Override`?
La anotación `@Override` se utiliza para indicar que un método en una subclase está sobrescribiendo un método de la clase base. Aunque no es estrictamente necesario, usar `@Override` es una buena práctica ya que ayuda a detectar errores en tiempo de compilación, como cuando un método en la subclase no coincide con la firma del método en la clase base.

#### Ejemplo de Uso de `@Override`
```java
public class Animal {
    public void hacerSonido() {
        System.out.println("El animal hace un sonido.");
    }
}

public class Gato extends Animal {
    @Override
    public void hacerSonido() {
        System.out.println("El gato maúlla.");
    }
}
```

En este ejemplo, `@Override` se coloca antes del método `hacerSonido` en la clase `Gato` para indicar que este método está sobrescribiendo el método de la clase base `Animal`.

## Consideraciones Adicionales

- **Polimorfismo**: La sobrescritura de métodos es una forma de polimorfismo. Permite que un método en la clase base sea invocado a través de una referencia de la clase base, pero que ejecute la implementación de la subclase.
- **Invocación del Método Base**: Dentro de la implementación del método sobrescrito, puedes usar la palabra clave `super` para llamar al método de la clase base si es necesario.
- **Métodos Estáticos**: Los métodos estáticos no se pueden sobrescribir. Si una subclase define un método estático con el mismo nombre y firma que el método estático en la clase base, se considera una ocultación de métodos (method hiding), no una sobrescritura.

La sobrescritura de métodos permite que las subclases modifiquen o extiendan el comportamiento de métodos heredados, facilitando la personalización y el ajuste del comportamiento de las clases base.
