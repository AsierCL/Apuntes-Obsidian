La capa de transporte prepara los mensajes de las aplicaciones para ser transmitidos por el emisor. En el receptor, se recuperan y se entregan a las aplicaciones. Solo implementada en los sistemas finales.
![[img_Capa de transporte.png]]
Existen dos protocolos principales de transporte, [[Protocolo TCP|TCP]] y [[Protocolo UDP|UDP]]. La diferencia de ambos radica en la conexión y fiabilidad de TCP, frente a la velocidad y sinmplifidad de UDP.

Trabajando en el caso de TCP, en la capa de transporte se fragmentan los mensajes en segmentos y se leañade la cabecera de la capa de transporte.
En el caso de UDP, simplemente se le añande la cabecera.