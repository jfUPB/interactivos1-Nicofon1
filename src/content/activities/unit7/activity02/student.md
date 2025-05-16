#### + Explica con tus propias palabras: ¿Por qué es necesario Dev Tunnels en este escenario y cómo funciona conceptualmente?  
  + para poderse conectar desde una red externa a nuestro servidor local sin exponer nuestra ip de manera peligrosa, dev tunnels funciona como un intermediario para comunicas servidor cliente en linea

#### + ¿Por qué usamos `JSON.stringify()` en el emisor (móvil) y `JSON.parse()` en el receptor (escritorio)? ¿Qué problema resuelve JSON aquí?  
  + `JSON.stringify()` es para pasar de json a string y como el movir es el q recive el input es el q debe enviar la info recolectada
  + `JSON.parse()` es para pasar de string a json y y lo usa el pc para poderl leer el input enviado y generar el output

#### + Describe la función de `touchMoved()` y por qué se usa la variable `threshold` en el cliente móvil.  
  + touch muved se ejecuta cada q el tactil del movil registra un movimiento y el treshold funciona como omisor de movimientos minimos que probablemente son involuntarios y tmbn evitar enviar demasiados datos e inecesarios

#### + ¿Qué otros eventos táctiles existen en p5.js y para qué tipo de interacciones podrían ser útiles (ej. un botón virtual, detectar un tap)?  
  + `touchStarted()` funcionaria parabotones de accion rapida tan pronto se tocan se ejecutas
  + `touchEnded()` por ejemplo cuanto tiempo se oprime algo solo toca registra cuando toco y cuando dejo de tocar, en vez de comprovar si todo el tiempo se esta tocando

#### + Compara brevemente Dev Tunnels con simplemente usar la IP local. ¿Cuáles son las ventajas y desventajas de cada uno?  
  + las ventajas es q cualquier persona en el mundo podria usar lo q hago si nos ponemos de acuredo q ahora q caigo en cuenta me sirve para q otras personas de otras ciudades testeen mi app de flutter sin q tengan q descargar el apk, ps se q tendria q acordar tiempos pero es algo q si necesitava
  + no c q desventaja tendria a comparacion
