Se dispone de 4 tipos de accesos, que se aplican tanto a los #atributos como a los #métodos .

### Privado
Los métodos y los atributos solo pueden leerse o invocarse desde la clase a la que pertenecen. Para leer los atributos desde el resto del programa, se usan getters y setters.
Estos deben incluir condiciones para evitar escrituras null.

### Acceso a paquete
Acceso a las clases que estén en el mismo paquete.

### Protected
Igual que acceso a paquete, pero además también dan acceso a las subclases en caso de que estas estén en un paquete diferente.

### Público:
Se pueden invocar o acceder a los métodos y atributos desde cualquier parte del programa.

![[img_TiposDeAcceso.png]]
