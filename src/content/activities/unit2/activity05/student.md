```
let port;
let connectBtn;

function setup() {
        createCanvas(400, 400);
    background(220);
    port = createSerial();
    connectBtn = createButton('Connect to micro:bit');
    connectBtn.position(135, 300);
    connectBtn.mousePressed(connectBtnClick);
      img1Btn = createButton('h');
      img1Btn.position(135, 250);
      img1Btn.mousePressed(img1BtnClick);
      img2Btn = createButton('j');
      img2Btn.position(155, 250);
      img2Btn.mousePressed(img2BtnClick);
  



    fill('white');

    x=200;
}

function draw() {
    background(220);


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
function img1BtnClick() {
    port.write('h');
}
function img2BtnClick() {
    port.write('j');
}
```

```
from microbit import *

uart.init(baudrate=115200)


while True:
    if uart.any():
        data = uart.read(1)
        if data:
            if data[0] == ord('h'):
                display.show('h')
                sleep(500)
            if data[0] == ord('j'):
                display.show('j')
                sleep(500)
            
```
