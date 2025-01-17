El protocolo ARP se encarga de traducir las [[Direcciones MAC]] a [[Direcciones IP]]. Para ello, mantiene una tabla (caché ARP) con las correspondencias entre IP-MAC.

Cuando ARP recibe una IP que no tiene en su tabla, emite una trama broadcast indicando esa IP. Dado que es una trama broadcast, todos los equipos de la red la reciben, pero solo el que tenga la IP correcta responderá. Por tanto, ya se conoce la dirección MAC de ese equipo, y se puede proceder a la comunicación. 

Para no saturar la tabla ARP, las entradas se eliminan tras un cierto periodo de tiempo (15mins por ejemplo).