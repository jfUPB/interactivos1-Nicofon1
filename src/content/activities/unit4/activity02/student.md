unciones:
1. preload():
Esta función se ejecuta antes de setup() y se utiliza para cargar los archivos SVG (módulos gráficos) que se utilizarán para el dibujo. Los módulos son imágenes SVG que se cargan con loadImage(). Los módulos se guardan en el arreglo lineModule[].

2. setup():
Se ejecuta una sola vez al inicio. Se crea el lienzo con createCanvas(windowWidth, windowHeight) para que ocupe toda la ventana del navegador. Se establece el fondo en blanco con background(255) y se desactiva el cursor con noCursor(). También se define un color por defecto para las líneas con color(181, 157, 0) y el grosor de la línea con strokeWeight(0.75).

3. windowResized():
Esta función se llama cuando el tamaño de la ventana cambia, y ajusta el lienzo al nuevo tamaño con resizeCanvas(windowWidth, windowHeight).

4. draw():
Esta función se llama en cada fotograma y es donde ocurre el dibujo interactivo. Si el ratón está presionado (mouseIsPressed), se dibujan elementos en la posición actual del ratón. Si la tecla Shift está presionada, se limita el dibujo a una dirección (horizontal o vertical), es decir, el usuario puede dibujar en línea recta en una dirección específica.

  Rotación: La imagen o línea que se dibuja se rota en función del valor de angle y angleSpeed.

  Si el lineModuleIndex no es 0, se utiliza un SVG del arreglo lineModule[] para dibujar (con el tamaño especificado en lineModuleSize). Si el lineModuleIndex es 0, se dibuja una línea simple.

  Cada vez que se dibuja un elemento, el ángulo de rotación (angle) se incrementa en angleSpeed, haciendo que los elementos giren mientras se dibujan.

5. mousePressed():
Cada vez que el usuario presiona el ratón, se establece un nuevo tamaño aleatorio para el módulo de línea (lineModuleSize) y se recuerdan las posiciones del clic en clickPosX y clickPosY. Estas posiciones se utilizan para determinar la dirección en la que se dibujará el siguiente elemento.

6. keyPressed():
Esta función se ejecuta cuando se presiona una tecla. Se utilizan varias teclas para cambiar la configuración del dibujo:

Flechas: Ajustan la velocidad de rotación (angleSpeed) y el tamaño del módulo de línea (lineModuleSize).

Teclas 5-9: Cambian el módulo gráfico que se utilizará para el dibujo (de 0 a 4, donde cada número corresponde a un SVG diferente).

7. keyReleased():
  Esta función se ejecuta cuando se suelta una tecla. Tiene varias funcionalidades importantes:

  Tecla 'S': Guarda el lienzo como una imagen PNG utilizando saveCanvas().

  Teclas de borrar (Delete/Backspace): Limpian el lienzo con background(255).

  Tecla 'D': Invierte la dirección de rotación y refleja el ángulo (cambia el signo de angleSpeed).

  Tecla 'Espacio': Cambia el color del pincel a un color aleatorio.

  Teclas 1-4: Cambian el color a una de las opciones predeterminadas.

  Teclas 5-9: Cambian el módulo de línea que se está utilizando (se asigna un valor diferente a lineModuleIndex).
