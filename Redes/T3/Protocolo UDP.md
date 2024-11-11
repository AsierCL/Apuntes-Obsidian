El protocolo **UDP (User Datagram Protocol)** es uno de los principales protocolos de transporte en la arquitectura de redes TCP/IP, junto con [TCP](Protocolo%20TCP.md). 

### Características generales
UDP no necesita conexión para enviar datos, ni ningún tipo de acuerdo previo entre emisor y receptor, por lo que hay muy poco retardo.
Por este mismo motivo, no existe garantía de entrega de paquetes, por lo que los paqutes perdidos no serán retransmitidos automáticamente.
Además, UDP no tiene estado, y cada paquete es completamente independiente.

#### Cabecera UDP
Posee los campos de puerto origen y destino, la long total y el [[Checksum]].
![[img_CabeceraUDP.png]]