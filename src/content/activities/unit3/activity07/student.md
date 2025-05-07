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
}

function draw() {
  background(220);
  Bomba();
}

function keyPressed() {
  if (key === 'A') event = "a";
  if (key === 'B') event = "b";
  if (key === 'S') event = "s";
  if (key === 'T') event = "t";
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
