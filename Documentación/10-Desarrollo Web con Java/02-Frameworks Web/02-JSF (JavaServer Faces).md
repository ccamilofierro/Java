# JavaServer Faces (JSF)

## ¿Qué es JSF?

JavaServer Faces (JSF) es un framework de Java para el desarrollo de interfaces de usuario web en aplicaciones Java EE. JSF es parte de la especificación Java EE y proporciona una infraestructura basada en componentes para crear interfaces web ricas y dinámicas. Ofrece una forma de manejar la presentación y la interacción del usuario en aplicaciones web Java.

## Componentes Principales

### 1. **Componentes de Usuario**

Los componentes de usuario en JSF son elementos gráficos que representan partes de una interfaz web, como botones, campos de texto y listas. Estos componentes permiten al desarrollador construir interfaces ricas y funcionales. Los componentes se definen en las páginas JSF mediante etiquetas y se pueden personalizar con atributos.

### 2. **Administración de Estado**

JSF proporciona mecanismos para gestionar el estado de los componentes a través de las solicitudes. El estado puede ser administrado en el lado del servidor y mantenido entre las solicitudes mediante el uso de un mecanismo llamado "view state". Esto permite a la aplicación recordar los datos introducidos por el usuario y su interacción con la interfaz.

### 3. **Manejo de Eventos**

JSF permite manejar eventos de usuario, como clics de botones y cambios en campos de entrada. Los eventos se asocian con métodos en los beans administrados, y JSF maneja la invocación de estos métodos en respuesta a las acciones del usuario.

## Configuración Básica

### 1. **Dependencias**

Para usar JSF en un proyecto Java EE, debes incluir las dependencias necesarias en tu archivo `pom.xml` si estás utilizando Maven.

#### Ejemplo de Dependencia en `pom.xml`

```xml
<dependencies>
    <dependency>
        <groupId>javax.faces</groupId>
        <artifactId>javax.faces-api</artifactId>
        <version>2.3</version>
        <scope>provided</scope>
    </dependency>
</dependencies>
```

### 2. **Configuración en `web.xml`**

Debes configurar el `FacesServlet` en el archivo `web.xml` para manejar las solicitudes JSF.

#### Ejemplo de Configuración en `web.xml`

```xml
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee
                             http://xmlns.jcp.org/xml/ns/javaee/web-app_3_1.xsd"
         version="3.1">

    <servlet>
        <servlet-name>FacesServlet</servlet-name>
        <servlet-class>javax.faces.webapp.FacesServlet</servlet-class>
        <load-on-startup>1</load-on-startup>
    </servlet>

    <servlet-mapping>
        <servlet-name>FacesServlet</servlet-name>
        <url-pattern>*.xhtml</url-pattern>
    </servlet-mapping>

</web-app>
```

## Creación de un Managed Bean

Un managed bean en JSF es una clase Java que se utiliza para manejar la lógica de negocio y los datos de la aplicación. Los beans son administrados por el contenedor JSF y se pueden utilizar en las páginas XHTML.

### Ejemplo de Managed Bean

```java
import javax.faces.bean.ManagedBean;
import javax.faces.bean.RequestScoped;

@ManagedBean
@RequestScoped
public class HelloBean {

    private String message;

    public HelloBean() {
        message = "Hola, Mundo!";
    }

    public String getMessage() {
        return message;
    }
}
```

## Creación de una Página XHTML

Las páginas XHTML en JSF utilizan una sintaxis especial para integrar componentes JSF y managed beans. Las páginas se crean con la extensión `.xhtml`.

### Ejemplo de Página XHTML

```xhtml
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml"
      xmlns:h="http://xmlns.jcp.org/jsf/html">
<head>
    <meta charset="UTF-8">
    <title>Hello Page</title>
</head>
<body>
    <h:form>
        <h:outputText value="#{helloBean.message}" />
    </h:form>
</body>
</html>
```

## Navegación en JSF

JSF permite definir la navegación entre páginas mediante reglas de navegación. Las reglas pueden ser configuradas en un archivo `faces-config.xml` o mediante anotaciones en los beans.

### Ejemplo de Navegación en `faces-config.xml`

```xml
<navigation-rule>
    <from-view-id>/index.xhtml</from-view-id>
    <navigation-case>
        <from-outcome>goToHello</from-outcome>
        <to-view-id>/hello.xhtml</to-view-id>
    </navigation-case>
</navigation-rule>
```

## Conclusión

JavaServer Faces (JSF) es una tecnología robusta y flexible para construir interfaces de usuario en aplicaciones Java EE. Proporciona una arquitectura basada en componentes y un marco para gestionar el estado, manejar eventos y realizar navegación entre páginas. Al utilizar JSF, puedes crear aplicaciones web interactivas y eficientes con una estructura clara y mantenible.
