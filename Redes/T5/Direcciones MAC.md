Cada dispositivo conectado a una red [[Ethernet]] tiene una **dirección MAC ÚNICA**, de 48bits o 6bytes, asignada por cada fabricante a la tarjeta de red grabada en una memoria ROM, bien sea inalámbrica o cableada.
![[img_MACFabricantes.png]]

## Tipos de direcciones MAC
- Unicast: Esta dirección es la "normal". Identifica al receptor
- Broadcast: Todos los bits a 1 (FF:FF:FF:FF:FF:FF), la trama se envia a todos los dispositvos de la red. Usadas en protocolos como el [[Protoolo ARP]]
- Multicast: Dirige el mensaje a un grupo de dispositivos. El bit menos significativo del primer byte vale 1 (xxxxxxx**1**:XX:XX:XX:XX:XX)
Un nodo acepta todas las tramas las cuales la dirección sea su propia dirección, la broadcast, la multicast o cualquier trama si se encuentra en **modo promiscuo**