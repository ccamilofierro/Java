# Spring MVC

## ¿Qué es Spring MVC?

Spring MVC (Model-View-Controller) es un marco de trabajo (framework) de Java basado en el patrón de diseño MVC para desarrollar aplicaciones web. Es parte del proyecto Spring, que proporciona una arquitectura robusta y flexible para construir aplicaciones web Java. Spring MVC ayuda a separar la lógica de la aplicación en tres componentes principales: el modelo, la vista y el controlador.

## Componentes Principales

### 1. **Modelo**

El modelo representa los datos de la aplicación y la lógica de negocio. En Spring MVC, los modelos suelen ser objetos Java que se utilizan para almacenar datos y pueden ser manipulados por los controladores.

### 2. **Vista**

La vista es responsable de presentar los datos al usuario. En Spring MVC, las vistas pueden ser JSP, Thymeleaf, o cualquier otro tipo de tecnología de presentación. La vista recibe los datos del modelo y los muestra en una forma adecuada para el usuario.

### 3. **Controlador**

El controlador maneja las solicitudes del usuario y coordina la interacción entre el modelo y la vista. En Spring MVC, los controladores son clases anotadas con `@Controller` y contienen métodos anotados con `@RequestMapping` que manejan las solicitudes HTTP.

## Configuración Básica

### 1. **Dependencias**

Para utilizar Spring MVC, debes agregar las dependencias de Spring Web en tu archivo `pom.xml` si estás utilizando Maven:

```xml
<dependencies>
    <dependency>
        <groupId>org.springframework</groupId>
        <artifactId>spring-webmvc</artifactId>
        <version>5.3.23</version>
    </dependency>
</dependencies>
```

### 2. **Configuración del DispatcherServlet**

El `DispatcherServlet` es el núcleo de Spring MVC. Debe configurarse en el archivo `web.xml` para manejar las solicitudes web.

#### Ejemplo de Configuración en `web.xml`

```xml
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee
                             http://xmlns.jcp.org/xml/ns/javaee/web-app_3_1.xsd"
         version="3.1">

    <servlet>
        <servlet-name>dispatcher</servlet-name>
        <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
        <load-on-startup>1</load-on-startup>
    </servlet>

    <servlet-mapping>
        <servlet-name>dispatcher</servlet-name>
        <url-pattern>/</url-pattern>
    </servlet-mapping>

</web-app>
```

### 3. **Configuración de Spring MVC**

La configuración de Spring MVC puede realizarse a través de un archivo de configuración XML o mediante una clase de configuración Java.

#### Ejemplo de Configuración en `dispatcher-servlet.xml`

```xml
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
                           http://www.springframework.org/schema/beans/spring-beans.xsd">

    <bean class="org.springframework.web.servlet.view.InternalResourceViewResolver">
        <property name="prefix" value="/WEB-INF/views/" />
        <property name="suffix" value=".jsp" />
    </bean>

</beans>
```

#### Ejemplo de Configuración en una Clase Java

```java
import org.springframework.context.annotation.Configuration;
import org.springframework.web.servlet.config.annotation.EnableWebMvc;
import org.springframework.web.servlet.config.annotation.WebMvcConfigurer;
import org.springframework.web.servlet.config.annotation.ViewResolverRegistry;
import org.springframework.web.servlet.view.InternalResourceViewResolver;

@Configuration
@EnableWebMvc
public class WebConfig implements WebMvcConfigurer {

    @Override
    public void configureViewResolvers(ViewResolverRegistry registry) {
        InternalResourceViewResolver resolver = new InternalResourceViewResolver();
        resolver.setPrefix("/WEB-INF/views/");
        resolver.setSuffix(".jsp");
        registry.viewResolver(resolver);
    }
}
```

## Creación de un Controlador

Los controladores en Spring MVC manejan las solicitudes web y devuelven los nombres de las vistas.

### Ejemplo de Controlador

```java
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;
import org.springframework.web.servlet.ModelAndView;

@Controller
public class HelloController {

    @RequestMapping(value = "/hello", method = RequestMethod.GET)
    public ModelAndView hello() {
        ModelAndView modelAndView = new ModelAndView("hello");
        modelAndView.addObject("message", "Hola, Mundo!");
        return modelAndView;
    }
}
```

En este ejemplo, el método `hello()` maneja las solicitudes a la URL `/hello`, agrega un mensaje al modelo, y retorna la vista `hello`.

## Creación de una Vista

La vista es un archivo que muestra la información al usuario. En este ejemplo, se usa JSP para la vista.

### Ejemplo de Vista (hello.jsp)

```jsp
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Hello Page</title>
</head>
<body>
    <h1>${message}</h1>
</body>
</html>
```

## Conclusión

Spring MVC es una potente herramienta para el desarrollo de aplicaciones web en Java. Ofrece un enfoque flexible y modular para separar las preocupaciones de la lógica de negocio, la presentación y la gestión de solicitudes. Al utilizar Spring MVC, puedes construir aplicaciones web escalables y mantenibles con una estructura clara y organizada.
