#### ¿Por qué es útil enviar los datos como un objeto JSON ({type: ‘touch’, x: …, y: …}) en lugar de simplemente enviar, por ejemplo, una cadena como “mouseX,mouseY”?  
+ Porque es más ordenado y fácil de leer o extender. Si después quiero mandar otros datos (tipo, color, presión), solo agrego más claves al objeto.

#### ¿Qué pasaría si quitaras la comprobación del `threshold`? ¿Cómo afectaría al rendimiento o la fluidez de la interacción?  
+ Se mandaría un mensaje por cada pixel de movimiento. Sería demasiado tráfico y podría hacer que se trabe o se atrase.

#### ¿Cómo adaptarías este código si quisieras que también respondiera al clic del ratón en un computador (para pruebas)?  
+ Podría usar `mouseMoved()` o `mousePressed()` de p5.js y poner el mismo `socket.emit(...)` ahí, igual que en `touchMoved()`.

#### ¿Por qué es importante usar `JSON.parse()` dentro de un bloque `try…catch`?  
+ Porque si el mensaje no es un JSON válido, da error y el programa se cae. Con `try…catch` sigue funcionando.

#### Si los canvas del móvil y del escritorio tuvieran tamaños diferentes (ej: móvil 300x300, escritorio 600x600), ¿cómo modificarías el código del escritorio para que la posición del círculo rojo refleje proporcionalmente la posición del toque en el móvil?  
+ Usaría `map()` para escalar las coordenadas:  
  `circleX = map(parsedData.x, 0, 300, 0, 600);`  
  `circleY = map(parsedData.y, 0, 300, 0, 600);`

#### ¿Qué tendrías que cambiar en el código del escritorio si el servidor, en lugar de retransmitir el evento como ‘message’, lo enviara como ‘updateDesktop’?  
+ Cambiar el listener a:  
  `socket.on('updateDesktop', (data) => { ... });`
  
#### ¿Cuál es el propósito principal de `mobile/sketch.js` y `desktop/sketch.js`?
+ **mobile/sketch.js:** Enviar al servidor las coordenadas del dedo cuando se mueve sobre el canvas.  
+ **desktop/sketch.js:** Recibir esas coordenadas del servidor y mover un círculo en el canvas del escritorio.

#### **Explica la función `touchMoved` en el móvil, incluyendo el uso del `threshold` y `JSON.stringify`.**  
+ Se llama cada vez que el usuario mueve el dedo. Si el movimiento es mayor al `threshold` o es el primer toque, se arma un objeto con las coordenadas y se convierte a texto con `JSON.stringify`. Luego se manda al servidor con `socket.emit`.

#### **Explica cómo el cliente de escritorio recibe (`socket.on`) y procesa (`JSON.parse`, chequeo de `type`) los datos para actualizar la posición del círculo.**  
+ Cuando llega un mensaje, lo intenta convertir de texto a objeto con `JSON.parse`. Si tiene tipo `"touch"`, usa sus coordenadas para actualizar la posición del círculo.
