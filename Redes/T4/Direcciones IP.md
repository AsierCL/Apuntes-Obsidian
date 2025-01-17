Las direcciones IP permiten identificar un host o dispositivo en una red.

## IPv4
Dirección de 32bits, dividia en 4 octetos por puntos (192.168.0.1)
Con esto, tenemos 2 elevado a 32 direcciones posibles, lo que no es suficiente para la demanda actual.

Existen 3 tipos de direcciones IPs:
##### Publicas
Son únicas a nivel global, y accesibles desde internet.
Para conocerlas, se usa el [[Protocolo DNS]].
##### Privadas
Son únicas en cada red local, y no son enrutables en internet.
Rangos reservados:
	- Clase A: `10.0.0.0` a `10.255.255.255`.
	- Clase B: `172.16.0.0` a `172.31.255.255`.
	- Clase C: `192.168.0.0` a `192.168.255.255`.
##### Otras
- Dirección de loopback, utilizada para pruebas o programas locales `127.0.0.0/8`
- Dirección de broadcast, última dirección de una red, y usada para enviar datos a todos os host de esa red: `192.168.0.255`  en una red `192.168.0.0/24`.
- Multidifusión, para enviar datos a múltiples usuarios interesados: `224.0.0.0` hasta `239.255.255.255`.
![[img_ClassDirIP.png]]