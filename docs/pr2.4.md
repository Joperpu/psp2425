# Práctica 2.4 - Sincronización de hilos II

## Ejercicio 1

En una carretera de dos carriles que discurre de Norte a Sur (y de Sur a Norte) hay un puente estrecho de un solo carril. Por ese puente solo pueden circular vehículos en un solo sentido al mismo tiempo, con la regla de que, estando los vehículos circulando en un sentido, cuando haya N o más vehículos (N es un parámetro del problema) esperando a cruzar en sentido contrario, se impide que entren nuevos vehículos al puente en el sentido actual de la marcha, para permitir cambiar ésta cuanto antes. En el caso de que haya N o más vehículos esperando a cruzar en cada uno de los dos sentidos, se debe dar prioridad a los vehículos que suben, es decir, que van de Sur a Norte. 

Se pide escribir un objeto protegido dotado de cuatro operaciones (Entrar_Norte, Salir_Norte, Entrar_Sur, Salir_Sur) que implemente el protocolo anterior.

## Ejercicio 2

Una barbería tiene una sala de espera con n sillas y una habitación con un sillón donde se atiende a los clientes. Si no hay clientes el barbero se duerme. Si un cliente entra en la barbería pero todas las sillas están ocupadas, entonces se va, dejando la barbería. Si el barbero esta ocupado entonces el cliente se sienta en una de las sillas disponibles. Si el barbero esta dormido el cliente lo despertará. Escribir una aplicación que coordine el barbero y sus clientes de forma adecuada utilizando semáforos.

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

**Apellido1Apellido2_Nombre_PSP_UD2_P4.zip**