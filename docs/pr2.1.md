# Práctica 2.1 - Programación multihilo en Java

## Ejercicio 1

Crea una clase que extienda de Thread cuya única funcionalidad sea visualizar el mensaje "Hola mundo". Crea un programa Java que visualice el mensaje anterior 5 veces creando para ello 5 hilos diferentes usando la clase creada  anteriormente. Modifica el mensaje "Hola mundo" en el hilo para incluir el identificador del hilo. Prueba de nuevo el programa Java creado  anteriormente.

## Ejercicio 2

Crea una clase que implemente la interfaz Runnable cuya única funcionalidad sea visualizar el mensaje "Hola mundo" seguido de una cadena que se recibirá en el constructor (es  decir al crear un objeto de este tipo se enviará una cadena) y seguido del identificador del hilo. Crea un programa Java que visualice el mensaje anterior 5 veces creando para ello 5 hilos  diferentes usando la clase creada anteriormente. Luego haz que antes de visualizar el mensaje el hilo espere un tiempo proporcional a su identificador; usa para ello el método sleep(). ¿Qué diferencias observas al ejecutar el programa usando o no el método sleep()?

## Criterios de evaluación

Esta práctica evalúa los criterios de evaluación **a)**, **b)**, **c)**, **d)** y **h)** del **RA2**. Para su corrección se tendrá en cuenta:

1. Funcionalidad del ejercicio 1 (3,5 puntos)
	- Implementa adecuadamente todos los requisitos de la aplicación.
2. Funcionalidad del ejercicio 2 (3,5 puntos)
	- Implementa adecuadamente todos los requisitos de la aplicación.
3. Calidad del código y buenas prácticas (0,5 puntos)
    - Código legible y bien estructurado, con indentación adecuada y nombres de variables descriptivos.
	- Uso de comentarios y documentación donde sea necesario.
4. Manejo de errores y validación de entradas (0,5 puntos)
	- Validación correcta de las entradas del usuario.
	- Mensajes de error claros y útiles en caso de entradas inválidas.
5. Ejecución y salida correcta (1 punto)
	- Las aplicaciones se ejecutan sin errores y producen la salida esperada.
6. Respuesta a las cuestiones (1 punto)
    - Las cuestiones que se plantean se contestan de manera satisfactoria.

## Método de entrega

Comprime todos los ejercicios, separados por carpetas, en un archivo ZIP y súbelo a la plataforma Moodle Centros en el lugar dedicado a ello. El archivo ZIP deberá tener el siguiente formato:

**Apellido1Apellido2_Nombre_PSP_UD2_P1.zip**