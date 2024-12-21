Carrier Sense Multiple Access with Collision Detection, es un mecanismo que evita colisiones en medios compartidos.

### Funcionamiento
El nodo emisor escucha el cable mientras transmite. Cuando un nodo ocupa el medio, su transmisión tarda un tiempo en alcanzar otros nodos, por lo que se vuelve vulnerable.
Cuando un nodo detecta una colisión, acaba de transmitir la cabecera, emite una secuencia de 32bits (jamming sequence), detiene la transmisión, y usa el algoritmo de espera exponencial binaria.
![[img_EsperaExponencialBinaria.png]]