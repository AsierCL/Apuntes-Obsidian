#protocolo 
Son las siglas de **HyperText Transfer Protocol**. Es el principal protocolo en la comunicación web, usado para intercambiar información entre cliente y servidor. Este protocolo usa [[Protocolo TCP|TCP]] y trabaja en la capa 7 del modelo OSI, o en la [[Capa de aplicación]] de la [[Arquitectura TCP-IP]]. 

El elemento principal es la página web o documento, que consta de **objetos**, direccionables por URL. Para trabajar con este protocolo, usamos **navegadores**. 

##### Conexiones no persistentes
Se usa una [[Protocolo TCP|conexion TCP]] diferente para cada petición. (HTTP/1.0)
- Serie: No puede haber varias conexiones simultáneas
- Paralelo: Puede haber varias conexiones simultáneas
![[img_HTTP No persistente.png]]
##### Conexiones persistentes
Se pueden transmitir varios objetos con la misma [[Protocolo TCP|conexion TCP]].
- Sin entubamiento: El cliente pide un objeto cuando recibe el anterior
- Con entubamiento: El cliente pide varios objetos simultáneamente
![[img_HTTP Persistente.png]]

## Tiempos de transferencia
Se usan 2 parámetros para medir el tiempo total: RTT y tiempo de transmisión.
RTT(Round-Trip Time) es el tiempo de ida y vuelta de un paquete. El tiempo de transmisión depende del tamaño del archivo.

## Mensajes
Los mensajes HTTP contienen una cabecera el la que viaja información básica, y un cuerpo en el que viajan los datos.
![[img_Cabecera HTTP.png]]
### Peticiones
Son los mensajes emitidos por el cliente. Estas peticiónes se pueden hacer con varios métodos. Dos de los más conocidos son GET y POST. El primero se usa para recuperar un recurso, y no modifica informacion del servidor, mientras que el segundo si envia datos, y se puede modificar el servidor con el.
#### Linea de petición
En esta linea está el objeto solicitado, la versión HTTP, y el método
#### Linea de cabecera
Contiene información adicional como el Host, el User-agent, el lenguaje preferido o el content-type y el content-lenght.
#### Cuerpo
Aqui viajan los datos de la petición. En el caso de GET, no viajará nada, mientras que en POST, por ejemplo, pueden ir los datos de un formulario que enviamos.

### Respuestas
Son los mensajes emitidos por el servidor. En estes se envia el objeto solicitado por el cliente, en caso de ser exitoso, o se informa de cualquier otro suceso.
#### Linea de estado
Incliye la version HTTP y el código de estado:
	Codigos de estado:
	- 1xx: Informativo
	- 2xx: Exitoso (200 OK, 201 Created)
	- 3xx: Redirección
	- 4xx: Error del cliente (403 Forbidden, 404 Not found)
	- 5xx: Error del servidor (500 Internal server error)

#### Linea de cabecera
Contiene información original, como la version del servidor, la fecha de envio, el last-modified o el content-type y el content-lenght.


## Mejoras
Implementación de un protocolo seguro [[Protoolo HTTPS|HTTPS]].
También existen nuevas versiones de HTTP, como la diseñada por Google, un 64% más rápida que la original.