```
from microbit import *
import speech

uart.init(baudrate=115200)

while True:
    if button_a.is_pressed():
        speech.say('hola')
        
        sleep(500)
    if button_b.is_pressed():
        speech.say('adios')
        
        sleep(500)
```
