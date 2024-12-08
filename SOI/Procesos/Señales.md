Las señales sn avisos que reciben los [[Procesos/Procesos]] acerca de eventos que pueden ocurrir en el sistema, y se usan como mecanismo de comunicación o sincronización entre ellos.

Las señales están asociadas a números enteros, de forma que cuando se recibe una señal, se identifica. Son similares a las [[Traps]], pero con la diferencia de que las traps son avisos que se realizan al SO, mientras que las señales van dirigidas a un proceso concreto.

Las señales pueden generarse por otros procesos, por sucesos del hardware, interrupciones de terminal (CTRL + C), notificaciones de E/S...