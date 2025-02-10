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
        
