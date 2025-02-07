# Práctica 4.1 - Cliente de FTP y correo electrónico

!!! note "Antes de comenzar"

    Para el uso de Jakarta Mail y Apache Commons Net necesitamos importar dichas API o librerías a nuestro proyecto. Este proceso se simplifica si usamos alguna herramienta para la construcción de proyectos, como puede ser Maven o Gradle.

    En el caso de Maven, añadiendo el archivo [*pom.xml*](https://pastebin.com/475Fd1Z6) con las dependencias correspondientes a la raíz del proyecto.

## Ejercicio 1 - Cliente de FTP

Para comenzar debes crear un servidor FTP en tu equipo. Para ello puedes usar [el siguiente tutorial](https://www.youtube.com/watch?v=8sMEfjzfB4o). Además, deberás crear 3 usuarios con una carpeta para cada uno de ellos. Dentro de dichas carpetas deberá existir un archivo LOG.txt, cuya primera línea es "Conexiones del usuario."

A continuación se muestran los nombres de usuario, contraseñas, carpetas y archivos a crear. Cada usuario tendrá control total sobre su carpeta y ninguno sobre las carpetas de los demás usuarios.

| Nombre de usuario | Contraseña | Carpeta y archivo |
| -- | -- | -- |
| usuario1 | usu1 | usuario1/LOG.txt |
| usuario2 | usu2 | usuario2/LOG.txt |
| usuario3 | usu3 | usuario3/LOG.txt |

Crea una aplicación en Java que, usando Apache Commons Net, pida por consola un nombre de usuario y contraseña en un proceso repetitivo que finalizará cuando el nombre de usuario sea *. Una vez introducido el nombre de usuario y la contraseña se deberá conectar al servidor FTP que se acaba de crear.

Cada vez que se realice esta conexión se deberá acceder al archivo LOG del usuario en cuestión y registrar la información sobre la fecha y hora en la que se realiza. Por ejemplo.

```
Conexiones del usuario.
Hora de conexión: Fry Jan 24 11:00:00 CET 2025
```

Para mostrar la hora de conexión se puede utilizar la siguiente expresión:

```java
java.util.Date hora = new java.util.Date(System.currentTimeMillis());
```

Cada vez que el usuario se conecte hay que añadir una nueva línea con la información correspondiente. Por ejemplo, si el usuario ha realizado 3 conexiones, el contenido del fichero LOG.txt sería el siguiente:

```
Conexiones del usuario.
Hora de conexión: Fry Jan 24 11:00:00 CET 2025
Hora de conexión: Fry Jan 24 11:15:58 CET 2025
Hora de conexión: Fry Jan 24 11:17:23 CET 2025
```

## Ejercicio 2 - Cliente de correo electrónico

Crea un cliente SMTP por consola en Java usando Jakarta Mail que permita enviar correos electrónicos. El programa solicitará al usuario los siguientes datos: dirección del servidor SMTP, puerto, usuario y contraseña.

Una vez introducidos deberá solicitar la dirección del remitente, del destinatario, el asunto y el cuerpo del mensaje. Además se deberá poder introducir, si el usuario desea, la ruta de un fichero para su envío.

El programa deberá mostrar que el envío ha sido satisfactorio ("Correo enviado con éxito.") o en caso de error ("No se pudo enviar el correo.").

A continuación, deberás crear un cliente IMAP por consola que permita leer los correos **no leídos** de una cuenta de correo electrónico. El usuario deberá facilitar la dirección del servidor IMAP, el puerto, el usuario y la contraseña.

La aplicación mostrará para cada correo sin leer toda la información relativa a él: remitente, fecha y hora, asunto y cuerpo del mensaje.

Se recomienda para este ejercicio el uso de alguna cuenta de correo de Google (tanto para el envío como para la lectura de mensajes no leídos), por ejemplo, la corporativa del centro. Para ello es necesario utilizar [las contraseñas para aplicaciones externas que tiene el correo de Google](https://myaccount.google.com/apppasswords).

## Criterios de evaluación

Esta práctica evalúa todos los criterios de evaluación del **RA4**. Para su corrección se tendrá en cuenta:

1. Conexión y autenticación (FTP y SMTP/IMAP) – 20 %
    - Correcta configuración y uso de credenciales para establecer conexión (servidor FTP, SMTP, IMAP).
    - Mecanismos de reconexión o manejo de errores básicos si la conexión falla.
2. Manejo de ficheros y persistencia (LOG en FTP) – 10 %
    - Descarga/lectura y subida/escritura de ficheros en el servidor FTP.
    - Registro de la información en el archivo LOG.txt, respetando el formato indicado.
3. Registro de fecha y hora en las acciones realizadas – 10 %
    - Uso correcto de objetos de fecha/hora (por ejemplo Date, LocalDateTime, etc.).
    - Formato y contenido del registro del LOG (una nueva línea por conexión con la fecha y hora).
4. Envío de correos con SMTP – 15 %
    - Solicitud de todos los campos por consola (servidor SMTP, puerto, usuario, contraseña, remitente, destinatario, asunto y cuerpo).
    - Posibilidad de añadir adjuntos en el correo si el usuario lo desea.
    - Confirmación clara de envío exitoso o mensaje de error.
5. Lectura de correos no leídos con IMAP – 15 %
    - Solicitud de credenciales IMAP (servidor, puerto, usuario, contraseña).
    - Lectura y muestra de la información del correo (remitente, fecha, hora, asunto y cuerpo) únicamente para los correos no leídos.
    - Control básico de posibles errores (problemas de conexión o credenciales).
6. Control de errores y validación de datos – 10 %
    - Manejo de excepciones (por ejemplo, manejo de IOException, MessagingException, etc.).
    - Validación de datos de entrada (campos vacíos, valores de puertos inválidos, etc.).
7. Uso correcto de las librerías (Apache Commons Net y Jakarta Mail) – 10 %
    - Inclusión de dependencias correctas (pom.xml, uso de Maven o Gradle si se desea).
    - Implementación eficaz de los métodos de las librerías y clases correspondientes.
8. Estructura, claridad y documentación del código – 10 %
    - Organización del código (clases y métodos con responsabilidades claras).
    - Comentarios o documentación mínima que facilite el mantenimiento y la comprensión.
    - Orden y legibilidad del código fuente.

## Método de entrega

Comprime el proyecto junto con la documentación en un archivo ZIP y súbelo a la plataforma Moodle Centros en el lugar dedicado a ello. El archivo ZIP deberá tener el siguiente formato:

**Apellido1Apellido2_Nombre_PSP_UD4_P1.zip**