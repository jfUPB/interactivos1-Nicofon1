lo que queria hacer es que los page 1 mostrara circulos blancos que se expanden en un fondo negro cada q hace clik,a su vez q page 2 mostrara lo mismo pero con los colores opuestos y con cuadrados y q todo funcionara con posiciones globales de la pantalla 
para esto lo q tenia q hacer es crear una lista de obetos  tipo honda con posicion global, tamaño, color y alpha 
cada vez q se hace clikc tiene q agregar el ovjeto a la lista y avisarle al resto del evento enviando la posicion del objeto 
tmbn añadir q cada q se reciva  el evento de un nuevo objeto con su posicion añadirlo a la lista con caracteristicas init por asi decirlo
y por ultimo en el draw recorrer la lista  dibujarlo y dsps aumentar su tamaño y reducirle la opacidad  y si la opacidad llega a cero eliminarlo

#### server
``` js
const express = require('express');
const http = require('http');
const socketIO = require('socket.io');
const path = require('path');
const app = express();
const server = http.createServer(app);
const io = socketIO(server);
const port = 3000;

app.use(express.static(path.join(__dirname, 'views')));

app.get('/page1', (req, res) => {
    res.sendFile(path.join(__dirname, 'views', 'page1.html'));
});

app.get('/page2', (req, res) => {
    res.sendFile(path.join(__dirname, 'views', 'page2.html'));
});

io.on('connection', (socket) => {
    console.log('Usuario conectado:', socket.id);

    socket.on('disconnect', () => {
        console.log('Usuario desconectado:', socket.id);
    });

    socket.on('newhonda', (data) => {
        socket.broadcast.emit('drawhonda', data);
    });
});

server.listen(port, () => {
    console.log(`Servidor escuchando en http://localhost:${port}`);
});
```

#### page1
``` js
let socket = io('http://localhost:3000');
let hondas = [];

function setup() {
    createCanvas(windowWidth, windowHeight);
    background(0);
}

function windowResized() {
    resizeCanvas(windowWidth, windowHeight);
}

function mousePressed() {
    socket.emit('newhonda', { screenX: screenX + mouseX, screenY: screenY + mouseY});
    hondas.push({ x: screenX + mouseX, y: screenY + mouseY, size: 0, alpha: 255, color: 255 });
}

socket.on('drawhonda', (data) => {
    hondas.push({ x: data.screenX, y: data.screenY, size: 0, alpha: 255, color: 255 });
});

function draw() {
    background(0);
    for (let i = hondas.length - 1; i >= 0; i--) {
        let honda = hondas[i];
        noFill();
        stroke(honda.color, honda.alpha);
        strokeWeight(2);
        ellipse(honda.x - screenX, honda.y - screenY, honda.size);
        honda.size += 10;
        honda.alpha -= 2;
        if (honda.alpha <= 0) {
            hondas.splice(i, 1);
        }
    }
}
```

#### page2
``` js
let socket = io('http://localhost:3000');
let hondas = [];

function setup() {
    createCanvas(windowWidth, windowHeight);
    background(255);
}

function windowResized() {
    resizeCanvas(windowWidth, windowHeight);
}

function mousePressed() {
    socket.emit('newhonda', { screenX: screenX + mouseX, screenY: screenY + mouseY});
    hondas.push({ x: screenX + mouseX, y: screenY + mouseY, size: 0, alpha: 255, color: 0 });
}

socket.on('drawhonda', (data) => {
    hondas.push({ x: data.screenX, y: data.screenY, size: 0, alpha: 255, color: 0 });
});

function draw() {
    background(255);
    for (let i = hondas.length - 1; i >= 0; i--) {
        let honda = hondas[i];
        noFill();
        stroke(honda.color, honda.alpha);
        strokeWeight(2);
        rectMode(CENTER);
        rect(honda.x - screenX, honda.y - screenY, honda.size, honda.size);
        honda.size += 10;
        honda.alpha -= 2;
        if (honda.alpha <= 0) {
            hondas.splice(i, 1);
        }
    }
}
```

#### video
https://youtu.be/IBHH7j_R3WY

