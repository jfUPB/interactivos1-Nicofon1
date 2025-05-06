**Vectores de Prueba Iniciales**

Aquí hay una serie de vectores de prueba para el código de la "Bomba". He incluido pruebas para los casos modelados y no modelados para tratar de encontrar posibles problemas.

* **Estado Inicial: STATE\_CONFIG**

    * Evento: 'a'
        * Acciones: BOOM\_TIME se incrementa en 1000 (si es menor a 60000).
        * Estado Siguiente: STATE\_CONFIG
    * Evento: 'b'
        * Acciones: BOOM\_TIME se decrementa en 1000 (si es mayor a 10000).
        * Estado Siguiente: STATE\_CONFIG
    * Evento: 's'
        * Acciones: current\_state se cambia a STATE\_ARMED, start\_time se inicializa, arr se vacía.
        * Estado Siguiente: STATE\_ARMED
    * Evento: 't'
        * Acciones: Ninguna.
        * Estado Siguiente: STATE\_CONFIG
    * Evento: Cualquier otra tecla
        * Acciones: Ninguna
        * Estado Siguiente: STATE\_CONFIG
* **Estado Actual: STATE\_ARMED**

    * Evento: 'a'
        * Acciones: 'a' se agrega a la cadena arr.
        * Estado Siguiente: STATE\_ARMED
    * Evento: 'b'
        * Acciones: 'b' se agrega a la cadena arr.
        * Estado Siguiente: STATE\_ARMED
    * Evento: 's'
        * Acciones: 's' se agrega a la cadena arr.
        * Estado Siguiente: STATE\_ARMED
    * Evento: 't'
        * Acciones: 't' se agrega a la cadena arr.
        * Estado Siguiente: STATE\_ARMED
    * Evento: (Tiempo > BOOM\_TIME)
        * Acciones: current\_state se cambia a STATE\_BOOM, start\_time se inicializa.
        * Estado Siguiente: STATE\_BOOM
    * Evento: arr == "abas"
        * Acciones: current\_state se cambia a STATE\_CONFIG.
        * Estado Siguiente: STATE\_CONFIG
     * Evento: Cualquier otra tecla
        * Acciones: la tecla se agrega a la cadena arr
        * Estado Siguiente: STATE_ARMED
* **Estado Actual: STATE\_BOOM**

    * Evento: 't'
        * Acciones: current\_state se cambia a STATE\_CONFIG.
        * Estado Siguiente: STATE\_CONFIG
    * Evento: (Tiempo > 3300ms desde el inicio de STATE\_BOOM)
        * Acciones: Se muestra " ☠︎︎ ".
        * Estado Siguiente: STATE\_BOOM
    * Evento: Cualquier otra tecla
        * Acciones: Ninguna.
        * Estado Siguiente: STATE\_BOOM
