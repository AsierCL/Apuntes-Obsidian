Un **programa** es un fichero que contiene las instrucciones y estructuras necesarias para la ejecución.

Un **proceso** es una abstracción de un programa en ejecución. Cada proceso tiene sus propias direcciones virtuales, en las que tiene su código, datos, stack. registros... a los que solo el tiene acceso. A pesar de que están aislados entre ellos, pueden establecer interacciones entre ellos escribiendo en un archivo en común, o mediante [[Señales]].

Cuando solo hay una CPU, solo puede haber un proceso ejecutándose a la vez. Puede parecerer que existe concurrencia, pero realmente en cada momento se ejectua solo un proceso, y se va alternando de forma muy veloz, imperceptible para el usuario, en diferentes procesos. Esto se conoce como **pseudoparalelismo**, y se realiza mediante un **cambio de contexto**. Esto crea la falsa sensación de paralelismo.

Cuando hay un cambio de contexto, el SO almacena el contenido de todos los registros en memoria del proceso que había en la CPU para cambiar el proceso que está ejecutando, por lo que cuando hay que reanudar la ejecución del primer proceso, se restaura exactamente en el mismo punto y la misma situación que antes del cambio de contexto.

En la zona de kernel de la memoria, hay una **tabla de procesos**, que almacena la información de todos los procesos del sistema. Puede que en la tabla no esté almacenado directamente la información, pero si un puntero a donde está situado ese dato.
![[img_TablaDeProcesos.png]]

