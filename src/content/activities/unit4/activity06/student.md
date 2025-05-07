1. Protocolo y su importancia:

Reglas para el intercambio de datos. Crucial en serial para interpretación correcta.

2. Separación con comas:

Delimitadores para identificar valores individuales al recibirlos.

3. Carácter de fin de mensaje:

Indica cuándo se ha recibido un paquete completo de datos (readUntil()).

4. Máquina de estados:

Gestiona diferentes comportamientos según la conexión del micro:bit (esperando vs. ejecutando).

5. Formato de datos en micro:bit:

Cadena de texto con valores separados por comas y terminada en \n ("{},{},{},{}\n".format(...)).

6. Codificación ASCII:

Cada carácter se representa con un número. p5.js debe convertirlo a su tipo original.

7. port.availableBytes() > 0:

Evita leer cuando no hay datos, previniendo errores o bloqueos.

8. Eliminar retorno de carro/salto de línea:

Método trim().

9. Dividir cadena por espacios:

Función split(" ").

10. Convertir cadenas a números:

Para realizar operaciones matemáticas y evaluar estados booleanos correctamente.

11. Bytes enviados por micro:bit (ejemplo):

Los bytes que se enviarían (en representación ASCII) serían los siguientes (en decimal):

'1': 49
'2': 50
'3': 51
',': 44
'7': 55
'5': 53
'6': 54
',': 44
'F': 70
'a': 97
'l': 108
's': 115
'e': 101
',': 44
'T': 84
'r': 114
'u': 117
'e': 101
'\n': 10
Por lo tanto, la secuencia de bytes sería: 49, 50, 51, 44, 55, 53, 54, 44, 70, 97, 108, 115, 101, 44, 84, 114, 117, 101, 10.
