# Práctica 5.1 - Técnicas de programación seguras

## Desarrollo de la práctica

1. Obtén el hash de los contenidos de un fichero, el fichero se debe elegir del disco duro con la clase JFileChooser. El resumen se debe mostrar en hexadecimal. Utiliza los algoritmos SHA-256 y MD5 y comprueba los resúmenes generados.

2. Programa una aplicación Java que reciba como parámetros de entrada un fichero y una contraseña, cifre el contenido utilizando AES, almacene el resultado con un nombre de fichero distinto y borre el fichero original. Programar también la aplicación que realice la transformación inversa.

3. Crea un programa que genere una firma de un fichero. La firma consistirá en el resultado de cifrar con la clave privada un hash SHA-2 de 256 bits. La firma se guardará en un fichero con el mismo nombre que el fichero original, añadiendo *.firma* al final. Crea otro programa que verifique esta firma. Debe descifrar la firma con la clave pública para obtener el hash, y compararla con el hash calculado sobre el fichero.

4. Recupera un ejemplo de código de la unidad 3 sobre Sockets con TCP y modifica los programas cliente y servidor para que utilicen sockets seguros.

## Criterios de evaluación

Esta práctica evalúa todos los criterios de evaluación del **RA5**. Para su corrección se tendrá en cuenta la siguiente ponderación:

- Ejercicio 1: 20%.
- Ejercicio 2: 25%.
- Ejercicio 3: 35%.
- Ejercicio 4: 20%.

## Método de entrega

Comprime el proyecto junto con la documentación en un archivo ZIP y súbelo a la plataforma Moodle Centros en el lugar dedicado a ello. El archivo ZIP deberá tener el siguiente formato:

**Apellido1Apellido2_Nombre_PSP_UD5_P1.zip**