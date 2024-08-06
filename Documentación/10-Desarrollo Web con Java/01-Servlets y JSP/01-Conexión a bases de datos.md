# Introducción a Servlets

## ¿Qué es un Servlet?

Un Servlet es una clase en Java que maneja las solicitudes y respuestas en un entorno web. Los Servlets son parte de la especificación de Java EE (Enterprise Edition) y se utilizan para generar contenido dinámico en aplicaciones web. Funcionan en el servidor web y responden a las peticiones del cliente, que generalmente provienen de un navegador web.

## Funcionamiento Básico

Cuando un cliente realiza una solicitud a un servidor web, el servidor puede delegar el procesamiento de esa solicitud a un Servlet. El Servlet procesa la solicitud, genera una respuesta (que puede ser HTML, JSON, XML, etc.) y envía esa respuesta de vuelta al cliente.

## Ciclo de Vida de un Servlet

El ciclo de vida de un Servlet está controlado por el contenedor de Servlets (como Apache Tomcat). El ciclo de vida incluye las siguientes fases:

1. **Carga e Inicialización**: El contenedor carga el Servlet en la memoria y lo inicializa mediante el método `init()`.
2. **Procesamiento de Solicitudes**: Cuando llega una solicitud, el contenedor llama al método `service()` del Servlet. Este método procesa la solicitud y genera una respuesta.
3. **Destrucción**: Cuando el Servlet ya no es necesario, el contenedor llama al método `destroy()` para liberar los recursos.

### Ejemplo Básico de Servlet

A continuación se muestra un ejemplo simple de un Servlet que responde con un mensaje "Hello, World!":

#### Código del Servlet

```java
import java.io.IOException;
import java.io.PrintWriter;
import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

public class HelloWorldServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response) 
            throws ServletException, IOException {
        response.setContentType("text/html");
        PrintWriter out = response.getWriter();
        out.println("<html><body>");
        out.println("<h1>Hello, World!</h1>");
        out.println("</body></html>");
    }
}
```

## Configuración del Servlet

Para que el contenedor de Servlets pueda reconocer y manejar el Servlet, debes configurarlo en el archivo `web.xml` de tu aplicación web.

### Ejemplo de Configuración en `web.xml`

```xml
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee
                             http://xmlns.jcp.org/xml/ns/javaee/web-app_3_1.xsd"
         version="3.1">
    
    <servlet>
        <servlet-name>HelloWorldServlet</servlet-name>
        <servlet-class>com.example.HelloWorldServlet</servlet-class>
    </servlet>
    
    <servlet-mapping>
        <servlet-name>HelloWorldServlet</servlet-name>
        <url-pattern>/hello</url-pattern>
    </servlet-mapping>
</web-app>
```

En este ejemplo, el Servlet `HelloWorldServlet` está mapeado a la URL `/hello`. Esto significa que cuando un cliente accede a `/hello`, el contenedor invoca el Servlet.

## Métodos de un Servlet

Los métodos principales en un Servlet son:

- **`init()`**: Se llama una vez al inicializar el Servlet. Aquí se pueden configurar recursos o realizar tareas de inicialización.
- **`service(HttpServletRequest req, HttpServletResponse res)`**: Maneja las solicitudes y genera respuestas. Dependiendo del método HTTP (GET, POST, etc.), puedes sobrescribir métodos específicos como `doGet()`, `doPost()`, etc.
- **`destroy()`**: Se llama cuando el Servlet es destruido. Aquí se deben liberar los recursos y realizar la limpieza necesaria.

## Ejemplo de Uso de Métodos HTTP

Un Servlet puede manejar diferentes tipos de solicitudes HTTP mediante métodos específicos:

- **`doGet(HttpServletRequest req, HttpServletResponse res)`**: Para manejar solicitudes GET.
- **`doPost(HttpServletRequest req, HttpServletResponse res)`**: Para manejar solicitudes POST.
- **`doPut(HttpServletRequest req, HttpServletResponse res)`**: Para manejar solicitudes PUT.
- **`doDelete(HttpServletRequest req, HttpServletResponse res)`**: Para manejar solicitudes DELETE.

### Ejemplo de Manejo de Solicitudes POST

```java
@Override
protected void doPost(HttpServletRequest request, HttpServletResponse response) 
        throws ServletException, IOException {
    String name = request.getParameter("name");
    response.setContentType("text/html");
    PrintWriter out = response.getWriter();
    out.println("<html><body>");
    out.println("<h1>Hello, " + name + "!</h1>");
    out.println("</body></html>");
}
```

## Conclusión

Los Servlets son componentes fundamentales en la construcción de aplicaciones web Java. Permiten manejar solicitudes HTTP, generar respuestas dinámicas y gestionar el ciclo de vida de las solicitudes. Con una comprensión básica de Servlets, puedes construir aplicaciones web más complejas y robustas en el entorno de Java.
