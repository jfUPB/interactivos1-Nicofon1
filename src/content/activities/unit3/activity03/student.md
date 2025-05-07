``` py
from microbit import *
import music
import utime
STATE_INIT = 0
STATE_CONFIG = 1
STATE_ARMED = 2
STATE_BOOM = 3
pitch_value = 6500
BOOM_TIME = 10000
print("hola")
start_time = 0
current_state = STATE_CONFIG
arr = ""
event = ""
uart.init(baudrate=115200)

def Event():
    global event
    
    data = uart.read(1)
    if data:
        if data[0] == ord('a')|button_a.is_pressed():
            event = "a"
        if data[0] == ord('b')|button_b.is_pressed():
            event = "b"
        if data[0] == ord('s')|accelerometer.is_gesture('shake'):
            event = "s"
        if data[0] == ord('t')|pin_logo.is_touched():
            event = "t"
    if button_a.was_pressed():
        event = "a"
    if button_b.was_pressed():
        event = "b"
    if accelerometer.was_gesture('shake'):
        event = "s"
    if pin_logo.is_touched():
        event = "t"
        
                                           


def Bomba():
    global current_state,BOOM_TIME,arr,start_time,pitch_value,event

    if current_state == STATE_CONFIG:
        music.stop()
        pitch_value = 5500
        arr = ""
        display.scroll(int(BOOM_TIME/1000), delay=70)
        if event == "a":
            if BOOM_TIME < 60000:
               BOOM_TIME+= 1000
            else:
                music.set_tempo(bpm=400)
                music.play(['c7', 'c7'])

        elif event == "b":
            if BOOM_TIME > 10000:
               BOOM_TIME-= 1000
            else:
                music.set_tempo(bpm=400)
                music.play(['c7', 'c7'])
        if event == "s":
            current_state = STATE_ARMED
            start_time = utime.ticks_ms()
        event=""


    elif current_state == STATE_ARMED:
        if event == "a":
            arr = arr+"a"
            print("aaaaaa")
        if event == "b":
            arr = arr+"b"
        if event == "s":
            arr = arr+"s"
        display.scroll(round((BOOM_TIME - utime.ticks_diff(utime.ticks_ms(), start_time))/1000), delay= 70)
        print(arr)
        if arr == "abas":
            current_state = STATE_CONFIG
            music.play(['c6','c6'])
        if utime.ticks_diff(utime.ticks_ms(), start_time) > BOOM_TIME:
            current_state = STATE_BOOM
            start_time = utime.ticks_ms()
        event=""



    elif current_state == STATE_BOOM:
        if utime.ticks_diff(utime.ticks_ms(), start_time) > 3300:
            if event == "t":
                    current_state = STATE_CONFIG
            music.stop()
        else:
            music.pitch(pitch_value)
            if pitch_value > 100:
                pitch_value -= 4




            if utime.ticks_diff(utime.ticks_ms(), start_time) > 2500:
                display.show(Image.SKULL)

            else:
                if utime.ticks_diff(utime.ticks_ms(), start_time) > 0:
                    display.show(Image('00000:'
                                       '00000:'
                                       '00900:'
                                       '00000:'
                                       '00000'))
                if utime.ticks_diff(utime.ticks_ms(), start_time) > 500:
                    display.show(Image('00000:'
                                       '00900:'
                                       '09090:'
                                       '00900:'
                                       '00000'))
                if utime.ticks_diff(utime.ticks_ms(), start_time) > 1000:
                    display.show(Image('00900:'
                                       '09090:'
                                       '90009:'
                                       '09090:'
                                       '00900'))
                if utime.ticks_diff(utime.ticks_ms(), start_time) > 1500:
                    display.show(Image('09090:'
                                       '90009:'


                                       '00000:'
                                       '90009:'
                                       '09090'))
                if utime.ticks_diff(utime.ticks_ms(), start_time) > 2000:
                    display.show(Image('90009:'
                                       '00000:'
                                       '00000:'
                                       '00000:'
                                       '90009'))

while True:
    Bomba()
    Event()
```
