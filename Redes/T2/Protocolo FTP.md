#protocolo
El **File Transfer Protocol** es un estandar usado para la transferencia de archivos entre cliente y servidor a través de una [[Arquitectura TCP-IP|red TCP-IP]], creado en los años 70.
Es un protocolocon estado, es decir, mantiene información durante toda la conexión.
### Arquitectura
Usa dos conexiones [[Protocolo TCP|TCP]] simultáneas entre el cliente y el servidor.
##### Conexión de control
Se establece en el puerto 21 del servidor, y se usa para enviar comandos y recibir respuestas. Esta es persistente, permanece abierta toda la sesión.
##### Conexión de datos
Esta no es persistente, y solo se abre para realizar una transferenca de datos. El servidor inicia una conexión por el puerto 20 a un puerto del cliente. Si esto sucede en modo activo, el cliente especificará el puerto. Si sucede en modo pasivo, el servidor escoge el puerto, y es el cliente el responsable de conectarse.

### Comandos
Para iniciar la conexión, podemos usar 'ftp 192.168.0.2'.
Una vez introducidos el usuario y la contraseña, tenemos varios comandos que podemos usar. Los más importantes son los siguientes:
- LIST: Equivalente a un ls o a un dir
- RETR: Equivalente a un get
- STOR: Equivalente a un put
- QUIT: Equivalente a un exit

### Respuesta
La respuesta del servidor es un número de 3 cifras y una frase explicativa: 
- 200: Comando exitoso
- 331: Usuario necesita contraseña para continuar
- 530: Error de login

### Versiones
Existen versiones mejoradas de este servicio, como SFTP.