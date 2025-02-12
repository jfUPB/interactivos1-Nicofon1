from microbit import *
import utime

class Sem:
    def __init__(self,V1,initState,interval):
        self.state = "Init"
        self.startTime = 0
        self.interval = interval
        self.pixel1 = (V1[0],V1[1])
        self.pixel2 = (V1[0],V1[1]+1)
        self.pixel3 = (V1[0],V1[1]+2)
        
        self.pixelState = initState

    def update(self):

        if self.state == "Init":
            self.startTime = utime.ticks_ms()
            self.state = "WaitTimeout"
            display.set_pixel(self.pixel1[0],self.pixel1[1],self.pixelState)

        elif self.state == "WaitTimeout":
            if utime.ticks_diff(utime.ticks_ms(),self.startTime) > self.interval:
                self.startTime = utime.ticks_ms()
                if self.pixelState == 9:
                    self.pixelState = 0
                else:
                    self.pixelState = 9
                display.set_pixel(self.pixel1[0],self.pixel1[1],self.pixelState)

pixel1 = Sem((0,0),0,1000)


while True:
    pixel1.update()
