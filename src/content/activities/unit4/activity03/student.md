Información enviada: El micro:bit envía los valores de aceleración en los ejes X y Y (xValue, yValue), y el estado de los botones A y B (aState, bState), todo en formato de cadena con valores separados por comas y terminados en un salto de línea.

Explicación de la línea:

python
Copiar
`"{},{},{},{}\n".format(xValue, yValue, aState, bState)`
genera un string con los valores de los sensores y botones en una cadena, separada por comas y terminada con un salto de línea, para facilitar la interpretación de los datos.

Comas y salto de línea: Las comas separan los datos para facilitar su análisis y el salto de línea organiza cada conjunto de datos en una nueva línea.

Problema sin comas y salto de línea: Los datos serían difíciles de interpretar, ya que no habría una clara separación entre los diferentes valores.

Función sleep(100): Hace que el micro:bit envíe datos cada 100 milisegundos (10 Hz). Sin ella, los datos se enviarían demasiado rápido, lo que podría saturar el receptor.

Valores de xValue y yValue: Los valores cambian según la inclinación del micro:bit, con xValue variando al inclinarse hacia los lados y yValue al inclinarse hacia adelante o atrás.

Valores de aState y bState: Son True si los botones A o B están presionados, y False si no lo están.

Diferencia entre is_pressed() y was_pressed():

is_pressed(): Detecta si el botón está presionado en el momento actual.

was_pressed(): Detecta si el botón fue presionado en el ciclo anterior.
