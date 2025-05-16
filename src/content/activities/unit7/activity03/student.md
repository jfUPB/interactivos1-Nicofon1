#### + ¿Cuál es la función principal de `express.static('public')` en este servidor? ¿Cómo se compara con el uso de `app.get('/ruta', …)` del servidor de la Unidad 6?  
+ `express.static('public')` permite que el servidor entregue todos los archivos estáticos (HTML, JS, CSS) automáticamente desde la carpeta `public`. Es más eficiente que `app.get('/ruta')`, porque no hay que crear una ruta para cada archivo.

#### + Explica detalladamente el flujo de un mensaje táctil:  
**¿Qué evento lo envía desde el móvil? ¿Qué evento lo recibe el servidor? ¿Qué hace el servidor con él? ¿Qué evento lo envía el servidor al escritorio? ¿Por qué se usa `socket.broadcast.emit` en lugar de `io.emit` o `socket.emit` en este caso?**  
+ El móvil usa `socket.emit('message')` cuando el usuario mueve el dedo. El servidor recibe ese mensaje con `socket.on('message')`, lo imprime en consola y lo reenvía a los demás clientes usando `socket.broadcast.emit('message')`. Se usa `broadcast` para que no le llegue al que lo mandó (el móvil), sino solo al escritorio.

#### + Si conectaras dos computadores de escritorio y un móvil a este servidor, y movieras el dedo en el móvil, ¿Quién recibiría el mensaje retransmitido por el servidor? ¿Por qué?  
+ Los dos computadores de escritorio lo recibirían, porque el servidor usa `socket.broadcast.emit`, que manda el mensaje a todos menos al emisor (el móvil).


#### + ¿Qué información útil te proporcionan los mensajes `console.log` en el servidor durante la ejecución?  
+ Muestran cuándo se conecta o desconecta un cliente y qué mensajes envía. Sirve para ver si todo está funcionando bien y saber qué clientes están activos.
