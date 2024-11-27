# Práctica 3.1 - Implementación de una sala de chat cliente/servidor en Java usando UDP

## Descripción de la tarea

Desarrolla una aplicación cliente/servidor en Java que permita a múltiples clientes participar en una sala de chat utilizando el protocolo UDP. La aplicación debe incorporar funcionalidades adicionales que mejoren la experiencia de usuario y la robustez del sistema.

### Requisitos específicos

1. Comunicación básica:
    - Implementar un servidor UDP que reciba mensajes de los clientes y los reenvíe a todos los clientes conectados.
    - Implementar un cliente UDP que permita a los usuarios enviar mensajes al servidor y recibir mensajes de otros usuarios a través del servidor.
2. Nombres de usuario únicos:
    - Al iniciar la aplicación, cada cliente debe ingresar un nombre de usuario.
    - El servidor debe garantizar que no existan dos usuarios conectados con el mismo nombre.
    - Si un nombre de usuario ya está en uso, el servidor debe notificar al cliente y solicitar un nombre diferente.
    - Todos los mensajes enviados deben incluir el nombre de usuario del remitente.
3. Mensajes privados:
    - Permitir a los usuarios enviar mensajes privados a otros usuarios específicos.
    - Utilizar un formato especial para los mensajes privados, por ejemplo: ```/privado <usuario_destino> <mensaje>```
    - El servidor debe reenviar el mensaje únicamente al usuario destinatario, indicando que es un mensaje privado.
    - Si el usuario destinatario no existe o no está conectado, el servidor debe notificar al remitente.
4. Listado de usuarios conectados:
    - Implementar un comando que permita a los clientes solicitar la lista actual de usuarios conectados.
    - Utilizar un comando específico, por ejemplo: ```/usuarios```
    - El servidor debe responder al cliente que lo solicitó con la lista actualizada de usuarios.
5. Desconexión limpia:
    - Cuando un cliente decide salir del chat, debe notificar al servidor mediante un comando, por ejemplo: ```/salir```
    - El servidor debe eliminar al usuario de la lista de usuarios conectados.
    - El servidor debe notificar a los demás clientes que el usuario se ha desconectado.
6. Manejo de comandos desconocidos:
    - Si un cliente envía un comando no reconocido (por ejemplo, un mensaje que comienza con ```/``` pero no es un comando válido), el servidor debe responder al cliente con un mensaje de error adecuado.
7. Historial de mensajes:
    - El servidor debe mantener un historial de los últimos 10 mensajes.
    - Cuando un nuevo cliente se conecta, el servidor le envía el historial para que pueda ponerse al día con la conversación.
8. Interfaz de usuario:
    - Los mensajes deben ser claros y distinguir entre mensajes públicos, mensajes privados y notificaciones del sistema.
    - Ejemplo de formato para mensajes públicos: ```[Usuario] Mensaje```
    - Ejemplo de formato para mensajes privados: ```[Privado de Usuario] Mensaje```
    - Ejemplo de notificación del sistema: ```Usuario se ha conectado/desconectado```
9. Servidor monohilo:
    - Importante: El servidor no debe ser multihilo. Todas las operaciones deben manejarse en un solo hilo de ejecución.
    - A pesar de las limitaciones de no utilizar hilos adicionales, el servidor debe ser capaz de manejar múltiples clientes de manera eficiente utilizando el protocolo UDP.
10. Robustez y manejo de errores:
    - El servidor y los clientes deben manejar adecuadamente posibles excepciones y errores de comunicación.
    - La aplicación no debe cerrarse inesperadamente ante entradas incorrectas o problemas de red.
    - Implementar validaciones necesarias para garantizar la estabilidad del sistema.
11. Visualización de actividades del servidor:
    - El servidor debe mostrar en la consola, durante su ejecución, las acciones que va realizando.
    - Esto incluye eventos como: conexiones de nuevos usuarios, desconexiones, recepción y envío de mensajes, manejo de comandos y cualquier error o situación relevante.
    - La información mostrada debe ser clara y permitir al administrador del servidor entender el estado y actividad del sistema.

### Instrucciones Adicionales

- Desarrollo modular:
    - Estructura tu código de forma modular, creando funciones o métodos que separen claramente las distintas funcionalidades (por ejemplo, manejo de comandos, envío y recepción de mensajes, etc.).
- Comentarios y buenas prácticas:
	- Incluye comentarios en el código que expliquen las partes más importantes y la lógica implementada.
	- Sigue las buenas prácticas de programación en Java (nombres de variables significativos, indentación, manejo adecuado de recursos, etc.).
- Pruebas:
	- Realiza pruebas exhaustivas para asegurarte de que todas las funcionalidades funcionan correctamente.
	- Prueba escenarios como: conexión de múltiples usuarios, envío de mensajes públicos y privados, manejo de usuarios con nombres duplicados, comandos desconocidos, etc.
- Documentación:
	- Proporciona un breve manual de usuario que explique cómo utilizar la aplicación, incluyendo los comandos disponibles y ejemplos de uso.
	- Incluye instrucciones sobre cómo compilar y ejecutar la aplicación.

## Criterios de evaluación

Esta práctica evalúa los criterios de evaluación **a)**, **b)**, **c)**, **d)**, **e)**, **f)** y **g)** del **RA3**. Para su corrección se tendrá en cuenta:

- Correctitud y completitud de las funcionalidades requeridas (70%).
- Calidad del código (10%).
- Manejo adecuado de errores y robustez de la aplicación (5%).
- Interfaz de usuario (5%).
- Documentación y claridad en las instrucciones proporcionadas (10%).

## Método de entrega

Comprime el proyecto junto con la documentación en un archivo ZIP y súbelo a la plataforma Moodle Centros en el lugar dedicado a ello. El archivo ZIP deberá tener el siguiente formato:

**Apellido1Apellido2_Nombre_PSP_UD3_P1.zip**