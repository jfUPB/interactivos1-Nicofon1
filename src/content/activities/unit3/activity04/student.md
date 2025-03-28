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
      img1Btn = createButton('a');
      img1Btn.position(135, 250);
      img1Btn.mousePressed(img1BtnClick);
      img2Btn = createButton('b');
      img2Btn.position(155, 250);
      img2Btn.mousePressed(img2BtnClick);
      img3Btn = createButton('t');
      img3Btn.position(185, 250);
      img3Btn.mousePressed(img3BtnClick);
      img4Btn = createButton('s');
      img4Btn.position(215, 250);
      img4Btn.mousePressed(img4BtnClick);




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
    port.write('a');
}
function img2BtnClick() {
    port.write('b');
}
function img3BtnClick() {
    port.write('t');
}
function img4BtnClick() {
    port.write('s');
}
```
