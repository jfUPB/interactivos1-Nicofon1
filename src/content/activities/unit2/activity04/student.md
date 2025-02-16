``` js
let port;
let connectBtn;

function setup() {
        createCanvas(1000, 1000);
    background(220);
    port = createSerial();
    connectBtn = createButton('Connect to micro:bit');
    connectBtn.position(135, 300);
    connectBtn.mousePressed(connectBtnClick);
    fill('white');

    x=0;
    y=0;
 q = 0;
  b=0;
  angleMode(DEGREES);
}

function draw() {
b=0;
    if(port.availableBytes() > 0){
        let dataRx = port.read(1);
        if(dataRx == 'A'){
            b=-2.5;
        }
        if(dataRx == 'B'){
            b=+2.5;
        }
        if(dataRx == 'C'){
            x=x+(sin(q)*15);
            y=y+(cos(q)*15);

            print(q);
        }

    }
    background(220);

  q=q+b;


  ellipse((sin(q)*50)+x+200,(cos(q)*50)+y+200, 10, 10);
  triangle((sin(q)*50)+x+200,(cos(q)*50)+y+200,
           (sin(q+120)*50)+x+200,(cos(q+120)*50)+y+200,
           (sin(q+240)*50)+x+200,(cos(q+240)*50)+y+200);


    if (!port.opened()) {
        connectBtn.html('Connect to micro:bit');
    }
    else {
        connectBtn.html('Disconnect');
    }
}

function connectBtnClick() {
    if (!port.opened()) {
        port.open('MicroPython', 115200);
    } else {
        port.close();
    }
}
```


``` py
from microbit import *

uart.init(baudrate=115200)


while True:
    if button_a.is_pressed():
        uart.write('A')
        sleep(20)
    if button_b.is_pressed():
        uart.write('B')
        sleep(20)
    if pin_logo.is_touched():
        uart.write('C')
        sleep(100)
```
  
#### Experimento 1: Botón A
+ **¿Qué querías comprobar?**  
        Quería comprobar si al presionar el botón A en el micro:bit, el carácter 'A' se enviaría correctamente a través del puerto serial y se detectaría en p5.js, causando que el triángulo gire en sentido contrario.

+ **¿Cuál fue tu hipótesis?**  
        Si se presiona el botón A, entonces el valor de 'b' será -2.5, lo que hará que el triángulo gire en sentido contrario a las manecillas del reloj en p5.js.

+ **Los códigos involucrados en el experimento:**  
``` py
MicroPython (micro:bit):
from microbit import *

uart.init(baudrate=115200)

while True:
    if button_a.is_pressed():
        uart.write('A')
        sleep(20)
        
```

```js

if (dataRx == 'A') {
    b = -2.5;
}
```

+ **Descripción de los resultados:**  
  Al presionar el botón A, el triángulo comenzó a girar en sentido contrario a las manecillas del reloj. Al soltar el botón, el triángulo dejó de girar.

+ **Análisis de esos resultados:**  
        Esto confirma que el carácter 'A' se está enviando y recibiendo correctamente, afectando la variable 'b' en p5.js, lo que cambia la dirección de rotación del triángulo.

+ **Conclusiones:**  
        El micro:bit y p5.js se están comunicando de manera efectiva. El botón A puede usarse de manera confiable para controlar la rotación en sentido contrario.

#### Experimento 2: Botón B  
+ **¿Qué querías comprobar?**  
        Quería verificar si al presionar el botón B en el micro:bit, se enviaría el carácter 'B' y el triángulo giraría en el sentido de las manecillas del reloj en p5.js.

+ **¿Cuál fue tu hipótesis?**  
        Si se presiona el botón B, entonces el valor de 'b' será 2.5, haciendo que el triángulo gire en el sentido de las manecillas del reloj.

+ **Los códigos involucrados en el experimento:**    


```py

from microbit import *

uart.init(baudrate=115200)

while True:
    if button_b.is_pressed():
        uart.write('B')
        sleep(20)
```
        
``` js

if (dataRx == 'B') {
    b = 2.5;
}
```

+ **Descripción de los resultados:**  
 Al presionar el botón B, el triángulo giró en el sentido de las manecillas del reloj. Al soltarlo, el giro se detuvo.

+ **Análisis de esos resultados:**  
        Esto demuestra que el micro:bit está enviando correctamente el carácter 'B' y que p5.js está usando esta señal para ajustar la rotación en el sentido esperado.

+ **Conclusiones:**  
        El botón B controla de manera confiable la rotación en el sentido de las manecillas del reloj. La comunicación serial funciona correctamente en este caso.

#### Experimento 3: Botón virtual del logo  
+ **¿Qué querías comprobar?**  
        Quería comprobar si tocar el logo del micro:bit enviaría el carácter 'C' y haría que el triángulo se moviera hacia adelante en la pantalla de p5.js.

+ **¿Cuál fue tu hipótesis?**  
        Si se toca el logo, entonces el triángulo avanzará en la dirección en la que está apuntando.

+ **Los códigos involucrados en el experimento:**   

``` py
from microbit import *

uart.init(baudrate=115200)

while True:
    if pin_logo.is_touched():
        uart.write('C')
        sleep(100)
```
``` js
if (dataRx == 'C') {
    x = x + (sin(q) * 15);
    y = y + (cos(q) * 15);
}
```

+ **Descripción de los resultados:**  
        Al tocar el logo, el triángulo se movió hacia adelante en la dirección en la que estaba apuntando. Si se tocaba repetidamente, el triángulo seguía avanzando.

+ **Análisis de esos resultados:**  
        Esto demuestra que el carácter 'C' se envía y recibe correctamente, afectando las variables 'x' e 'y' en p5.js para mover el triángulo en la dirección deseada.

+ **Conclusiones:**  
        El botón virtual del logo puede usarse de manera confiable para controlar el movimiento hacia adelante. La integración entre micro:bit y p5.js funciona bien para esta funcionalidad.
