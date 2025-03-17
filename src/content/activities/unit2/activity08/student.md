Enunciado: analiza el siguiente código identificando estados, eventos y acciones. Responde las preguntas planteadas.

```python
from microbit import *
import utime

class Pixel:
    def __init__(self,pixelX,pixelY,initState,interval):
        self.state = "Init"
        self.startTime = 0
        self.interval = interval
        self.pixelX = pixelX
        self.pixelY = pixelY
        self.pixelState = initState

    def update(self):

        if self.state == "Init":
            self.startTime = utime.ticks_ms()
            self.state = "WaitTimeout"
            display.set_pixel(self.pixelX,self.pixelY,self.pixelState)

        elif self.state == "WaitTimeout":
            if utime.ticks_diff(utime.ticks_ms(),self.startTime) > self.interval:
                self.startTime = utime.ticks_ms()
                if self.pixelState == 9:
                    self.pixelState = 0
                else:
                    self.pixelState = 9
                display.set_pixel(self.pixelX,self.pixelY,self.pixelState)

pixel1 = Pixel(0,0,0,1000)
pixel2 = Pixel(4,4,0,500)

while True:
    pixel1.update()
    pixel2.update()
```

Este programa controla el parpadeo de dos píxeles en una pantalla de micro:bit usando una máquina de estados. Los píxeles cambian de estado entre encendido (`9`) y apagado (`0`) con diferentes intervalos de tiempo.

En el contexto del programa, se identifican los siguientes elementos:

### Estados:
- **Init**: Este es el estado inicial cuando el objeto `Pixel` se crea. En este estado, se configura el tiempo de inicio y se cambia al estado `WaitTimeout`.
- **WaitTimeout**: En este estado, el programa espera que pase el tiempo establecido por el `interval`. Dependiendo de si ha transcurrido el tiempo, cambia el estado del píxel y reinicia el tiempo de espera.

### Eventos:
- **Tiempo transcurrido**: El evento clave es verificar si ha pasado el tiempo especificado (`interval`) usando la condición:
```python
if utime.ticks_diff(utime.ticks_ms(),self.startTime) > self.interval:
```
Este evento determina si el programa debe cambiar el estado del píxel.

### Acciones:
- **Actualizar el tiempo de inicio**: Cuando se inicializa el píxel o cuando el tiempo ha transcurrido, se actualiza el tiempo de inicio con:
```python
self.startTime = utime.ticks_ms()
```
- **Actualizar el estado del píxel**: Dependiendo del estado actual del píxel, este cambia de encendido (`9`) a apagado (`0`) o viceversa:
```python
if self.pixelState == 9:
    self.pixelState = 0
else:
    self.pixelState = 9
display.set_pixel(self.pixelX,self.pixelY,self.pixelState)
```
Esto hace que el píxel parpadee en la pantalla del micro:bit.


