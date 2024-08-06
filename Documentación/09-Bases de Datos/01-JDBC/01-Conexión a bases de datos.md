# Conexión a Bases de Datos en Java

## Introducción

Conectar una aplicación Java a una base de datos es una tarea común en el desarrollo de aplicaciones empresariales. Java proporciona varias formas de conectarse a bases de datos, siendo JDBC (Java Database Connectivity) el estándar principal para interactuar con bases de datos relacionales. Además, existen bibliotecas y marcos de trabajo que simplifican la interacción con las bases de datos.

## JDBC (Java Database Connectivity)

JDBC es una API estándar en Java que permite a las aplicaciones conectarse y ejecutar consultas en bases de datos. JDBC proporciona una interfaz de alto nivel para trabajar con bases de datos relacionales.

### Configuración de la Conexión

Para conectar una base de datos usando JDBC, debes seguir estos pasos básicos:

1. **Cargar el Driver JDBC**: Los drivers de JDBC permiten que tu aplicación Java se comunique con la base de datos. Debes cargar el driver correspondiente para tu base de datos.
2. **Establecer la Conexión**: Utiliza `DriverManager` para obtener una conexión a la base de datos.
3. **Crear y Ejecutar Consultas**: Usa objetos `Statement` o `PreparedStatement` para ejecutar consultas SQL.
4. **Cerrar la Conexión**: Asegúrate de cerrar la conexión y liberar los recursos después de finalizar las operaciones.

### Ejemplo de Uso de JDBC

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.Statement;
import java.sql.SQLException;

public class EjemploJDBC {
    public static void main(String[] args) {
        String url = "jdbc:mysql://localhost:3306/mi_base_de_datos";
        String usuario = "root";
        String contrasena = "mi_contrasena";

        try {
            // Cargar el driver JDBC
            Class.forName("com.mysql.cj.jdbc.Driver");

            // Establecer la conexión
            Connection conexion = DriverManager.getConnection(url, usuario, contrasena);

            // Crear una consulta
            Statement sentencia = conexion.createStatement();
            String sql = "SELECT * FROM empleados";
            ResultSet resultado = sentencia.executeQuery(sql);

            // Procesar los resultados
            while (resultado.next()) {
                System.out.println("ID: " + resultado.getInt("id"));
                System.out.println("Nombre: " + resultado.getString("nombre"));
            }

            // Cerrar recursos
            resultado.close();
            sentencia.close();
            conexion.close();
        } catch (ClassNotFoundException | SQLException e) {
            e.printStackTrace();
        }
    }
}
```

## Hibernate

Hibernate es un marco de trabajo de mapeo objeto-relacional (ORM) que simplifica el proceso de interacción con bases de datos. Proporciona una abstracción sobre JDBC y permite mapear objetos Java a tablas de bases de datos.

### Configuración de Hibernate

1. **Agregar Dependencias**: Asegúrate de incluir las dependencias de Hibernate en tu proyecto.
2. **Configurar Hibernate**: Crea un archivo de configuración (`hibernate.cfg.xml`) con los detalles de la conexión a la base de datos.
3. **Crear Entidades**: Define las clases Java que se mapearán a las tablas de la base de datos.
4. **Realizar Operaciones**: Utiliza la API de Hibernate para realizar operaciones CRUD (Crear, Leer, Actualizar, Eliminar) en la base de datos.

### Ejemplo de Configuración de Hibernate

```xml
<!-- archivo hibernate.cfg.xml -->
<!DOCTYPE hibernate-configuration PUBLIC "-//Hibernate/Hibernate Configuration DTD 3.0//EN" "http://hibernate.sourceforge.net/hibernate-configuration-3.0.dtd">
<hibernate-configuration>
    <session-factory>
        <!-- JDBC Database connection settings -->
        <property name="hibernate.connection.driver_class">com.mysql.cj.jdbc.Driver</property>
        <property name="hibernate.connection.url">jdbc:mysql://localhost:3306/mi_base_de_datos</property>
        <property name="hibernate.connection.username">root</property>
        <property name="hibernate.connection.password">mi_contrasena</property>

        <!-- Specify dialect -->
        <property name="hibernate.dialect">org.hibernate.dialect.MySQLDialect</property>

        <!-- Echo all executed SQL to stdout -->
        <property name="hibernate.show_sql">true</property>

        <!-- Drop and re-create the database schema on startup -->
        <property name="hibernate.hbm2ddl.auto">update</property>

        <!-- Mention annotated class -->
        <mapping class="com.ejemplo.Empleado"/>
    </session-factory>
</hibernate-configuration>
```

## Spring Data JPA

Spring Data JPA es una parte del proyecto Spring que facilita la implementación de acceso a datos utilizando JPA (Java Persistence API). Ofrece una forma simplificada de trabajar con repositorios y entidades en aplicaciones Spring.

### Configuración de Spring Data JPA

1. **Agregar Dependencias**: Incluye las dependencias de Spring Data JPA en tu proyecto.
2. **Configurar el Repositorio**: Define interfaces de repositorio que extienden `JpaRepository`.
3. **Configurar la Entidad**: Anota las clases con `@Entity` para definir las entidades JPA.

### Ejemplo de Uso de Spring Data JPA

```java
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.stereotype.Repository;
import javax.persistence.Entity;
import javax.persistence.Id;

@SpringBootApplication
public class EjemploSpringDataJPA {
    public static void main(String[] args) {
        SpringApplication.run(EjemploSpringDataJPA.class, args);
    }
}

@Entity
class Empleado {
    @Id
    private Long id;
    private String nombre;

    // Getters y Setters
}

@Repository
interface EmpleadoRepository extends JpaRepository<Empleado, Long> {
}
```

## Conclusión

La conexión a bases de datos en Java puede realizarse utilizando JDBC para un control más detallado y directo o mediante bibliotecas como Hibernate y Spring Data JPA para una abstracción y simplificación de las operaciones. Cada enfoque tiene sus propias ventajas y puede ser elegido según los requisitos del proyecto.
