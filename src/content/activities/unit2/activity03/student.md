#### Características del micro:bit

##### **Entradas**
- **Botones A y B** – Detectan pulsaciones.
- **Logo táctil (V2)** – Actúa como botón capacitivo.
- **Acelerómetro** – Detecta movimientos e inclinaciones.
- **Micrófono (V2)** – Capta sonidos del entorno.

##### **Salidas**
- **Matriz de LEDs 5x5** – Muestra imágenes y texto.
- **Zumbador (V2)** – Reproduce sonidos.
- **Pines de salida** – Controlan dispositivos externos.
- **Conectividad inalámbrica** – Comunicación vía Bluetooth y radio.

---

#### **Funciones en MicroPython**

##### **Entradas**
- **Botones:**  
  ```python
  from microbit import *
  if button_a.is_pressed():
      display.show("A")
  ```
- Logo táctil:
  ``` python
  if pin_logo.is_touched():
    display.show(Image.HEART)
  ```
 - Acelerómetro:
  ``` python
  if accelerometer.current_gesture() == "shake":
      display.show(Image.SURPRISED)
  ```
### **Salidas**
 - Matriz de LEDs:
  ``` python
  display.show(Image.HAPPY)
  ``` 
 - Sonido:
  ``` python
  import music
  music.play(music.NYAN)
  ``` 
 - Pines de salida:
  ``` python
  pin0.write_digital(1)
  ``` 
