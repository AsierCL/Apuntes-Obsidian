Ethernet es una implementación de la [[Capa MAC]], es el estandar más común para las redes LAN cableadas, y utiliza [[CSMA-CD]].
La topología de red más común actualmente es **en estrella**, aunque antiguamente se usaba la topología en bus, con cable coaxial.
Las velocidades de Ethernet pueden variar, desde 10Mbps hasta 10Gbps.
Cada dispositivo de una red ethernet, tiene una [[Direcciones MAC|direccion MAC]] única que lo identifica dentro de esa red, mientras que fuera de dicha red, se utiliza una [[Direcciones IP|direccion IP]]. Para relacionar estas dos direcciones, se usa el [[Protoolo ARP]].
Existen dispositivos llamados Switches Ethernet que usan las direcciones MAC para reenviar las tramas únicamente al puerto necesario, reduciendo asi el tráfico en la red.

### Trama Ethernet
- **Preambulo (7 bytes):** Sincronización para los receptores.
- **SFD (Start Frame Delimiter, 1 byte):** Indica el inicio de la trama.
- **Dirección destino (6 bytes):** Dirección MAC del receptor.
- **Dirección origen (6 bytes):** Dirección MAC del emisor.
- **Tipo/longitud (2 bytes):** Indica el protocolo de nivel superior o la longitud de datos.
- **Datos (46-1500 bytes):** Información encapsulada (ej., un datagrama IP).
- **Relleno (opcional):** Asegura que la trama alcance el tamaño mínimo (64 bytes).
- **FCS (Frame Check Sequence, 4 bytes):** Verifica errores en la transmisión usando un código CRC.
![[img_TramaMACEthernet.png]]