1. **Prueba de transición de HAPPY a SAD (por presionar botón A):**
   - **Entrada:** Botón A presionado mientras está en estado HAPPY.
   - **Resultado esperado:** La bomba debería cambiar a estado SAD y mostrar la imagen correspondiente.
   - **Error encontrado:** En algunos casos, el sistema no reconocía el evento si el botón A se presionaba rápidamente.
   - **Corrección implementada:** Se introdujo un pequeño retraso entre la acción de presionar el botón y el cambio de estado para evitar problemas de rebote.

2. **Prueba de cambio de estado basado en tiempo (sin interacción del usuario):**
   - **Entrada:** El sistema cambia de HAPPY a SMILE después del tiempo definido.
   - **Resultado esperado:** El sistema debería cambiar a SMILE tras el tiempo estipulado.
   - **Error encontrado:** En algunos momentos, el tiempo de espera no se cumplía correctamente debido a la forma en que se calculaba el tiempo transcurrido.
   - **Corrección implementada:** Se ajustó el cálculo de la diferencia de tiempo utilizando `utime.ticks_diff()`.

3. **Prueba de cambio de estado de SMILE a SAD basado en tiempo:**
   - **Entrada:** El temporizador se cumple y el sistema cambia de SMILE a SAD sin interacción del usuario.
   - **Resultado esperado:** La bomba debe cambiar a estado SAD.
   - **Error encontrado:** En ocasiones, el cambio de estado no ocurría después del tiempo estipulado.
   - **Corrección implementada:** Se revisó la lógica del temporizador y se corrigió el ciclo de tiempo.

4. **Prueba de repetición de estado sin interacción:**
   - **Entrada:** El sistema pasa por todos los estados y vuelve a repetir el ciclo sin intervención.
   - **Resultado esperado:** El sistema vuelve al estado inicial sin fallos.
   - **Error encontrado:** N/A.
   - **Corrección implementada:** El ciclo se mantuvo estable.

5. **Prueba de la transición incorrecta entre estados:**
   - **Entrada:** El sistema pasa del estado SAD a SMILE incorrectamente.
   - **Resultado esperado:** El sistema debe pasar de SAD a HAPPY antes de llegar a SMILE.
   - **Error encontrado:** Se produjo un error en la transición que llevaba a un estado incorrecto.
   - **Corrección implementada:** Se reorganizaron las transiciones para que sigan el flujo correcto.
