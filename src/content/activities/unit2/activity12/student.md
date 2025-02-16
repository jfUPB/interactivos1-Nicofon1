```py
from microbit import *
import music
import utime 
STATE_INIT = 0
STATE_CONFIG = 1
STATE_ARMED = 2
STATE_BOOM = 3
pitch_value = 6500
BOOM_TIME = 10000

start_time = 0
current_state = STATE_CONFIG


while True:
    # pseudoestado STATE_INIT
    if current_state == STATE_CONFIG:
        music.stop()
        pitch_value = 5500
        
        display.scroll(int(BOOM_TIME/1000), delay=70)
        if button_a.was_pressed():
            if BOOM_TIME < 60000:
               BOOM_TIME+= 1000
            else:
                music.set_tempo(bpm=400)
                music.play(['c7', 'c7'])
                
        elif button_b.was_pressed():
            if BOOM_TIME > 10000:
               BOOM_TIME-= 1000
            else:
                music.set_tempo(bpm=400)
                music.play(['c7', 'c7'])
        if accelerometer.was_gesture('shake'):
            current_state = STATE_ARMED
            start_time = utime.ticks_ms()
    elif current_state == STATE_ARMED: 
        display.scroll(round((BOOM_TIME - utime.ticks_diff(utime.ticks_ms(), start_time))/1000), delay= 70)
        if utime.ticks_diff(utime.ticks_ms(), start_time) > BOOM_TIME:
            current_state = STATE_BOOM
            start_time = utime.ticks_ms()


            
    elif current_state == STATE_BOOM:
        
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
        if utime.ticks_diff(utime.ticks_ms(), start_time) > 3300:
            current_state = STATE_CONFIG
            
            
       
```
