``` js
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
    
    a=0;
    b=0;
    c=0;
}

function draw() {

    if(port.availableBytes() > 0){
        let dataRx = port.read(1);
        if(dataRx == 'A'){
            a = random(0,250);
            b = random(0,250);
            c = random(0,250);
        }
      fill(a,b,c)
    square(100, 100, 200);
    }


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
    
```
