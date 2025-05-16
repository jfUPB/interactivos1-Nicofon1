+ ¿Ves algún error relacionado con la conexión? ¿Qué indica?+
  + que no se pudo tener la coneccion
```
Failed to load resource: net::ERR_CONNECTION_REFUSEDUnderstand this error
socket.io/?EIO=4&transport=polling&t=PR5yHDE:1 
            
            
           Failed to load resource: net::ERR_CONNECTION_REFUSEDUnderstand this error
manager.js:108 
            
            
           GET http://localhost:3000/socket.io/?EIO=4&transport=polling&t=PR5yIMA net::ERR_CONNECTION_REFUSED
```
+ Vuelve a iniciar el servidor y refresca la página. ¿Desaparecen los errores?
  + si
+ ¿Qué pasó en page1 antes de que movieras page2?
  + apuntaba a donde no era
+ ¿Tenía la información correcta sobre page2 desde el principio?
  + no
+ ¿Por qué es útil enviar el estado inicial al conectarse?
  + para evitar errores como esos y poder desde el inicio tener informacion real de ambas partes una de la otra
+ Mueve la ventana de page1. Observa la consola del navegador de page2. ¿Se dispara el log “Page 2 received…”? ¿Qué datos muestra?
  + si `{x: 58, y: 217, width: 952, height: 673}`
+ ¿Se dispara este log? ¿Por qué sí o por qué no?
  + no, pq no tiene esta linea `console.log(remotePageData);` dentro de `socket.on('getdata', (dataWindow)`
+ ¿Cuándo aparece el mensaje “Page 2 detected change…”?
  + cuando se mueve la page 2

+ Deja la ventana de page2 quieta. ¿Aparece el mensaje?
  + no

+ ¿Por qué es eficiente esta estrategia de comparar con el estado anterior antes de enviar datos por la red? Anota tu reflexión.
  + pq, evita envios y procesamiento del servidor inecesarios
![image](https://github.com/user-attachments/assets/5b212a9b-5c0d-4748-af21-a5f68202031b)

