* **Estado Inicial: STATE\_CONFIG**

    * Evento (Teclado): 'a'
        * Acciones: BOOM\_TIME se incrementa en 1000 (si es menor a 60000).
        * Estado Siguiente: STATE\_CONFIG
    * Evento (Teclado): 'b'
        * Acciones: BOOM\_TIME se decrementa en 1000 (si es mayor a 10000).
        * Estado Siguiente: STATE\_CONFIG
    * Evento (Teclado): 's'
        * Acciones: current\_state se cambia a STATE\_ARMED, start\_time se inicializa, arr se vacía.
        * Estado Siguiente: STATE\_ARMED
    * Evento (Teclado): 't'
        * Acciones: Ninguna.
        * Estado Siguiente: STATE\_CONFIG
    * Evento (Teclado): Cualquier otra tecla
        * Acciones: Ninguna
        * Estado Siguiente: STATE\_CONFIG
    * Evento (Serial): Recibir 'A'
        * Acciones: BOOM\_TIME se incrementa en 1000 (si es menor a 60000).
        * Estado Siguiente: STATE\_CONFIG
    * Evento (Serial): Recibir 'B'
        * Acciones: BOOM\_TIME se decrementa en 1000 (si es mayor a 10000).
        * Estado Siguiente: STATE\_CONFIG
    * Evento (Serial): Recibir 'S'
        * Acciones: current\_state se cambia a STATE\_ARMED, start\_time se inicializa, arr se vacía.
        * Estado Siguiente: STATE\_ARMED
    * Evento (Serial): Recibir 'T'
        * Acciones: Ninguna.
        * Estado Siguiente: STATE\_CONFIG
    * Evento (Serial): Recibir cualquier otro carácter
        * Acciones: Ninguna
        * Estado Siguiente: STATE\_CONFIG

* **Estado Actual: STATE\_ARMED**

    * Evento (Teclado): 'a'
        * Acciones: 'a' se agrega a la cadena arr.
        * Estado Siguiente: STATE\_ARMED
    * Evento (Teclado): 'b'
        * Acciones: 'b' se agrega a la cadena arr.
        * Estado Siguiente: STATE\_ARMED
    * Evento (Teclado): 's'
        * Acciones: 's' se agrega a la cadena arr.
        * Estado Siguiente: STATE\_ARMED
    * Evento (Teclado): 't'
        * Acciones: 't' se agrega a la cadena arr.
        * Estado Siguiente: STATE\_ARMED
    * Evento (Teclado): Cualquier otra tecla
        * Acciones: la tecla se agrega a la cadena arr
        * Estado Siguiente: STATE\_ARMED
    * Evento (Serial): Recibir 'A'
        * Acciones: 'a' se agrega a la cadena arr.
        * Estado Siguiente: STATE\_ARMED
    * Evento (Serial): Recibir 'B'
        * Acciones: 'b' se agrega a la cadena arr.
        * Estado Siguiente: STATE\_ARMED
    * Evento (Serial): Recibir 'S'
        * Acciones: 's' se agrega a la cadena arr.
        * Estado Siguiente: STATE\_ARMED
    * Evento (Serial): Recibir 'T'
        * Acciones: 't' se agrega a la cadena arr.
        * Estado Siguiente: STATE\_ARMED
    * Evento (Serial): Recibir cualquier otro carácter
        * Acciones: el carácter se agrega a la cadena arr
        * Estado Siguiente: STATE\_ARMED
    * Evento: arr == "abas" (independientemente de la fuente del evento)
        * Acciones: current\_state se cambia a STATE\_CONFIG.
        * Estado Siguiente: STATE\_CONFIG
    * Evento: (Tiempo > BOOM\_TIME)
        * Acciones: current\_state se cambia a STATE\_BOOM, start\_time se inicializa.
        * Estado Siguiente: STATE\_BOOM

* **Estado Actual: STATE\_BOOM**

    * Evento (Teclado): 't'
        * Acciones: current\_state se cambia a STATE\_CONFIG.
        * Estado Siguiente: STATE\_CONFIG
    * Evento (Teclado): Cualquier otra tecla
        * Acciones: Ninguna.
        * Estado Siguiente: STATE\_BOOM
    * Evento (Serial): Recibir 'T'
        * Acciones: current\_state se cambia a STATE\_CONFIG.
        * Estado Siguiente: STATE\_CONFIG
    * Evento (Serial): Recibir cualquier otro carácter
        * Acciones: Ninguna.
        * Estado Siguiente: STATE\_BOOM
    * Evento: (Tiempo > 3300ms desde el inicio de STATE\_BOOM)
        * Acciones: Se muestra " ☠︎︎ ".
        * Estado Siguiente: STATE\_BOOM

