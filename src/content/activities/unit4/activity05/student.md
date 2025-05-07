original: https://editor.p5js.org/Nicofon1/sketches/4TyJH8nI4

```js
let port;
let connectBtn;
let microBitConnected = false;

const STATES = {
  WAIT_MICROBIT_CONNECTION: "WAITMICROBIT_CONNECTION",
  RUNNING: "RUNNING",
};
let appState = STATES.WAIT_MICROBIT_CONNECTION;
let microBitX = 0;
let microBitY = 0;
let microBitZ = 0;
let microBitX1 = 0;
let microBitY1 = 0;
let microBitZ1 = 0;
let microBitX2 = 0;
let microBitY2 = 0;
let microBitZ2 = 0;
let microBitX3 = 0;
let microBitY3 = 0;
let microBitZ3 = 0;



function setup() {
  
  createCanvas(800, 800, WEBGL);
  angleMode(DEGREES);
  strokeWeight(1);
  noFill();
  describe(
    'Users can click on the screen and drag to adjust their perspective in 3D space. The space contains a sphere of dark rgb(255,255,255) cubes on a light pink background.'
  );
  camera(0, 0, 0, 10, 20, 30, 0, 1, 0)
  
  port = createSerial();
  connectBtn = createButton("Connect to micro:bit");
  connectBtn.position(0, 0);
  connectBtn.mousePressed(connectBtnClick);
  
}

function connectBtnClick() {
  if (!port.opened()) {
    port.open("MicroPython", 115200);
  } else {
    port.close();
  }
}
function windowResized() {
  resizeCanvas(windowWidth, windowHeight);
}

function readData() {
  if (!port.opened()) {
    connectBtn.html("Connect to micro:bit");
    microBitConnected = false;
  } else {
    microBitConnected = true;
    connectBtn.html("Disconnect");
    if (port.availableBytes() > 0) {
      let data = port.readUntil("\n");
      if (data) {
        data = data.trim();
        let values = data.split(",");
          
          microBitX4 = microBitX3;
          microBitY4 = microBitY3;
          microBitZ4 = microBitZ3;
                  
          microBitX3 = microBitX2;
          microBitY3 = microBitY2;
          microBitZ3 = microBitZ2;
        
          microBitX2 = microBitX1;
          microBitY2 = microBitY1;
          microBitZ2 = microBitZ1;
        
        
        
        
        
          microBitX1 = int(values[0]);
          microBitY1 = int(values[1]);
          microBitZ1 = int(values[2]);
  
          microBitX = -(microBitX1+microBitX2+microBitX3+microBitX4)/4;
          microBitY = -(microBitY1+microBitY2+microBitY3+microBitY4)/4;
          microBitZ = -(microBitZ1+microBitZ2+microBitZ3+microBitZ4)/4;

        
      }
    }
  }
}
function draw() {
  stroke(31, 8, 64);
  
  background(250*2, 180*2, 200);
  	print(round(1000/deltaTime));
  readData();

  // Call every frame to adjust camera based on mouse/touch
  orbitControl();

  // Rotate rings in a half circle to create a sphere of cubes
  for (let zAngle = 0; zAngle < 170; zAngle += 25) {
    // Rotate cubes in a full circle to create a ring of cubes
    for (let xAngle = 0; xAngle < 360; xAngle += 10) {
      push();

      // Rotate from center of sphere
      rotateZ(zAngle);
      rotateX(xAngle);

      // Then translate down 400 units
      translate(0, 400, 0);

      torus(25,1);
      cone(20, 30, 4)
      pop();
      
    }
  }
  
  camera(microBitX, microBitY, microBitZ, 10, 20, 30, 0, 1, 0)
  
}
```


```py
# Imports go at the top
from microbit import *

uart.init(115200)
display.set_pixel(0,0,9)

while True:
    xValue = accelerometer.get_x()
    yValue = accelerometer.get_y()
    zValue = accelerometer.get_z()
    aState = button_a.is_pressed()
    bState = button_b.is_pressed()
    data = "{},{},{},{},{}\n".format(xValue, yValue, zValue, aState,bState)
    uart.write(data)
    sleep(50) # Envia datos a 10 Hz
```

https://editor.p5js.org/Nicofon1/sketches/rAWY--SdD

![image](https://github.com/user-attachments/assets/ca39170c-94e1-4bca-82d5-5070fa2f8179)
