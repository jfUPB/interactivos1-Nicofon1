
15. Presiona los botones A y B del micro:bit.
+ En este paso segun al boton se muestra A con rojo o B con amarillo y es gracias a esto:
    ``` js
  if(port.availableBytes() > 0){
        let dataRx = port.read(1);
        if(dataRx == 'A'){
            fill('red');
        }
        else if(dataRx == 'B'){
            fill('yellow');
        }
  }


Y esto 

     
     if button_a.is_pressed():
          uart.write('A')
          sleep(500)
      if button_b.is_pressed():
          uart.write('B')
          sleep(500)

17. Sacude el micro:bit. ¿Qué pasa?
+ Pasa a C en verde y es gracias a esto:

      if accelerometer.was_gesture('shake'):
        uart.write('C')
        sleep(500)


18. Presiona el botón Send Love. ¿Qué pasa?
+ Aparese un corazon y carita  feliz y es gracias a esto:

      if uart.any():
        data = uart.read(1)
        if data:
            if data[0] == ord('h'):
                display.show(Image.HEART)
                sleep(500)
                display.show(Image.HAPPY)

          function sendBtnClick() {
              port.write('h');
          }
