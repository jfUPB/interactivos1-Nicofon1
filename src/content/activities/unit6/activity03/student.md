+ ¿Por qué crees que es útil usar módulos o librerías en lugar de escribir todo desde cero? ¿Qué ventajas aporta?
  + porque no es necesario trabajar horas en algo q ya esta creado, funciona perfecto y es gratuito.
+ ¿Qué ocurre? ¿Por qué? ¿Qué mensaje ves en el navegador o en su consola de desarrollador (F12)?
  + se queda en blanco ya que no obtiene la info q necesita, en la consola aparece
```
Failed to load resource: the server responded with a status of 404 (Not Found)Understand this error
page1:1 Refused to execute script from 'http://localhost:3000/page1.js' because its MIME type ('text/html') is not executable, and strict MIME type checking is enabled.
```
+ Intenta acceder a http://localhost:3000/page1. ¿Funciona?
  + no, dice esto `Cannot GET /page1'`
+ Intenta acceder a http://localhost:3000/pagina_uno. ¿Funciona?
  + si
+ Abre http://localhost:3000/page1 en una pestaña. Observa la terminal del servidor. ¿Qué mensaje ves? Anota el ID.
  + da el id de la pagina uno, que coincide con el que se imprime dentro de la consola de chrome, y al cerrarse tambn coincide, lo mismo con la page 2
+ Mueve la ventana de page1 y 2. Observa la terminal del servidor. ¿Qué evento se registra (win1update o win2update)? ¿Qué datos (Data:) ves?
  +  con la uno `Received win1update from ID: BcGbqjl0h1JyNYElAAAB Data: { x: 794, y: 337, width: 400, height: 936 }` con la dos `Received win1update from ID: BcGbqjl0h1JyNYElAAAB Data: { x: 794, y: 326, width: 400, height: 947 }`
+ ¿Se actualiza la visualización en page2? ¿Por qué sí o por qué no?
  + el page 2 no La página page2 no recibe el mensaje porque socket.emit envía el mensaje únicamente al mismo cliente que lo originó (el mismo socket).
+ ¿Se actualiza la visualización en page2?
  + no
+ ¿Por qué sí o por qué no?
  + `socket.emit('getdata', page1);` solo envía el mensaje al **cliente actual** (el que envió el 'win1update'), **no a los demás clientes**. Por eso **page2 no se actualiza**.  
  + Al quitar `broadcast`, se pierde la difusión a otros clientes conectados. Solo el emisor recibe su propio cambio, lo cual no es útil en este caso de sincronización entre páginas. 
