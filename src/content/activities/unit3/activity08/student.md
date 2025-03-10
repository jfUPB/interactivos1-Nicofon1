``` js
let STATE_CONFIG = 1;
let STATE_ARMED = 2;
let STATE_BOOM = 3;
let current_state = STATE_CONFIG;

let BOOM_TIME = 10000;
let start_time = 0;
let arr = "";
let pitch_value = 5500;
let event = "";

function setup() {
  createCanvas(400, 400);
  textAlign(CENTER, CENTER);
  textSize(32);
      connectBtn = createButton('Connect to micro:bit');
    connectBtn.position(80, 300);
    connectBtn.mousePressed(connectBtnClick);
      port = createSerial();
}

function draw() {
  background(220);
  Ebent();
  Bomba();
  
  print(arr);
  
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

function Ebent() {
  
  if (key === 'A') event = "a";
  if (key === 'B') event = "b";
  if (key === 'S') event = "s";
  if (key === 'T') event = "t";
  if(port.availableBytes() > 0){
        let dataRx = port.read(1);
        if(dataRx == 'A') event="a";
        if(dataRx == 'B') event="b";
        if(dataRx == 'S') event="s";
        if(dataRx == 'T') event="t";
        
            
        
  }
}

function Bomba() {
  let elapsed = millis() - start_time;
  
  if (current_state === STATE_CONFIG) {
    fill(0);
    text("Config: " + int(BOOM_TIME / 1000) + "s", width / 2, height / 2);
    
    if (event === "a" && BOOM_TIME < 60000) BOOM_TIME += 1000;
    if (event === "b" && BOOM_TIME > 10000) BOOM_TIME -= 1000;
    if (event === "s") {
      current_state = STATE_ARMED;
      start_time = millis();
      arr = "";
    }
  }
  
  else if (current_state === STATE_ARMED) {
    fill(0);
    text("Time: " + int((BOOM_TIME - elapsed) / 1000) + "s", width / 2, height / 2);
    arr += event;
    
    if (arr === "abas") {
      current_state = STATE_CONFIG;
    }
    if (elapsed > BOOM_TIME) {
      current_state = STATE_BOOM;
      start_time = millis();
    }
  }
  
  else if (current_state === STATE_BOOM) {
    let boom_elapsed = millis() - start_time;
    if (boom_elapsed > 3300) {
      fill(0);
      text(" ☠︎︎ ", width / 2, height / 2);
      if (event === "t") {
        current_state = STATE_CONFIG;
      }
    } else {
      fill(255, 0, 0);
      text("BOOM!", width / 2, height / 2);
    }
  }
  event = "";
}
```



``` py
# Imports go at the top
from microbit import *


# Code in a 'while True:' loop repeats forever
while True:
    if button_a.is_pressed():
        uart.write('A')
        sleep(400)
    if button_b.is_pressed():
        uart.write('B')
        sleep(400)
    if pin_logo.is_touched():
        uart.write('T')
        sleep(400)
    if accelerometer.is_gesture('shake'):
        uart.write('S')
        sleep(600)

```
