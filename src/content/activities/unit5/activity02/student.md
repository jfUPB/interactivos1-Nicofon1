1. Captura el resultado del experimento anterior. ¿Por qué se ve este resultado?
   ![image](https://github.com/user-attachments/assets/b6fefc27-5209-4b2d-97bb-09ca0afaf91a)
   pq pa la representacion de texto se necesita ascci
2. Captura el resultado del experimento anterior. Lo que ves ¿Cómo está relacionado con esta línea de código?
   ![image](https://github.com/user-attachments/assets/dd3b3cf3-8669-4136-82e5-61048d8f2b58)
   esa es la forma gexadecimal del empaquetado binario de estos datos  xValue, yValue, int(aState), int(bState)
3. ¿Qué ventajas y desventajas ves en usar un formato binario en lugar de texto en ASCII?
   tiene la ventaja de su eficiencia y su velocidad pero su contra es que no es legible para depurar
4. ¿Cuántos bytes se están enviando por mensaje? ¿Cómo se relaciona esto con el formato '>2h2B'? ¿Qué significa cada uno de los bytes que se envían?
+ Bytes por mensaje: 6 bytes.

+ Relación con '>2h2B':

  + 2h = dos enteros de 16 bits (2 × 2 bytes = 4 bytes)

  + 2B = dos enteros de 8 bits (2 × 1 byte = 2 bytes)

+ Significado de cada byte:

  + Bytes 0-1: xValue (acelerómetro eje X)

  + Bytes 2-3: yValue (acelerómetro eje Y)

  + Byte 4: aState (estado del botón A)

  + Byte 5: bState (estado del botón B)
 
5.Recuerda de la unidad anterior que es posible enviar números positivos y negativos para los valores de xValue y yValue. ¿Cómo se verían esos números en el formato '>2h2B'?
Sí, es posible porque 'h' en '>2h2B' representa enteros con signo de 16 bits.

+ Positivo (ej. 1000) → 0x03E8 → Bytes: 03 e8

+ Negativo (ej. -1000) → 2’s complement: 0xFC18 → Bytes: fc 18

Ambos se codifican en 2 bytes usando complemento a 2 y orden big-endian.

6. ¿Qué diferencias ves entre los datos en ASCII y en binario? ¿Qué ventajas y desventajas ves en usar un formato binario en lugar de texto en ASCII? ¿Qué ventajas y desventajas ves en usar un formato ASCII en lugar de binario?
+ **Diferencias entre ASCII y binario:**

  - **Binario:** Más compacto (6 bytes), eficiente y rápido, pero no legible sin decodificación.
  - **ASCII:** Más grande (ej. 13+ bytes), fácil de leer y depurar, pero menos eficiente.

+ **Ventajas del binario:**  
  - Menor tamaño  
  - Mayor velocidad  
  - Ideal para sistemas con recursos limitados

+ **Desventajas del binario:**  
  - Difícil de interpretar manualmente  
  - Requiere código para decodificar

+ **Ventajas del ASCII:**  
  - Legible por humanos  
  - Fácil de depurar y usar con herramientas estándar

+ **Desventajas del ASCII:**  
  - Mayor tamaño  
  - Menor eficiencia en transmisión

