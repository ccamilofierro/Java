# Mapeo de Entidades y Relaciones en Hibernate

## Mapeo de Entidades

En Hibernate, el mapeo de entidades implica relacionar las clases Java con las tablas de una base de datos. Cada instancia de una clase se corresponde con una fila en la tabla correspondiente. Aquí se describen algunos aspectos clave del mapeo de entidades:

### Anotaciones Básicas

- **`@Entity`**: Marca una clase como entidad que debe ser mapeada a una tabla de la base de datos.
- **`@Table`**: Especifica la tabla de la base de datos a la que se mapea la entidad (opcional si el nombre de la tabla es el mismo que el nombre de la clase).
- **`@Id`**: Marca un campo como la clave primaria de la entidad.
- **`@GeneratedValue`**: Especifica la estrategia de generación de valores para la clave primaria (por ejemplo, AUTO, IDENTITY, SEQUENCE, TABLE).
- **`@Column`**: Define las propiedades de la columna en la tabla, como el nombre, el tipo y la longitud (opcional si los valores predeterminados son adecuados).

### Ejemplo de Mapeo de Entidad

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

## Relaciones entre Entidades

Hibernate también permite modelar relaciones entre entidades, como las relaciones uno a uno, uno a muchos y muchos a muchos. Las principales anotaciones utilizadas para definir relaciones son:

- **`@OneToOne`**: Define una relación uno a uno entre dos entidades.
- **`@OneToMany`**: Define una relación uno a muchos entre dos entidades.
- **`@ManyToOne`**: Define una relación muchos a uno entre dos entidades.
- **`@ManyToMany`**: Define una relación muchos a muchos entre dos entidades.

### Ejemplo de Relación Uno a Muchos

Consideremos un ejemplo en el que un `Department` tiene múltiples `Employee`:

#### Entidad `Department`

```java
import javax.persistence.Entity;
import javax.persistence.Id;
import javax.persistence.OneToMany;
import java.util.Set;

@Entity
public class Department {
    @Id
    private Long id;

    private String name;

    @OneToMany(mappedBy = "department")
    private Set<Employee> employees;

    // Getters y Setters
    public Long getId() { return id; }
    public void setId(Long id) { this.id = id; }

    public String getName() { return name; }
    public void setName(String name) { this.name = name; }

    public Set<Employee> getEmployees() { return employees; }
    public void setEmployees(Set<Employee> employees) { this.employees = employees; }
}
```

#### Entidad `Employee`

```java
import javax.persistence.Entity;
import javax.persistence.Id;
import javax.persistence.ManyToOne;

@Entity
public class Employee {
    @Id
    private Long id;

    private String name;
    private double salary;

    @ManyToOne
    private Department department;

    // Getters y Setters
    public Long getId() { return id; }
    public void setId(Long id) { this.id = id; }

    public String getName() { return name; }
    public void setName(String name) { this.name = name; }

    public double getSalary() { return salary; }
    public void setSalary(double salary) { this.salary = salary; }

    public Department getDepartment() { return department; }
    public void setDepartment(Department department) { this.department = department; }
}
```

### Ejemplo de Relación Muchos a Muchos

Consideremos un ejemplo en el que `Student` puede estar inscrito en múltiples `Course` y cada `Course` puede tener múltiples `Student`:

#### Entidad `Student`

```java
import javax.persistence.Entity;
import javax.persistence.Id;
import javax.persistence.ManyToMany;
import java.util.Set;

@Entity
public class Student {
    @Id
    private Long id;

    private String name;

    @ManyToMany
    private Set<Course> courses;

    // Getters y Setters
    public Long getId() { return id; }
    public void setId(Long id) { this.id = id; }

    public String getName() { return name; }
    public void setName(String name) { this.name = name; }

    public Set<Course> getCourses() { return courses; }
    public void setCourses(Set<Course> courses) { this.courses = courses; }
}
```

#### Entidad `Course`

```java
import javax.persistence.Entity;
import javax.persistence.Id;
import javax.persistence.ManyToMany;
import java.util.Set;

@Entity
public class Course {
    @Id
    private Long id;

    private String title;

    @ManyToMany(mappedBy = "courses")
    private Set<Student> students;

    // Getters y Setters
    public Long getId() { return id; }
    public void setId(Long id) { this.id = id; }

    public String getTitle() { return title; }
    public void setTitle(String title) { this.title = title; }

    public Set<Student> getStudents() { return students; }
    public void setStudents(Set<Student> students) { this.students = students; }
}
```

## Conclusión

El mapeo de entidades y relaciones en Hibernate permite a los desarrolladores definir cómo se deben almacenar y relacionar las clases Java con las tablas de bases de datos. Al utilizar anotaciones para definir estas relaciones, Hibernate facilita la gestión de datos complejos y la implementación de modelos de dominio ricos en aplicaciones Java.
