# Práctica 1.2 - Programación multiproceso

## Ejercicio 1

En este ejercicio debes realizar la multiplicación de 2 arrays de números enteros de dimensión 10. El resultado de la multiplicación es un nuevo array donde el elemento de posición 0 es igual a la multiplicación de posición 0 de los dos arrays, el de posición 1 multiplica las posiciones 1 de los dos arrays, y así sucesivamente.

Realiza un programa padre llamado *Ejecuta_Ejercicio1* que inicialice los arrays con números aleatorios y envíe a dos procesos hijos cuya clase se llama *Ejercicio1* la mitad de cada array. Los procesos hijos deben devolver la multiplicación de las partes de los arrays que les ha correspondido.

El proceso padre debe mostrar por consola el resultado de la multiplicación de los dos arrays que ha recogido de los procesos hijos.

## Ejercicio 2

Realiza un programa que lea por teclado en un proceso repetitivo datos de alumnos. Los datos de los alumnos que debe leer son el nombre (String) y la edad (int). El proceso repetitivo finaliza cuando el nombre sea *.

- Si el nombre leído es blanco o su longitud de caracteres es 0 se debe volver a leer.
- Si la edad no está comprendida entre 1 y 99, se debe volver a leer.
- Igualmente, se debe volver a leer si se introduce una cadena en lugar de un número en dicho campo.
- Se deben visualizar mensajes al pedir los datos y cuando no son correctos.

Una vez finalizado el proceso de lectura de los datos se debe mostrar al usuario un mensaje con el número de alumnos leídos, el nombre del alumno con más edad y el nombre del alumno con menos edad. Nombra al programa *Ejercicio2*.

A continuación, se muestra un ejemplo de la salida de ejecución del programa:

	1- Introduce datos de alumnos:

	Escribe un nombre:
	JUAN

	Introduce la edad entre 1 y 99:
	10

	Datos introducidos: JUAN, 10

	2- Introduce datos de alumnos:

	Escribe un nombre:
	PEDRO

	Introduce la edad entre 1 y 99:
	16

	Datos introducidos: PEDRO, 16

	3- Introduce datos de alumnos:

	Escribe un nombre:

	Incorrecto, escríbelo de nuevo:

	Escribe un nombre:
	ANA

	Introduce la edad entre 1 y 99:
	0

	Incorrecto, debe estar entre 1 y 99

	Introduce la edad entre 1 y 99:
	33

	Datos introducidos: ANA, 33

	4- Introduce datos de alumnos:

	Escribe un nombre:
	*

	Fin del proceso de lectura...

	Datos leídos: 3

	Alumno con más edad: ANA
	
	Alumno con menos edad: JUAN

Realiza otro programa Java para ejecutar *Ejercicio2*. Este programa recibe desde los argumentos de main() el nombre de los ficheros que contendrán los datos de entrada para la ejecución del programa *Ejercicio2*. Pueden ser varios ficheros. El programa *Ejercicio2* se ejecutará tantas veces como ficheros hay en los argumentos del main().

La salida de las distintas ejecuciones del programa se debe almacenar en un fichero, cuyo nombre coincidirá con el del fichero de entrada, pero añadiendo una letra **S** al principio del nombre del mismo. También la salida de error de cada ejecución se almacenará en otro fichero, cuyo nombre será el mismo que el nombre del fichero de entrada, pero añadiendo la letra **E** al principio del nombre del mismo.

Si el programa no recibe los argumentos requeridos (1 o más) debe mostrar un mensaje y finalizar la ejecución.

Si alguno de los nombres de fichero indicados en los argumentos de main() no existe, se debe mostrar un mensaje indicándolo.

El programa debe mostrar en pantalla el número de veces que se ejecuta *Ejercicio2* y el mensaje de fin de proceso.

El programa debe crear tantos ficheros de salida como ficheros de entrada existan. Por ejemplo, si los ficheros de entrada se llaman *Fichero1.txt*, *Fichero2.txt* y *Fichero3.txt*, y existen, se deben generar los ficheros de salida *SFichero1.txt*, *SFichero2.txt* y *SFichero3.txt*.

Igualmente, se deben crear tantos ficheros de salida de error como ficheros de entrada (siempre y cuando los ficheros de entrada existan). En este caso *EFichero1.txt*, *EFichero2.txt* y *EFichero3.txt*, los cuales se encontrarán vacíos si no se produce ningún error.

Este programa se llamará *Ejecuta_Ejercicio2*.

Un ejemplo del contenido del fichero con datos de alumnos podría ser el siguiente:

	FELIPE 19
	PABLO 21
	MARIA 11
	IVAN 1000
	*


## Criterios de evaluación

Esta práctica evalúa los criterios de evaluación **e)**, **f)**, **g)** y **h)** del **RA1**. Para su corrección se tendrá en cuenta en cada uno de los ejercicios:

1. Funcionalidad de la aplicación *Hija* (1,5 puntos)
	- Implementa adecuadamente todos los requisitos de la aplicación.
2. Funcionalidad de la aplicación *Padre* (2 puntos)
	- Implementa adecuadamente todos los requisitos de la aplicación.
3. Calidad del código y buenas prácticas (0,5 puntos)
    - Código legible y bien estructurado, con indentación adecuada y nombres de variables descriptivos.
	- Uso de comentarios y documentación donde sea necesario.
4. Manejo de errores y validación de entradas (0,5 puntos)
	- Validación correcta de las entradas del usuario.
	- Mensajes de error claros y útiles en caso de entradas inválidas.
5. Ejecución y Salida Correcta (0,5 puntos)
	- Las aplicaciones se ejecutan sin errores y producen la salida esperada.

## Método de entrega

Comprime todos los ejercicios, separados por carpetas, en un archivo ZIP y súbelo a la plataforma Moodle Centros en el lugar dedicado a ello. El archivo ZIP deberá tener el siguiente formato:

**Apellido1Apellido2_Nombre_PSP_UD1_P2.zip**