1. Comunicación: Micro:bit y p5.js se comunican por cable USB (conexión serial). El micro:bit manda datos de aceleración (X, Y) y estado de botones (A, B) como texto. Ejemplo: "-100, 250, True, False\n".

2. Protocolo: Es texto simple (ASCII). Los valores se separan con comas, y cada envío termina con un salto de línea (\n) para indicar el final del dato.

3. Lectura y transformación en p5.js:

        if (port.availableBytes() > 0) {
          let data = port.readUntil("\n");
          if (data) {
            data = data.trim();
            let values = data.split(",");
            if (values.length == 4) {
              microBitX = int(values[0]) + windowWidth / 2;
              microBitY = int(values[1]) + windowHeight / 2;
              microBitAState = values[2].toLowerCase() === "true";
              microBitBState = values[3].toLowerCase() === "true";
              updateButtonStates(microBitAState, microBitBState);
            }
          }
        }
4. Eventos de botones:
La función updateButtonStates() mira si el estado de un botón cambió desde la última vez. Si el botón A ahora está presionado (antes no lo estaba), se genera el evento "A pressed". Si el botón B ahora está suelto (antes estaba presionado), se genera "B released".
