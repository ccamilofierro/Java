# Ejecución de Sentencias SQL en Java

## Introducción

La ejecución de sentencias SQL en Java se realiza principalmente mediante JDBC (Java Database Connectivity). JDBC proporciona una interfaz estándar para interactuar con bases de datos relacionales y ejecutar consultas SQL. Este documento describe los pasos básicos para ejecutar sentencias SQL, incluyendo consultas SELECT, INSERT, UPDATE y DELETE.

## Configuración Inicial

Antes de ejecutar sentencias SQL, debes establecer una conexión con la base de datos. Esto incluye cargar el driver JDBC, establecer la conexión y crear un objeto `Statement` o `PreparedStatement` para ejecutar las consultas.

### Ejemplo de Configuración Inicial

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

public class ConexionBD {
    public static Connection obtenerConexion() throws SQLException {
        String url = "jdbc:mysql://localhost:3306/mi_base_de_datos";
        String usuario = "root";
        String contrasena = "mi_contrasena";

        // Cargar el driver JDBC
        try {
            Class.forName("com.mysql.cj.jdbc.Driver");
        } catch (ClassNotFoundException e) {
            e.printStackTrace();
        }

        // Establecer la conexión
        return DriverManager.getConnection(url, usuario, contrasena);
    }
}
```

## Consultas SELECT

Las consultas SELECT se utilizan para recuperar datos de la base de datos. Puedes ejecutar consultas SELECT utilizando el objeto `Statement` o `PreparedStatement`, y procesar los resultados con el objeto `ResultSet`.

### Ejemplo de Consulta SELECT

```java
import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.Statement;
import java.sql.SQLException;

public class ConsultaSelect {
    public static void main(String[] args) {
        try (Connection conexion = ConexionBD.obtenerConexion();
             Statement sentencia = conexion.createStatement()) {

            String sql = "SELECT * FROM empleados";
            ResultSet resultado = sentencia.executeQuery(sql);

            while (resultado.next()) {
                System.out.println("ID: " + resultado.getInt("id"));
                System.out.println("Nombre: " + resultado.getString("nombre"));
            }
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
```

## Consultas INSERT, UPDATE y DELETE

Estas consultas se utilizan para modificar los datos en la base de datos. Se ejecutan utilizando el método `executeUpdate` del objeto `Statement` o `PreparedStatement`.

### Ejemplo de Consulta INSERT

```java
import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.SQLException;

public class ConsultaInsert {
    public static void main(String[] args) {
        String sql = "INSERT INTO empleados (id, nombre) VALUES (?, ?)";

        try (Connection conexion = ConexionBD.obtenerConexion();
             PreparedStatement sentencia = conexion.prepareStatement(sql)) {

            sentencia.setInt(1, 1);
            sentencia.setString(2, "Juan Pérez");
            int filasAfectadas = sentencia.executeUpdate();

            System.out.println("Filas afectadas: " + filasAfectadas);
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
```

### Ejemplo de Consulta UPDATE

```java
import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.SQLException;

public class ConsultaUpdate {
    public static void main(String[] args) {
        String sql = "UPDATE empleados SET nombre = ? WHERE id = ?";

        try (Connection conexion = ConexionBD.obtenerConexion();
             PreparedStatement sentencia = conexion.prepareStatement(sql)) {

            sentencia.setString(1, "Ana García");
            sentencia.setInt(2, 1);
            int filasAfectadas = sentencia.executeUpdate();

            System.out.println("Filas afectadas: " + filasAfectadas);
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
```

### Ejemplo de Consulta DELETE

```java
import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.SQLException;

public class ConsultaDelete {
    public static void main(String[] args) {
        String sql = "DELETE FROM empleados WHERE id = ?";

        try (Connection conexion = ConexionBD.obtenerConexion();
             PreparedStatement sentencia = conexion.prepareStatement(sql)) {

            sentencia.setInt(1, 1);
            int filasAfectadas = sentencia.executeUpdate();

            System.out.println("Filas afectadas: " + filasAfectadas);
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
```

## Manejo de Excepciones

Es importante manejar las excepciones adecuadamente al ejecutar sentencias SQL. Las excepciones más comunes son `SQLException`, que se produce cuando ocurre un error en la base de datos, y `ClassNotFoundException`, que se produce si el driver JDBC no se encuentra.

### Ejemplo de Manejo de Excepciones

```java
try {
    // Código para ejecutar consultas SQL
} catch (SQLException e) {
    System.err.println("Error en la base de datos: " + e.getMessage());
} catch (ClassNotFoundException e) {
    System.err.println("Driver no encontrado: " + e.getMessage());
}
```

## Conclusión

La ejecución de sentencias SQL en Java mediante JDBC es fundamental para interactuar con bases de datos relacionales. Al utilizar las clases `Statement`, `PreparedStatement`, y `ResultSet`, puedes realizar operaciones de consulta y modificación de datos. Asegúrate de manejar las excepciones adecuadamente y cerrar los recursos para evitar fugas de memoria y otros problemas.
