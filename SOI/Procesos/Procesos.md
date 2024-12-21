Un **programa** es un fichero que contiene las instrucciones y estructuras necesarias para la ejecución.

Un **proceso** es una abstracción de un programa en ejecución. Cada proceso tiene sus propias direcciones virtuales, en las que tiene su código, datos, stack. registros... a los que solo el tiene acceso. A pesar de que están aislados entre ellos, pueden establecer interacciones entre ellos escribiendo en un archivo en común, o mediante [[Señales]].

Cuando solo hay una CPU, solo puede haber un proceso ejecutándose a la vez. Puede parecerer que existe concurrencia, pero realmente en cada momento se ejectua solo un proceso, y se va alternando de forma muy veloz, imperceptible para el usuario, en diferentes procesos. Esto se conoce como **pseudoparalelismo**, y se realiza mediante un **cambio de contexto**. Esto crea la falsa sensación de paralelismo.

Cada proceso pertenece a un usuario identificado (UID),  a un grupo (GID). El usuario root puedee saltarse cualquier regla de protección de los procesos. 
Todos los proccesos se identifican con el PID (Process ID).

Los procesos tienen un espacio de [[Memoria virtual]] asignada a este. En este espacio se guardan los datos y la pila de ejecución. Las direcciones van desde 0 hasta un valor máximo.

Cuando hay un cambio de contexto, el SO almacena el contenido de todos los registros en memoria del proceso que había en la CPU para cambiar el proceso que está ejecutando, por lo que cuando hay que reanudar la ejecución del primer proceso, se restaura exactamente en el mismo punto y la misma situación que antes del cambio de contexto.

En la zona de kernel de la memoria, hay una **tabla de procesos**, que almacena la información de todos los procesos del sistema. Puede que en la tabla no esté almacenado directamente la información, pero si un puntero a donde está situado ese dato.
![[img_TablaDeProcesos.png]]

## Creación, clasificaciónn y terminación
Los procesos se pueden crear de 3 formas:
- Durante el [[Arranque del ordenador]]
- Desde otro proceso que usa llamadas al sistema
- Por solicitud del usuario (mediante comandos)

Otra clasificación alternativa podría ser por tipo:
- Modo kernel (muchas llamadas al sistema y lentos)
- Modo usuario
- Modo daemon (ejecución en segundo plano y sin supervisión ninguna del usuario)

Los procesos pueden terminar de 4 formas diferentes:
- Salida normal (voluntaria). El proceso termina con un exit(0)
	- El padre puede examinar el status al salir, pero el exit no tiene salida
	- Tras el exit, el proceso se borra del arbol de procesos
	- La función main no necesita un exit (se pone automáticamente)
- Salida por error (voluntaria). El proceso termina con un exit(!=0)
- Error fatal (involuntaria): Segfaults, división/0...
- Eliminado por otro proceso (involuntaria). Recibe una señal KILL