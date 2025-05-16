1. Compara el código original con el anterior. ¿Qué notas de diferente?
+ El código original parece estar configurado para un proyecto de diseño generativo más amplio. El nuevo index.html se ha simplificado significativamente, eliminando estas dependencias y añadiendo específicamente la biblioteca p5.webserial para la comunicación con el micro:bit.
2. Reflexiona ¿Para qué se usan estas imágenes? ¿Qué representan?

+ Son "pinceles" o módulos de línea para dibujar formas distintas controladas por el micro:bit.
3. ¿Recuerdas que en las unidades anteriores teníamos un pseudoestado llamado INIT? ¿Dónde está?

+ La función setup() cumple el rol de INIT, realizando la configuración inicial.
4. ¿Qué pasaría al hacer clic en el botón?

+ Alterna entre abrir (si está cerrado) y cerrar el puerto serial.
5. ¿Para qué abres el puerto serial?

+ Para recibir datos del micro:bit (posición y estado de botones).
6. ¿Por qué solo se leen datos con el puerto abierto?

+ La comunicación solo es posible con una conexión activa.
7. ¿Se pueden leer datos con el puerto cerrado?

+ No.
8. ¿Qué pasa si el micro:bit envía datos con el puerto cerrado?

+ Los datos se pierden.
9. ¿Qué pasa si el micro:bit no envía "\n"?

+ readUntil() esperará indefinidamente, y los datos no se procesarán.
10. ¿Por qué se suma windowWidth/2 y windowHeight/2 a x e y?

+ Para centrar el origen de coordenadas del micro:bit en el centro de la ventana.
11. ¿Cómo verificar los eventos keyPressed y keyReleased?

+ Observar mensajes en la consola (print) y el comportamiento visual de la aplicación.
12. ¿Qué hace updateButtonStates? ¿Por qué el estado anterior? ¿Qué pasaría sin él?

+ Detecta cuándo se presionan y sueltan los botones. El estado anterior es necesario para detectar la transición. Sin él, las acciones se ejecutarían continuamente mientras el botón esté en un estado.
13. ¿Diferencias entre códigos? ¿Eventos del ratón? ¿Barra espaciadora?

+ El nuevo código se centra en el control del micro:bit. Eventos del ratón originales probablemente reemplazados por botones y acelerometro del micro:bit.
