# Práctica 3.2 - El juego de la ruleta

Diseño e implementación del juego de la ruleta permitiendo jugar de manera individual o bien en grupos. La finalidad del juego es averiguar la frase o palabra secreta que se muestra en cada partida.

## Descripción de la tarea

La comunicación entre los clientes del juego de la ruleta se realizará bajo el protocolo de transporte TCP. La práctica que se propone consiste en la realización de una aplicación cliente/servidor (multihilo) que implemente el juego de la ruleta mediante el cual, los usuarios del juego (los clientes) se conectan al servicio (el servidor) y pueden jugar una partida, permitiendo o bien jugar una partida de forma individual o bien competir en el juego con otros usuarios. Todas las partidas tanto individuales como colectivas versarán sobre la categoría de refranes.

### Juego individual

La primera variante del juego nos permite jugar una partida al ahorcado de forma individual. Nos conectaremos al servidor y nos permitirá iniciar una partida.

El procedimiento que se seguirá será el siguiente:

- Un cliente se conecta al servicio y si la conexión ha sido correcta el sistema devuelve “+0k. Usuario conectado”.
- Para poder acceder a los servicios es necesario identificarse mediante el envío del usuario y clave para que el sistema lo valide. Los mensajes que deben indicarse son: “USUARIO usuario” para indicar el usuario, tras el cual el servidor enviará “+Ok. Usuario correcto” o “–Err. Usuario incorrecto”. En caso de ser correcto el siguiente mensaje que se espera recibir es “PASSWORD password”, donde el servidor responderá con el mensaje de “+Ok. Usuario
validado” o “–Err. Error en la validación”.
- Un usuario nuevo podrá registrarse mediante el mensaje “REGISTRO –u usuario –p password”. Se llevará un control para evitar colisiones con los nombre de usuarios ya existentes.
- Una vez conectado y validado, el cliente podrá llevar a cabo una partida individual en el juego indicando un mensaje de “PARTIDA-INDIVIDUAL”. Recibido este mensaje en el servidor, éste se encargará de mandarle una frase
con la que iniciar el juego indicando mediante el símbolo “-“ las posiciones que deben ser rellenadas con consonante o vocal y el símbolo “ “ para indicar el espacio en blanco entre las palabras que componen la frase. No se tendrán en cuenta en la frase los signos de puntuación como elemento a adivinar por el jugador. En este punto son admitidos tres tipos de mensajes que se puede enviar al servidor:

    - CONSONANTE letra, donde letra indica una consonante que se piensa que puede estar en la frase.
    - VOCAL letra, donde letra indica una vocal que se piensa que puede estar en la frase.
    - RESOLVER frase, donde frase representará una cadena que contiene el refrán que queremos resolver. El contenido de la cadena debe ser independiente de si se trata de mayúsculas o minúsculas.

- Cada vez que un cliente mande un mensaje de CONSONANTE/VOCAL al servidor, éste deberá devolverle “+Ok. Existe la consonante” seguido por la frase con la información que se lleva de momento si la letra está contenida en la frase a resolver o “+Ok. No existe la consonante” seguido por la frase con la información que se lleva de momento en caso de que la letra no exista en la palabra a averiguar. En caso de error en la recepción del mensaje, debido a que se trate de una consonante o vocal inválida, se procederá con un mensaje “-Err. Mensaje no válido”.
- Se llevará la cuenta del número de intentos que ha realizado el usuario para resolver la frase, para que finalmente al terminar la partida se le asigne una puntuación a cada usuario. La puntuación será fija y tendrá establecido los siguientes valores, si se ha resuelto en menos de 5 intentos tendrá una valoración de 150 puntos, si lo consigue entre 5 y 8 intentos se le asignará 100 puntos, entre 9 y 11 será 70 puntos, entre 12 y 15 será 50 puntos y todo lo que sea más de 15 intentos tendrá una puntuación de 0 puntos.
- Simplemente se podrá enviar un mensaje RESOLVER, en caso de acertarse o fallarse se termina la partida y el usuario simplemente podrá optar por salir del sistema o realizar otra partida:

    - Si se acierta la frase se le mandará al cliente un mensaje “+Ok. Enhorabuena”, mostrándole una estadística de las frases acertadas y falladas y su puntuación desde que se registró por primera vez.
    - Si se falla la frase, se le mandará al cliente un mensaje “+Ok. Le deseamos mejor suerte la próxima vez”, mostrándole una estadística de las frases acertadas y falladas y su puntuación desde que se registró por primera vez.

- Un mensaje de un cliente en la que se envíe la petición “SALIR”, hará que el servidor le dé de baja del sistema. Este mensaje puede ser enviado en cualquier momento, incluso en una partida empezada.
- Cualquier mensaje que no use uno de los especificadores detallados, generará un mensaje de “-Err” por parte del servidor.

Algunas de las restricciones a tener en cuenta son:

- La comunicación será mediante consola.
- El cliente deberá aceptar como argumento una dirección IP que será la dirección del servidor al que se conectará.
- El protocolo deberá permitir mandar mensajes de tamaño arbitrario. Teniendo como tamaño máximo envío una cadena de longitud 200 caracteres.
- El servidor aceptará servicios en el puerto 2050.
- El servidor debe permitir la conexión de varios clientes simultáneamente. Esto deberá resolverse mediante el uso de hilos.
- El número máximo de clientes conectados para jugar será de 50 usuarios.
- Todos los mensajes devueltos por el servidor que se necesiten contemplar, seguirán el criterio de ir precedidos por +Ok. Texto informativo, si la petición se ha podido aceptar sin problemas y –Err. Texto informativo, si ha habido algún tipo de error.
- Las frases que se van a resolver no tendrán en cuenta los signos de puntuación. En caso de que la frase cuente con alguno de ellos, aparecerá directamente como elemento visible desde el principio en la frase que se le muestra al usuario.

### Juego colectivo

La segunda variante del juego nos permite jugar con varias personas, concretamente el juego estará formado por grupo de tres personas.

El procedimiento que se seguirá será el siguiente:

- Un cliente se conecta al servicio y si la conexión ha sido correcta el sistema devuelve “+0k. Usuario conectado”.
- Para poder acceder a los servicios es necesario identificarse mediante el envío del usuario y clave para que el sistema lo valide. Los mensajes que deben indicarse son: “USUARIO usuario” para indicar el usuario, tras el cual el servidor enviará “+Ok. Usuario correcto” o “–Err. Usuario incorrecto”. En caso de ser correcto el siguiente mensaje que se espera recibir es “PASSWORD password”, donde el servidor responderá con el mensaje de “+Ok. Usuario validado” o “–Err. Error en la validación”.
- Un usuario nuevo podrá registrarse mediante el mensaje “REGISTRO –u usuario –p password”. Se llevará un control para evitar colisiones con los nombre de usuarios ya existentes.
- Una vez conectado y validado, el cliente podrá llevar a cabo una partida en el juego indicando un mensaje de “PARTIDA-GRUPO”. Recibido este mensaje en el servidor, éste se encargará de comprobar las personas que tiene pendiente para comenzar una partida:
    
    - Si con esta petición, ya se forma un grupo de tres personas, mandará un mensaje a cada una de ellas, para indicarle que la partida va a comenzar.
    - Si todavía falta alguna persona para iniciar la partida, mandará un mensaje al nuevo usuario, especificando que tiene su petición y que está a la espera de la conexión de otros jugadores. El usuario en este caso deberá quedarse a la espera de recibir un mensaje para jugar o también se le permitirá salir de la aplicación.
    - Cuando se disponga de tres usuarios, se le deja un mensaje a los tres usuarios indicando que va a comenzar la partida “+Ok. Empieza la partida” y seguido se indica la frase con la que iniciar la partida. Se indicarán todas las posiciones que representan una consonante o vocal mediante el símbolo “-“ y el espacio en blanco “ “, se utilizará para representar la separación entre las palabras de la frase. No se tendrán en cuenta en la frase los signos de puntuación como elemento a adivinar por el jugador. El orden de los usuarios en el juego será el mismo orden en el que se ha realizado la conexión (aunque puede implementarse otro criterio si lo veis más conveniente).
    - Cada usuario podrá ir mandando mensajes de CONSONANTE/VOCAL letra, mientras la frase contenga la letra que va especificando. Esta información se va mostrando a cada uno de los usuarios, al igual que los mensajes que envía el usuario que está jugando en cada momento. Cuando falle, se pasará a otro usuario, así hasta que un usuario escoja la opción de RESOLVER la frase. 
	
	En este punto son admitidos tres tipos de mensajes que se puede enviar al servidor:

    - CONSONANTE letra, donde letra indica una consonante que se piense que puede estar en la frase. La puntuación que se obtiene, sería 50 puntos por cada vez que la consonante aparezca en la frase a resolver. Si la frase desconocida no contiene ninguna consonante de la que has elegido, se pasará el turno al siguiente jugador.
    - VOCAL letra, para poder mandar este mensaje necesitas tener al menos 50 puntos, que se restarán por cada vocal que solicites, con independencia del número de veces que aparezca.
    - RESOLVER frase, donde frase representará una cadena que contiene el refrán que queremos resolver.

- Se debe tener cuidado con que el servidor cuando lleguen peticiones de usuarios cuando no sea su turno de jugar. En caso de que envíen un mensaje cuando no es su turno, deberá responder que todavía no es turno y deben esperar. La especificación del mensaje que se enviaría sería: “-Err. Debe esperar su turno”.
- En caso de que un usuario envíe la petición RESOLVER y ésta no sea la frase correcta, la partida termina, el usuario que ha fallado queda automáticamente con una puntuación de cero y ganaría el usuario que tuviese hasta ese momento una mayor puntuación. Se enviará un mensaje a cada uno de los jugadores, para indicar puntuaciones y ganador.
- Para salir del servicio se usará el mensaje “SALIR”, de este modo el servidor lo eliminará de clientes conectados y el juego continuará entre los restantes participantes. Este hecho se le debe de comunicar al resto de usuarios. Cuando quede un único jugador podrá terminar el panel o salir del sistema.
- Cualquier mensaje que no use uno de los especificadores detallados, generará un mensaje de “-Err” por parte del servidor.

Algunas restricciones a tener en cuenta en esta nueva versión que se debe implementar es:

- La comunicación será mediante consola.
- El cliente deberá aceptar como argumento una dirección IP que será la dirección del servidor al que se conectará.
- El protocolo deberá permitir mandar mensajes de tamaño arbitrario. Teniendo como tamaño máximo envío una cadena de longitud 200 caracteres.
- El servidor aceptará servicios en el puerto 2050.
- El servidor debe permitir la conexión de varios clientes simultáneamente. Esto deberá resolverse mediante el uso de hilos.
- El número máximo de clientes conectados será de 50 usuarios.
- Todos los mensajes devueltos por el servidor que se necesiten contemplar, seguirán el criterio de ir precedidos por +Ok. Texto informativo, si la petición se ha podido aceptar sin problemas y –Err. Texto informativo, si ha habido algún tipo de error.
- Las frases que se van a resolver no tendrán en cuenta los signos de puntuación. En caso de que la frase cuente con alguno de ellos, aparecerá directamente como elemento visible desde el principio en la frase que se le muestra al usuario.

### Resumen paquetes

Considerando la práctica completa, vamos a resumir los tipos de mensajes con el siguiente formato cada uno:

- USUARIO usuario: mensaje para introducir el usuario que desea.
- PASSWORD contraseña: mensaje para introducir la contraseña asociada al usuario.
- REGISTER –u usuario –p password: mensaje mediante el cual el usuario solicita registrarse para acceder al juego de la ruleta que escucha en el puerto TCP 2050.
- CONSONANTE letra, donde letra indica una consonante que se piensa que puede estar en la frase.
- VOCAL letra, para poder mandar este mensaje necesitas tener al menos 50 puntos, que se restarán por cada vocal que solicites, con independencia del número de veces que aparezca.
- RESOLVER frase, donde frase representará una cadena que contiene el refrán que queremos resolver.
- SALIR: mensaje para solicitar salir del juego.
- Cualquier otra tipo de mensaje que se envíe al servidor, no será reconocida por el protocolo como un mensaje válido y generará su correspondiente “-Err.” por parte del servidor.

## Criterios de evaluación

Esta práctica evalúa todos los criterios de evaluación del **RA3**. Para su corrección se tendrá en cuenta:

1. Implementación del protocolo y mensajes (20%)
    - Correcta recepción y envío de mensajes según lo descrito en la práctica:
    - USUARIO, PASSWORD, REGISTRO, CONSONANTE, VOCAL, RESOLVER, SALIR, etc.
    - Respuestas adecuadas: +Ok. / –Err. con los textos de confirmación o error correspondientes.
    - Manejo de mensajes no válidos (respuestas de tipo “-Err. Mensaje no válido”).
    - Manejo adecuado de tamaños máximos de mensaje (hasta 200 caracteres).
2. Funcionalidad del juego individual (20%)
	- Lógica correcta para iniciar y finalizar partidas individuales.
	- Control de los intentos y asignación de puntuaciones (conforme a las reglas: menos de 5 intentos = 150 puntos, entre 5 y 8 = 100, etc.).
	- Posibilidad de RESOLVER la frase en cualquier momento y envío de mensajes adecuados (+Ok. Enhorabuena o +Ok. Le deseamos mejor suerte…).
	- Mantenimiento y actualización de la estadística de aciertos, fallos y puntuación total por usuario.
3. Funcionalidad del juego colectivo (25%)
	- Creación y manejo de grupos de tres jugadores (PARTIDA-GRUPO).
	- Control de turnos de cada jugador (permitir jugar sólo al usuario correspondiente, en caso contrario: “-Err. Debe esperar su turno”).
	- Gestión de puntos:
	    - +50 puntos por cada aparición de la consonante.
	    - –50 puntos al pedir una vocal (se necesita al menos 50 puntos para solicitarla).
	- Finalización correcta de la partida colectiva:
	    - Ganador designado en caso de que alguien falle al RESOLVER.
	    - Comunicación de puntuaciones finales y notificación al resto de jugadores.
	- Manejo de la salida de un jugador (mensaje SALIR) y continuidad del juego con el resto, cuando sea posible.
4. Manejo de concurrencia y varios clientes (15%)
    - Uso adecuado de hilos para gestionar múltiples conexiones simultáneas.
	- Control del número máximo de 50 clientes conectados.
	- Evitar bloqueos o comportamientos indeterminados al manejar varios clientes en paralelo.
5. Estructura y calidad del código (10%)
	- Claridad y organización del código fuente (modularización, funciones, clases, etc.).
	- Legibilidad: uso de nombres de variables adecuados, comentarios, e indentación coherente.
	- Manejo adecuado de excepciones o errores a nivel de implementación (control de flujos, cierres de sockets, etc.).
6. Documentación y guía de uso (10%)
	- Instrucciones claras de compilación y ejecución (cliente y servidor).
	- Explicación de cómo se gestiona cada comando y su flujo dentro del juego (diagrama o descripción).
	- Descripción de las funciones más relevantes en el código.
	- Inclusión de un breve manual de usuario con ejemplos de interacción (entrada/salida) para cada modo de juego.

## Método de entrega

Comprime el proyecto junto con la documentación en un archivo ZIP y súbelo a la plataforma Moodle Centros en el lugar dedicado a ello. El archivo ZIP deberá tener el siguiente formato:

**Apellido1Apellido2_Nombre_PSP_UD3_P2.zip**