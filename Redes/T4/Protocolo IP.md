El protocolo IP actua como un servicio de entrega de paquetes en la red.

### Características
- No garantiza la entrega de los paquetes, ni su orde o protección. Eso se maneja en capas superiores como el [[Protocolo TCP]].
- Los datos de las capas superiores se encapsulan en datagramas IP.
- Funciona sobre los diferentes medios [[Ethernet]] o [[Wifi]] independientemente de las características del medio.
- Usa el [[Protocolo ICMP]] para enviar mensajes de control y error.

### Direccionamiento
Para saber a que host enviar cada datagrama, se usan [[Direcciones IP]], que actualmente cuenta con 2 versiones en uso (IPv4 e IPv6).
Para mejorar el número de IPs disponibles, se crean redes locales, con IPs locales, que se asignan a los dispositivos de manera estática, o de manera dinámica mediante el [[Protocolo DHCP]]. Para que estos dispositivos puedan salir a internet teniendo una IP local, se usa [[NAT]].
### Estructura de un datagrama (IPv4)
Longitud mínima: 20bytes:
- Versión: 4bits
- Longitud de cabecera: Tamaño en múltiplos de 4bytes
- Direcciones IP de origen y destino
- TTL: Time to Live, son los números de saltos permitidos antes de descartar un paquete
- Protocolo de la capa superior: Como TCP, UDP...
- Checksum: Verifica errores en la cabecera
- Datos: Contiene la informacion del nivel de transporte

