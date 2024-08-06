# Introducción a Hibernate

## ¿Qué es Hibernate?

Hibernate es un marco de mapeo objeto-relacional (ORM) para Java. Proporciona una solución para mapear las clases de Java a tablas de bases de datos y viceversa. Hibernate simplifica el proceso de persistencia y recuperación de datos mediante el uso de un modelo de objetos, eliminando la necesidad de escribir código SQL detallado para la mayoría de las operaciones de base de datos.

## Ventajas de Usar Hibernate

- **Reducción de Código SQL**: Hibernate genera automáticamente el SQL necesario para realizar operaciones de base de datos, reduciendo el código SQL manual que debes escribir.
- **Manejo de la Persistencia**: Hibernate maneja la persistencia de objetos, lo que significa que no tienes que preocuparte por la conversión entre objetos Java y registros de la base de datos.
- **Consultas HQL**: Hibernate Query Language (HQL) es un lenguaje de consulta orientado a objetos que permite realizar consultas sobre el modelo de objetos en lugar de directamente sobre la base de datos.
- **Soporte para Transacciones**: Hibernate ofrece soporte para la gestión de transacciones, facilitando la administración de las operaciones de base de datos que requieren atomicidad.

## Configuración Básica

Para comenzar a usar Hibernate, debes seguir algunos pasos básicos de configuración:

1. **Agregar Dependencias**: Incluye las bibliotecas de Hibernate en tu proyecto. Si usas Maven, agrega las dependencias en tu archivo `pom.xml`.

   ### Ejemplo de Dependencias en Maven

   ```xml
   <dependency>
       <groupId>org.hibernate</groupId>
       <artifactId>hibernate-core</artifactId>
       <version>5.6.7.Final</version>
   </dependency>
   <dependency>
       <groupId>javax.persistence</groupId>
       <artifactId>javax.persistence-api</artifactId>
       <version>2.2</version>
   </dependency>
   <dependency>
       <groupId>org.hibernate</groupId>
       <artifactId>hibernate-entitymanager</artifactId>
       <version>5.6.7.Final</version>
   </dependency>
   <dependency>
       <groupId>org.hsqldb</groupId>
       <artifactId>hsqldb</artifactId>
       <version>2.5.1</version>
   </dependency>
   ```

2. **Configurar Hibernate**: Crea un archivo de configuración `hibernate.cfg.xml` que define la conexión a la base de datos y otras propiedades de Hibernate.

   ### Ejemplo de Configuración Hibernate

   ```xml
   <!DOCTYPE hibernate-configuration PUBLIC "-//Hibernate/Hibernate Configuration DTD 3.0//EN" "http://hibernate.sourceforge.net/hibernate-configuration-3.0.dtd">
   <hibernate-configuration>
       <session-factory>
           <!-- Database connection settings -->
           <property name="hibernate.connection.driver_class">org.hsqldb.jdbc.JDBCDriver</property>
           <property name="hibernate.connection.url">jdbc:hsqldb:hsql://localhost/mydb</property>
           <property name="hibernate.connection.username">sa</property>
           <property name="hibernate.connection.password"></property>

           <!-- Specify dialect -->
           <property name="hibernate.dialect">org.hibernate.dialect.HSQLDialect</property>

           <!-- Echo all executed SQL to stdout -->
           <property name="hibernate.show_sql">true</property>

           <!-- Drop and re-create the database schema on startup -->
           <property name="hibernate.hbm2ddl.auto">update</property>

           <!-- Names the annotated entity class -->
           <mapping class="com.example.Employee"/>
       </session-factory>
   </hibernate-configuration>
   ```

3. **Crear la Entidad**: Define las clases de entidad que se mapearán a las tablas de la base de datos. Las clases deben estar anotadas con las anotaciones de Hibernate.

   ### Ejemplo de Entidad

   ```java
   import javax.persistence.Entity;
   import javax.persistence.Id;
   import javax.persistence.GeneratedValue;
   import javax.persistence.GenerationType;

   @Entity
   public class Employee {
       @Id
       @GeneratedValue(strategy = GenerationType.IDENTITY)
       private Long id;

       private String name;
       private double salary;

       // Getters y Setters
       public Long getId() { return id; }
       public void setId(Long id) { this.id = id; }

       public String getName() { return name; }
       public void setName(String name) { this.name = name; }

       public double getSalary() { return salary; }
       public void setSalary(double salary) { this.salary = salary; }
   }
   ```

## Operaciones Básicas con Hibernate

Una vez que Hibernate está configurado, puedes realizar operaciones básicas como guardar, actualizar y eliminar entidades.

### Ejemplo de Guardar una Entidad

```java
import org.hibernate.Session;
import org.hibernate.Transaction;

public class HibernateExample {
    public static void main(String[] args) {
        Session session = HibernateUtil.getSessionFactory().openSession();
        Transaction transaction = null;

        try {
            transaction = session.beginTransaction();

            Employee employee = new Employee();
            employee.setName("John Doe");
            employee.setSalary(50000);

            session.save(employee);
            transaction.commit();
        } catch (Exception e) {
            if (transaction != null) transaction.rollback();
            e.printStackTrace();
        } finally {
            session.close();
        }
    }
}
```

### Ejemplo de Consultar Entidades

```java
import org.hibernate.Session;
import org.hibernate.query.Query;
import java.util.List;

public class HibernateQueryExample {
    public static void main(String[] args) {
        Session session = HibernateUtil.getSessionFactory().openSession();

        try {
            Query<Employee> query = session.createQuery("FROM Employee", Employee.class);
            List<Employee> employees = query.list();

            for (Employee emp : employees) {
                System.out.println("ID: " + emp.getId() + ", Name: " + emp.getName() + ", Salary: " + emp.getSalary());
            }
        } finally {
            session.close();
        }
    }
}
```

## Conclusión

Hibernate es una poderosa herramienta ORM que simplifica la persistencia de datos en Java mediante el mapeo de clases a tablas de base de datos. Con una configuración adecuada y el uso de entidades, puedes realizar operaciones CRUD (crear, leer, actualizar y eliminar) de manera eficiente. A medida que adquieras experiencia con Hibernate, podrás explorar características avanzadas como relaciones entre entidades, cachés y consultas más complejas.
