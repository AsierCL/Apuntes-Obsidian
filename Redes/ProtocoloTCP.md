El protocolo **TCP (Transfer Control Protocol)**, pertenece a la [[Capa de transporte]]. Este protocolo se basa en conexión. 
Este usa varios métodos para garantizar una transmision fiable:
- Números de secuencia: Cada byte enviado se identifica con un número de secuencia de 32bits, lo que permite saber el orden de los paquetes y detectar la falta de alguno.
- ACKs (Acknowledgment o acuses de recibo). Se envian para decirle al emisor que el paquete ha llegado.
- Timeouts: Si el emisor no recibe un ACK en un tiempo determinado, reenviará el paquete correspondiente.
### Three-Way Handshake
TCP establece conexión en 3 fases:
- SYN: El cliente envia un segmento especial. Este no contiene datos, pero pone a 1 el bit de SYN. El cliente crea un número de secuencia aleatorio.
- SYN ACK: El servidor responde con un paquete, tras asignar la memoria y los buffers correspondientes. En este paquete, también se crea un número de secuencia aleatorio propio del servidor.
- ACK: Por último, el cliente confirma la conexión con un ACK, ya con el bit de SYN=1. Junto con este paso, ya se puede empezar a transmitir datos desde el cliente.
![[img_Three-Way Handshake.png]]

### Cabecera TCP
- Puerto de origen:
- Puerto de destino
- Número de secuencia: Permite ordenar los segmentos, y detectar errores
- Número de reconocimiento: epresenta el siguiente número de byte que el receptor espera recibir del emisor
- Long de cabecera: Indica el tamaño de la cabecera, para permitir saber donde comienzan los datos del segmento
- 3 bits reservados
- Flags de control: 
	- URG: Datos urgentes, que deben ser procesados de inmediato
	- ACK: Confirma que todos los datos hasta este byte han sido recibidos
	- PSH: Petición para enviar los datos directamente a capa de aplicación
	- RST: Reset de conexion
	- SYN: Se usa para iniciar la conexión, como parte del Three-Way Handshake
	- FIN: Se usa para cerrar la conexion
	- ECE: Notificación explícita de conexión (usado por los routers)
	- CWR: Señala que el emisor ha reducido su ventana de congestión
- Ventana de recepción: Cantidad max de datos que el receptor acepta
- [[Checksum]]: Suma de todos los campos para verificar la integridad del paquete.
- Puntero de urgencia: Apunta al último byte de datos urgentes cuando la flag URG=1
- Opciones: Tiene varios campos que pueden variar.  El más importante es el MSS .
	- MSS o Maximum Segment Size, es el tamaño máximo de un segmento TCP.
	  Se establece en el [[ProtocoloTCP#Three-way handshake]], y puede variar.
- Datos: Aqui va toda la información enviada.
![[img_CabeceraTCP.png]]

### Control de congestión
El protocolo TCP ajusta la tasa de envio de paquetes de forma que no satura la red. Este ajuste, posee tres fases.
###### Conceptos previos
- Ventana de congestión(cwnd): Esta variable adicional del emisor, impone una restricción sobre la velocidad de transmisión.
- Umbral de arranque lento(sstrhesh): Esta segunda variable, se define para saber cuando terminar el proceso de arranque lento.

###### Modos
- Inicio lento: En esta primera fase se produce un crecimiento exponencial, en el que el cwnd se va duplicando con cada ACK nuevo. Este proceso continua hasta un timeout, en el que se vuelve a empezar el proceso de inicio lento, poniendo la vriable sstrhesh a la mitad del valor de cwnd. Cuando el valor del cwnd supere al sstrhesh, se pasa al modo de AIMD. Si se reciben 3ACKs duplicados, se pasa a Fast Recovery.
- AIMD(incremento aditivo, decremento multiplicativo): En este modo, el cwnd se aumenta de MSS en MSS, teniendo un crecimiento lineal. 
  Si se produce un timeout, sstrhesh=cwnd/2, y se vuelve al arranque lento. Si se reciben 3ACKs duplicados, se pasa a Fast Recovery
- Fast Recovery: En este modo, se envia el segmento restante, hasta recibir un ACK nuevo. Cuando esto ocurre, se vuelve a AIMD. Si hay un timeout, sstrhesh=cwnd/2 y vuelta a Inicio Lento.
![[img_Congestion TCP.png]]