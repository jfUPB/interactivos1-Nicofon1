```js
let port;
let connectBtn;

function setup() {
        createCanvas(400, 400);
    background(220);
    port = createSerial();
    connectBtn = createButton('Connect to micro:bit');
    connectBtn.position(135, 300);
    connectBtn.mousePressed(connectBtnClick);
    fill('white');
    
    x=200;
}

function draw() {
    background(220);

    if(port.availableBytes() > 0){
        let dataRx = port.read(1);
        if(dataRx == 'B'){
            x=x+5;
        }
      
        else if(dataRx == 'A'){
            x=x-5;
        }
        print(x);

      
    }
    circle(x, 200, 150);

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

```
from microbit import *

uart.init(baudrate=115200)
display.show(Image.BUTTERFLY)

while True:
    if button_a.is_pressed():
        uart.write('A')
        sleep(500)
    if button_b.is_pressed():
        uart.write('B')
        sleep(500)
    
```

Se mapea gracias a `if button_a.is_pressed():
        uart.write('A')
        sleep(500)` y  `if(dataRx == 'A')`
