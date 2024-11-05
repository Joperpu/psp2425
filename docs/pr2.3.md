# Práctica 2.3 - Sincronización de hilos

## Ejercicio 1

Crea una clase para gestionar el saldo de una **Cuenta**. Debe tener métodos para obtener el saldo actual, hacer un ingreso (se incrementa al saldo), hacer un reintegro (se le resta al saldo), controlar si hay algún error por ejemplo si se hace un reintegro y no hay saldo; o si se hace un ingreso y el saldo supera el máximo; mostrar mensajes con los movimientos que se realicen. La cuenta recibe en su constructor el saldo actual y el valor máximo que puede tener.

Crea después la clase **Persona** que extienda Thread y que realice en su método run() 2  ingresos y 2 reintegros alternándolos y con algún sleep() en medio. Para crear los movimientos de dinero generar números aleatorios entre 1 y 500. El constructor de la clase debe llevar el nombre de la persona.

Crea en el método main() de la clase **Principal** un objeto Cuenta compartido por varios objetos Persona e inicia el proceso de realizar movimientos en la cuenta.

## Ejercicio 2

Desarrolla un programa en Java que simule el control de stock en un almacén. El almacén recibe piezas a intervalos regulares y también despacha piezas en otros momentos. Para implementar esta simulación, se utilizará el patrón de diseño mproductor-consumidor y se manejará mediante hilos para garantizar la concurrencia y la sincronización.

El almacén parte de 8000 piezas y tiene una capacidad máxima de 20000 piezas. Si la cantidad de piezas en el almacén alcanza su límite máximo, el productor debe esperar hasta que haya espacio disponible para agregar más piezas.

Las piezas entran al almacén cada 8 horas en cantidades aleatorias que oscilan entre 400 y 1000 piezas. 

Del almacén salen piezas cada 24 horas, a un ritmo de entre 2000 y 2500 piezas. Debe mostrarse el estado del stock de piezas en cada iteración del programa.

Clases a crear:

- **Almacen**: Esta clase representará el almacén y contendrá métodos para agregar y quitar piezas, así como para mostrar el estado actual del stock.
- **Productor**: Clase que implementará el hilo del productor. Su función será agregar piezas al almacén.
- **Consumidor**: Clase que implementará el hilo del consumidor. Se encargará de quitar piezas del almacén.
- **Main**: Clase principal que iniciará el programa, creará instancias de **Almacen**, **Productor** y **Consumidor**, y controlará la ejecución de los hilos.

Consideraciones:

- El almacén debe tener una capacidad máxima definida.
- Los hilos del productor y del consumidor deben operar de manera concurrente y sincronizada para evitar problemas de concurrencia en el almacén.
- El programa debe mostrar de manera clara y ordenada el estado actual del stock en el almacén en cada iteración.

## Criterios de evaluación

Esta práctica evalúa todos los criterios de evaluación del **RA2**. Para su corrección se tendrá en cuenta:

1. Funcionalidad de los ejercicios (5 puntos)
	- Implementa adecuadamente todos los requisitos de las aplicaciones.
2. Uso correcto de la sincronización de los hilos (3 puntos)
	- Implementa adecuadamente la sincronización de los hilos.
3. Calidad del código y buenas prácticas (0,5 puntos)
    - Código legible y bien estructurado, con indentación adecuada y nombres de variables descriptivos.
	- Uso de comentarios y documentación donde sea necesario.
4. Manejo de errores (0,5 puntos)
	- Mensajes de error claros y útiles.
5. Ejecución y salida correcta (1 punto)
	- Las aplicaciones se ejecutan sin errores y producen la salida esperada.

## Método de entrega

Comprime el proyecto en un archivo ZIP y súbelo a la plataforma Moodle Centros en el lugar dedicado a ello. El archivo ZIP deberá tener el siguiente formato:

**Apellido1Apellido2_Nombre_PSP_UD2_P3.zip**