+ ¿Qué pasaría si esa rampa se corta?
  + ps no se puede acceder a la informacion buscada
+ ¿Puedes identificar otros ejemplos de relaciones Cliente-Servidor en tu vida diaria (no necesariamente digitales)? Por ejemplo, al pedir comida en un restaurante. ¿Quién es el cliente y quién el servidor? ¿Qué se pide y qué se entrega?
  + cualquier tiendita de la esquina
  +  en el restaurante yo soy el cilente y chefs/meseros etc son el servidor
  +  yo pido un plato y ps me dan la comida
+ Toma la URL de tu sitio web favorito. Intenta identificar el protocolo, el nombre de dominio y la ruta (si la hay). ¿Qué crees que pasa si solo escribes el nombre de dominio (ej. www.google.com) sin una ruta específica? ¿Qué “página por defecto” crees que te envía el servidor?
  + `https://jfupb.github.io/interactivos1-Nicofon1/units/unit6/`
  +  la original es `https://jfupb.github.io` pero es privado o algo asi ent me aparece 404
  +  si tengo en cuenta `https://jfupb.github.io/interactivos1-Nicofon1` me tira la pagina preincipar y amedida que navego por las unidade va accediendo a las diferentes direcciones
+ ¿Qué similitudes encuentras?
  + que ambos son protocolos de comunicacin con unemisor y un receptor
+ ¿Qué diferencias clave ves?
  + que http es mucho mas complejo, el cliente tiene que identificarse, hay muchos mas procesos de seguridad y la comunicacion se termina al finalizar el envio del contenido de la pagina
+ ¿Por qué crees que HTTP necesita ser más complejo que un simple envío de bytes como hacías con el micro:bit?
  + por la seguridad, la estructura de datos,

**en github**
+ ¿Qué parte crees que es HTML (ej. los campos de texto, el botón)?
  + toda la divicion de seciones tipo header campos de ingrso de texto botones  
+ ¿Qué parte es CSS (ej. el color del botón, el tipo de letra)?
  + funtes,  colores, formato de los fobones animaciones
+ ¿Qué parte es JavaScript (ej. la comprobación de si escribiste algo antes de enviar, el mensaje de “contraseña incorrecta” que aparece sin recargar la página)?
  + toda lo que se encarga de la comunicacion con el server, tipo comits, cambios en configuraciones de usuarios etc
+ ¿Qué ventajas crees que tiene el modelo basado en eventos para una interfaz de usuario web?
  + es mucho mas eficiente y consume menos recursos ya que en estas intefaces no se requiere de una interactividad constante.
+ ¿Sería eficiente tener un bucle draw() redibujando toda la página 60 veces por segundo si nada ha cambiado?
  + para nada solo implicaria mayor consumo de recursos
+ ¿Por qué crees que podría ser útil usar JavaScript tanto en el cliente (navegador) como en el servidor?
  + esto evita tener que desarrollar un protocolo de comunicacion complejo entre los lenguajes
+ ¿Se te ocurre alguna ventaja para los desarrolladores?
  + supongo que a la hora de enviar la intancia de un objeto se puede mandar cruda sin necesidad de enviarla a travez de un string o json
+ Resume con tus propias palabras la diferencia fundamental entre una comunicación HTTP tradicional y una comunicación usando WebSockets/Socket.IO.
  + HTTP es comunicación puntual (petición-respuesta); WebSockets/Socket.IO es comunicación continua y bidireccional en tiempo real.
+ ¿En qué tipo de aplicaciones has visto o podrías imaginar que se usa esta comunicación en tiempo real?
  + Se usa en chats, juegos online, videollamadas, colaboraciones en vivo (como Google Docs) o seguimiento de ubicación en tiempo real.
