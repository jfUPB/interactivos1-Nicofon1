+ Describe con tus propias palabras cuál es la función del servidor Node.js en la arquitectura que exploramos. ¿Por qué los clientes p5.js no se comunican directamente entre sí?
  + El servidor Node.js hace como de intermediario entre los clientes. Los clientes no se comunican directo porque eso complicaría las conexiones, y el servidor organiza todo.

+ Explica la diferencia fundamental entre socket.emit() y socket.broadcast.emit() en el contexto de Socket.IO en el servidor. ¿Cuándo usarías cada uno?
  + `socket.emit()` envía al cliente que se conectó. `socket.broadcast.emit()` envía a todos menos al que mandó el mensaje. Uso el segundo cuando no quiero que el cliente que envió el dato lo reciba de nuevo.

+ Compara la comunicación mediante Node.js/Socket.IO con la comunicación serial (ASCII y binaria con framing) que viste en unidades anteriores. Menciona al menos una ventaja y una desventaja de cada enfoque según el contexto de aplicación (ej. conectar micro:bit vs. conectar dos navegadores).
  + Serial es más para hardware tipo micro:bit, y Socket.IO es para navegadores. Serial es directo pero más limitado, mientras que Socket.IO sirve para varias personas y es más flexible.

+ ¿Qué rol juega el protocolo http y qué rol juega socket.io (que usa WebSockets por debajo) en la aplicación del caso de estudio?
  + HTTP es para cargar la página. Socket.IO es para que los clientes hablen en tiempo real sin recargar.

+ ¿Qué fue lo más sorprendente o interesante que aprendiste sobre la comunicación en red en esta unidad?
  + desde hace rato tenia curiosidad de como hacer  back con un server y aunq aqui casi no hay back el uso de servidor si me gusto mucho y no es tan complejo como crei q seria.
