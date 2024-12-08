El sistema operativo es el software más basico que corre en un ordenador. Este se encarga de gestionar el hardware y proporciona una plataforma para que las aplicaciones funcionen. Es decir, hace de **puente entre el hardware y el software**. Además, provee al programador de un **conjunto abstracto de recursos**, como la memoria o las interacciones de I/O.

## Conceptos básicos
#### [[Procesos/Procesos]]
Un proceso es un programa en ejecución, que incluye datos, código del programa, y una pila de memoria. Los SO permiten ejecutar varios procesos simultáneamente, y gestionan el estado, suspensión y reanudación de estos. Dentro de un proceso, pueden existir varios [[Hilos]], que se ejecutan concurrentemente.
#### [[Memoria virtual]]
Permite que los programas tengan un espacio de direcciones independiente de la memoria fisica, e independiente undos de otros, ayudando a mejorar la seguridad.
#### [[Sistemas de archivos]]
Organiza y almacena los datos en las memorias secundarias, permitiendo crear rutas y gestionar permisos de lectura, escritura y ejecución de los archivos.
#### [[Entrada y salida]]
El SO facilita la comunicación con los dispositivos externos como impresoras, discos o redes. A través de controladores, gestiona las transferencias de datops, garantizando un uso eficiente y seguro de los dispositivos.

## Syscalls
Las llamadas al sistema, permiten a las aplicaciones utilizar los servicios del SO. Estas llamadas varían de un SO a otro, y en sistemas UNIX, se usa el estandar POSIX.
```C
int nbytes = read(file_descriptor, buffer, count);
```
En este ejemplo, vemos como la función read hace una llamada al sistema que lee datos en buffer desde un archivo expecificado con file_descriptor.