# Creación de Páginas JSP

## ¿Qué es JSP?

JavaServer Pages (JSP) es una tecnología que permite crear páginas web dinámicas basadas en Java. JSP facilita la integración de código Java en el HTML para generar contenido dinámico que se envía al cliente. Es una tecnología complementaria a los Servlets y se utiliza para la presentación en aplicaciones web Java.

## Estructura Básica de una Página JSP

Una página JSP es un archivo con extensión `.jsp` que contiene código HTML y elementos JSP. El contenido dinámico se genera utilizando fragmentos de código Java insertados en la página. La estructura básica de una página JSP incluye:

1. **Directivas**: Proporcionan información sobre la página JSP, como el tipo de contenido y la codificación. Se colocan al inicio del archivo.
2. **Declaraciones**: Permiten definir variables y métodos que pueden ser utilizados en toda la página JSP.
3. **Expresiones**: Se utilizan para insertar valores directamente en el flujo de salida de la página.
4. **Scripts**: Permiten escribir bloques de código Java que se ejecutan en el servidor.
5. **Acciones**: Etiquetas especiales que realizan tareas específicas, como incluir otros archivos o redirigir a otra página.

### Ejemplo Básico de una Página JSP

Aquí tienes un ejemplo sencillo de una página JSP que muestra un saludo:

#### Código JSP

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Saludo JSP</title>
</head>
<body>
    <h1>Hola, Mundo!</h1>
    <% 
        // Código Java
        String nombre = "Juan";
        out.println("<p>Hola, " + nombre + "!</p>");
    %>
</body>
</html>
```

## Directivas JSP

Las directivas se utilizan para definir atributos globales para la página JSP. Se colocan al inicio del archivo y se escriben entre `<%@ %>`.

### Ejemplo de Directiva

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
```

- **`language`**: Define el lenguaje de scripting, en este caso, `java`.
- **`contentType`**: Define el tipo de contenido de la respuesta HTTP.
- **`pageEncoding`**: Define la codificación de caracteres utilizada en la página JSP.

## Declaraciones JSP

Las declaraciones se utilizan para definir variables y métodos que se pueden utilizar en toda la página JSP. Se colocan entre `<%! %>`.

### Ejemplo de Declaración

```jsp
<%! 
    private String getGreeting() {
        return "Bienvenido a mi página JSP!";
    }
%>
```

## Expresiones JSP

Las expresiones se utilizan para insertar valores en la página HTML. Se colocan entre `<%= %>`.

### Ejemplo de Expresión

```jsp
<p>La fecha y hora actual es: <%= new java.util.Date() %></p>
```

## Scripts JSP

Los scripts permiten escribir bloques de código Java que se ejecutan en el servidor. Se colocan entre `<% %>`.

### Ejemplo de Script

```jsp
<%
    String nombre = request.getParameter("nombre");
    if (nombre == null) {
        nombre = "Invitado";
    }
%>
<p>Hola, <%= nombre %>!</p>
```

## Acciones JSP

Las acciones JSP son etiquetas especiales que permiten realizar tareas como incluir otros archivos o redirigir a otra página. Se escriben entre `<jsp: %>`.

### Ejemplo de Acción: Incluir un Archivo

```jsp
<jsp:include page="header.jsp"/>
```

Este ejemplo incluye el contenido de `header.jsp` en la página actual.

## Conclusión

JSP es una tecnología poderosa para generar contenido web dinámico en aplicaciones Java. Permite integrar código Java en HTML de manera efectiva, facilitando la creación de páginas web interactivas y personalizadas. Al combinar JSP con Servlets y otras tecnologías Java EE, puedes construir aplicaciones web robustas y escalables.
