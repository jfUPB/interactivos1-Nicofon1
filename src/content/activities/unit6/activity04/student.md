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
  + para evitar errores como esos y poder 
