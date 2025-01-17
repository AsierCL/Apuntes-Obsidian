Funcionan como las estructuras de la mayoria de lenguajes de programación, agrupando varios [[Tipos de datos]] en sus atributos, bien sean primitivos u otras clases.

Las Clases contienen 2 tipos de codigo:
### Variables o #atributos
Son las características que definen la entidad representada por la clase.
Por ejemplo, el nombre de un continente. 
Para mantener la integridad de los datos, deberian ser privados siempre, y solo se deberia acceder a ellos desde otras clases mediante sus métodos.

### Funciones o #métodos
Estas funciones acceden a los atributos, para permitir la lectura y escritura y dar funcionalidad al programa.


## Constructores
Estos son un tipo de #métodos que crea una instancia de una clase.
En esta función se da valor a todos los atributos de la clase. En caso de ser un tipo primitivo, se le da el valor por default. En caso de ser otra clase, debe asignarsele un espacio en memoria usando el operador **new**. 
Clase clase = new Clase()

Java tiene un constructor por defecto para todas las clases, sin argumentos, que se usa cuando no se especifica ningún otro. Por tanto, inicializa todo por defecto, es decir, las clase son NULL.