```py
from microbit import *
import struct

uart.init(115200)
display.set_pixel(0, 0, 9)

while True:
    xValue = accelerometer.get_x()
    yValue = accelerometer.get_y()
    zValue = accelerometer.get_z()
    aState = button_a.is_pressed()
    bState = button_b.is_pressed()
    data = struct.pack('>3h2B', xValue, yValue, zValue, int(aState), int(bState))
    checksum = sum(data) % 256
    packet = b'\xAA' + data + bytes([checksum])
    uart.write(packet)
    sleep(50)  # Envía datos a 10 Hz
```

```js
let serialBuffer = []; // Buffer para almacenar bytes recibidos

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
let microBitAState = false;
let microBitBState = false;

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

function readSerialData() {
  // Acumula los bytes recibidos en el buffer
  let available = port.availableBytes();
  if (available > 0) {
    let newData = port.readBytes(available);
    serialBuffer = serialBuffer.concat(newData);
  }

  // Procesa el buffer mientras tenga al menos 10 bytes (tamaño de un paquete)
  while (serialBuffer.length >= 10) {
    // Busca el header (0xAA)
    if (serialBuffer[0] !== 0xaa) {
      serialBuffer.shift(); // Descarta bytes hasta encontrar el header
      continue;
    }

    // Si hay menos de 10 bytes, espera a que llegue el paquete completo
    if (serialBuffer.length < 10) break;

    // Extrae los 10 bytes del paquete
    let packet = serialBuffer.slice(0, 10);
    serialBuffer.splice(0, 10); // Elimina el paquete procesado del buffer

    // Separa datos y checksum
    let dataBytes = packet.slice(1, 9); // Ahora son 8 bytes de datos
    let receivedChecksum = packet[9];

    // Calcula el checksum sumando los datos y aplicando módulo 256
    let computedChecksum = dataBytes.reduce((acc, val) => acc + val, 0) % 256;

    if (computedChecksum !== receivedChecksum) {
      console.log("Checksum error in packet");
      continue; // Descarta el paquete si el checksum no es válido
    }

    // Si el paquete es válido, extrae los valores
    let buffer = new Uint8Array(dataBytes).buffer;
    let view = new DataView(buffer);
    microBitX1 = view.getInt16(0);
    microBitY1 = view.getInt16(2);
    microBitZ1 = view.getInt16(4); // Nuevo valor Z
    microBitAState = view.getUint8(6) === 1;
    microBitBState = view.getUint8(7) === 1;

    microBitX = -(microBitX1 + microBitX2 + microBitX3) / 3;
    microBitY = -(microBitY1 + microBitY2 + microBitY3) / 3;
    microBitZ = -(microBitZ1 + microBitZ2 + microBitZ3) / 3;

    // Desplazamiento de los valores para el promedio
    microBitX3 = microBitX2;
    microBitY3 = microBitY2;
    microBitZ3 = microBitZ2;
    microBitX2 = microBitX1;
    microBitY2 = microBitY1;
    microBitZ2 = microBitZ1;
  }
}

function draw() {
  stroke(31, 8, 64);
  background(250 * 2, 180 * 2, 200);
  print(round(1000 / deltaTime));

  if (microBitConnected) {
    readSerialData();
  }

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

      torus(25, 1);
      cone(20, 30, 4);
      pop();
    }
  }

  camera(microBitX * 0.1, microBitY * 0.1, microBitZ * 0.1, 10, 20, 30, 0, 1, 0); // Ajusta la sensibilidad
}
```


