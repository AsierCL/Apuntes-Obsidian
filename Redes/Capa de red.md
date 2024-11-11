La capa de red se encarga de llevar los paquetes que recibe de la capa de transporte de un host a otro.
Está implementada tanto en sistemas finales como en los routers.

## Funciones principales
##### Encaminamiento (Routing)
El **encaminamiento** determina la ruta óptima que debe seguir un paquete para llegar desde el origen hasta su destino. Para ello, se usan **[[algoritmos de encaminamiento]]**.
##### Reenvio (Forwarding)
Es el proceso de mover y **reenviar** los paquetes de datos desde un enlace de entrada a un enlace de salida de un router, basándose en la dirección de la [[tabla de enrutamiento]].
##### Direccionamiento lógico
La capa de red utiliza direcciones [[Protocolo IP|IP]] para identificar de forma única cada dispositivo en la red, y facilitar la comunicación entre redes.
##### Fragmentación
Los paquetes que son demasiado grandes para un enlace, se fragmentan en partes pequeñas en el emisor, y en la capa de transporte del receptor se **reensamblan**.