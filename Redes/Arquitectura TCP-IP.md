La arquitectura TPC/IP es una simplifacioón del modelo OSI. Esta, posee 5 capas:
![[img_ArqTCP-IP.png]]
#### Capa de aplicación
La [[Capa de aplicación]] son los procesos que se comunican entre si mediante mensajes. Algunos de estos protocolos son HTTP, SSH, DNS...

#### Capa de transporte
La [[Capa de transporte]] se encarga de recoger los mensajes de la capa de aplicación y enviarlos a la red. Tiene dos protocolos principales, TCP y UDP.

#### Capa de red
La [[Capa de red]] es la encargada de mover los paquetes de un host a otro. Cuenta con protocolos de enrutamiento para determinar el camino que seguirán los paquetes. Su elemento principal es el router.

#### Capa de enlace
La [[Capa de enlace]] se encarga de los detalles de bajo nivel entre los extremos de un enlace. Sus protocolos depende del medio y la tecnología de la red.

#### Capa física
La [[Capa física]] es la capa más baja del modelo. Esta capa trabaja a nivel de bit, y es la encargada de transformar dichos bits en impulsos eléctricos. 