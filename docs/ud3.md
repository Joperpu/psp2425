# Unidad 3 - Programación de mecanismos de comunicación en red con sockets

## Modelos de comunicaciones entre procesos

En esta unidad didáctica se van a desarrollar aplicaciones concurrentes apropiadas para sistemas distribuidos. En ellos, los procesos se ejecutan en distintos procesadores de sistemas independientes, y se comunican a través de una red mediante protocolos estándares de comunicaciones.

Podemos encontrar dos modelos de sistemas distribuidos:

- Cliente servidor.
- Entre iguales (P2P).

<center>![Tipos de sistemas distribuidos](assets/images/ud3/img01.png){ width="700" }</center>

## Modelo TCP/IP

El modelo TCP/IP es una arquitectura de red compleja que integra múltiples protocolos organizados en capas. Sin lugar a dudas, es la arquitectura más utilizada a nivel mundial, ya que constituye la base de Internet y es ampliamente empleada en diversas versiones de sistemas operativos.

La arquitectura TCP/IP se desarrolló diseñando inicialmente los protocolos y luego estructurándolos en capas dentro de la arquitectura. Por esta razón, TCP/IP es frecuentemente referida como una pila de protocolos.

La arquitectura TCP/IP es la más utilizada hoy en día. Se utiliza tanto en redes de área extensa como en redes de área local. Fue creada a principios de los años 70 por el Departamento de Defensa de los Estados Unidos. El objetivo era crear una arquitectura de red con las siguientes características:

* Permitir interconectar redes distintas aunque utilicen distinta tecnología.
* Ser tolerante a fallos. Mantener las comunicaciones a pesar de que se destruya parte de la red.
* Suministrar los servicios de comunicación más utilizados en redes de ordenadores. Finalmente, este proyecto derivó en lo que hoy conocemos como Internet.

Los niveles o capas de este modelo son los siguientes:

1. **Capa de acceso a la red**: El modelo TCP/IP no proporciona detalles específicos sobre esta capa; simplemente establece que debe existir un protocolo que conecte el dispositivo a la red. Esto se debe a que TCP/IP fue diseñado para funcionar sobre diversas redes, por lo que esta capa depende de la tecnología utilizada y no está predefinida. Es importante considerar que una red puede estar interconectada mediante diferentes tipos de cables o de forma inalámbrica. En este nivel se definen los protocolos asociados a los dispositivos de bajo nivel para cada una de estas tecnologías.

2. **Capa de Internet o red**: Esta es la capa más esencial de la arquitectura. Su función es permitir que los dispositivos envíen paquetes de información a la red y que estos viajen de forma independiente hasta su destino. Durante el recorrido, los paquetes pueden atravesar diferentes redes y pueden llegar desordenados. Esta capa no se encarga de reordenar los mensajes en el destino. El protocolo más importante en este nivel es el IP (Internet Protocol), aunque también existen otros protocolos.

3. **Capa de transporte**: Su misión es establecer una comunicación confiable entre el origen y el destino, similar a la capa de transporte en el modelo OSI. Dado que las capas inferiores no gestionan el control de errores ni el ordenamiento de los mensajes, esta capa asume esas responsabilidades. En este nivel se han definido varios protocolos, destacando TCP (Transmission Control Protocol) y UDP (User Datagram Protocol).

4. **Capa de aplicación**: Al igual que en el modelo OSI, esta capa incluye todos los protocolos de alto nivel que utilizan las aplicaciones para comunicarse. Aquí se encuentran protocolos como FTP para la transferencia de archivos, HTTP que utilizan los navegadores para acceder a páginas web, y los protocolos para la gestión del correo electrónico, entre otros.

<center>![Modelo TCP/IP](assets/images/ud3/img02.png){ width="700" }</center>

<center>![Modelo TCP/IP](assets/images/ud3/img03.png){ width="700" }</center>

## Direcciones, puertos y sockets

### Direcciones IP

Cada host o equipo que está en una red TCP/IP tiene asignada na dirección IP única consistente en un número de red y un número de host. El número de red sirve para identificar la red en la que se encuentran los hosts. El número de
host sirve para identificar a un host dentro de una red.

- Las direcciones Ipv4 son direcciones de 32-bits. La dirección IP se agrupa en cuatro octetos o bytes (grupos de 8 bits) y se representan usando el valor en notación decimal de cada uno de los bytes, separados por puntos. El valor mínimo para cada octeto es 0 y el valor máximo es 255. Por ejemplo: 192.168.0.100
- Las direcciones IPv6 está formadas por 64-bits para la dirección de red o prefijo de red, y otros 64 bits para el número de host. Las direcciones IPv6 se escriben como 8 grupos de 4 dígitos hexadecimales separados por el carácter ':'. Un grupo que sólo tiene ceros puede ser omitido. Los ceros iniciales también se pueden omitir. Por ejemplo: 2001:0db8::1428:57ab

### Puertos

Cuando una aplicación que se está ejecutando en un equipo quiere comunicarse con otra aplicación de otro equipo, se identifica a sí misma con un número de 16 bits, que denominamos puerto. Ese identificador es usado por los protocolos de la capa de transporte (TCP or UDP) para entregar los mensajes a la aplicación correcta dentro del equipo. Los puertos van de 0 a 65535, y se agrupan en tres rangos.

| Grupo de puertos | Rango de puertos | Descripción |
| ----------------| ---------------- | ------------- |
| Puertos bien conocidos o puertos del sistema | 0 - 1023 | Los usan los protocolos estándar y los servicios del SO |
| Puertos registrados | 1024 - 49151 | Reservados por empresas y organizaciones para sus propios servicios | 
| Puertos efímeros | 49152 - 65535 | De libre disposición y uso para aplicaciones cliente y servidor |

### Sockets

Un socket es un punto final de conexión en una comunicación entre procesos y está formado por una combinación única de dirección IP, puerto y protocolo de transporte (normalmente TCP).

Cuando una aplicación cliente quiere comunicarse con un servidor, el SO crea el socket que usará el cliente para recibir la información del servidor. La combinación única de Protocolo + puerto + IP permite que este extremo de la
comunicación sea accesible desde el servidor, de manera inequívoca y asegura que los datos los recibe el proceso que los solicitó.

El servidor tiene su propio socket para comunicarse con el cliente, y una conexión establecida entre el cliente y el servidor usando los dos extremos (los dos sockets cliente <--> servidor). Las aplicaciones intercambian información escribiendo o leyendo en los sockets que han creado.

La conexión usada por un cliente está formada por dos sockets, uno en el lado del cliente y otro en el lado del servidor. Por lo tanto, la conexión puede identificarse con una tupla formada por cuatro número: la dirección IP de origen, la dirección IP de destino, el puerto de origen y el puerto de destino.

## TCP y UDP

El **Protocolo de Control de Transmisión** (Transmission Control Protocol o **TCP**) es un protocolo de la capa de transporte, por lo que su trabajo consiste en permitir la transmisión de paquetes de datos. TCP garantiza que los paquetes se entregan al destinatario de forma ordenada, completa y correcta. Se utiliza para la transferencia de información cuando es necesario garantizar la integridad de esta, como, por ejemplo, en la web o en la transferencia de archivos con FTP. Este protocolo está basado en conexiones, por lo que cuando se establece una comunicación entre dos nodos de la red se crea un cana estable a través del cual se envía la información.

El **Protocolo de Datagramas de Usuario** (User Datagram Protocol o **UDP**) es, al igual que TCP, un protocolo de la capa de transporte que posibilita la transmisión de paquetes de datos. Al contrario que TCP, UDP no está basado en conexiones. Esto significa que cada paquete se envía sin que exista un canal de comunicación abierto con el receptor,
por lo que cada paquete podrá alcanzar su destino por un camino distinto.

Por esta razón, entre otras, los paquetes de datos UDP (conocidos como datagramas) pueden no llegar a su destino en el mismo orden en el que se enviaron o incluso pueden “perderse” y no alcanzarlo. Este comportamiento sin garantías puede resultar llamativo, pero tiene sus ventajas. Al no tener que garantizar la entrega ni el orden, la
comunicación es mucho más rápida que cuando se usa el protocolo TCP, a cambio de aceptar la pérdida de algunos paquetes de información. Esta característica hace que UDP sea el protocolo más adecuado para algunas aplicaciones en las que la rapidez prevalece sobre la fiabilidad, como las transmisiones de voz o de vídeo en tiempo real.

## Clases Java para comunicaciones de red

El paquete java.net proporciona clases que permiten llevar a cabo comunicaciones entre procesos utilizando los protocolos estándares de la familia de TCP/IP. Puede dividirse en dos secciones.

- Clases de bajo nivel, que permiten representar las principales entidades de los niveles de enlace, red y transporte.
- Clases de alto nivel, relacionadas con protocolos de nivel de aplicación, que se verán en la siguiente unidad de trabajo.
