+ **¿Por qué fue necesario introducir framing en el protocolo binario?**
  + Para delimitar el inicio y fin de cada paquete de datos.

+ **¿Cómo funciona el framing?**
  + Usa un byte especial (ej. `0xAA`) para marcar el inicio del paquete.

+ **¿Qué es un carácter de sincronización?**
  + Byte que indica el comienzo de un paquete (ej. `0xAA`).

+ **¿Qué es el checksum y para qué sirve?**
  + Es una suma usada para verificar que los datos no se corrompieron.

+ **¿Qué hace la función concat en la función readSerialData()? ¿Por qué?**
  + Une los nuevos datos al buffer existente para acumularlos.

+ **En el código anterior qué significa 0xAA?**
  + Byte que marca el inicio de un paquete (sincronización).

+ **¿Qué hace shift y la instrucción continue? ¿Por qué?**
  + `shift()` elimina el primer byte. `continue` salta al siguiente ciclo si no es `0xAA`.

+ **¿Qué hace break si hay menos de 8 bytes? ¿Por qué?**
  + Sale del bucle porque no hay datos suficientes para un paquete.

+ **¿Diferencia entre slice y splice? ¿Por qué usar ambos?**
  + `slice()` copia sin modificar. `splice()` elimina del buffer. Se usan juntos para procesar y limpiar.

+ **¿Cómo opera reduce?**
  + Suma los valores del array para calcular el checksum.

+ **¿Por qué se compara el checksum enviado con el calculado?**
  + Para detectar errores en la transmisión.

+ **¿Qué hace continue en esa comparación? ¿Por qué?**
  + Salta el ciclo si hay error de checksum y evita procesar datos corruptos.

+ **¿Qué es un DataView? ¿Para qué se usa?**
  + Permite leer datos binarios como enteros o booleanos desde un buffer.

+ **¿Por qué hacer conversiones con DataView?**
  + Porque los datos binarios deben interpretarse según su tipo.
