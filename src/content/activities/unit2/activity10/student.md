#### Explicación resumida de la concurrencia en el programa

El programa usa una máquina de estados para cambiar entre varios estados (feliz, sonriente, triste) basándose en el tiempo y la presión del botón. Utiliza dos mecanismos clave de concurrencia:

1. **Temporizadores**: Cambian de estado tras intervalos de tiempo (por ejemplo, de feliz a sonriente después de 1.5 segundos).
2. **Eventos de botón**: Cambian de estado inmediatamente cuando se presiona el botón A, sin esperar el temporizador.

#### Vectores de prueba

1. **Prueba 1: Cambio de "HAPPY" a "SMILE" por temporizador**
   - **Condiciones**: El sistema está en STATE_HAPPY (1.5 segundos).
   - **Esperado**: Después de 1.5 segundos, el sistema debe cambiar a STATE_SMILE.
   - **Resultado**: El cambio ocurre correctamente y el temporizador se ajusta a 1 segundo.
   
2. **Prueba 2: Cambio de "SMILE" a "SAD" por temporizador**
   - **Condiciones**: El sistema está en STATE_SMILE (1 segundo).
   - **Esperado**: Después de 1 segundo, el sistema debe cambiar a STATE_SAD.
   - **Resultado**: El cambio ocurre correctamente y el temporizador se ajusta a 2 segundos.

3. **Prueba 3: Cambio de "HAPPY" a "SAD" por presión del botón A**
   - **Condiciones**: El sistema está en STATE_HAPPY y se presiona el botón A.
   - **Esperado**: El sistema debe cambiar inmediatamente a STATE_SAD al presionar el botón.
   - **Resultado**: El cambio de estado ocurre correctamente y el temporizador se ajusta a 2 segundos.
