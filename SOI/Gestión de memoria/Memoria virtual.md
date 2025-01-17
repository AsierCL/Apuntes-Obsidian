Los sistemas con multiprogramación necesitan espacios de memoria cada vez más grandes.

En la memoria virtual, cada proceso tiene su propio espacio de direcciones dividido en #Páginas_de_memoria. El espacio, por tanto, esta formado por direcciones virtuales que no tienen porque coincidir con las físicas, y pueden ser mucho mayores. La traducción de unas a otras se realiza en la **MMU**, que forma parte de la CPU.
![[img_MMU.png]]

## Paginación
El espacio de direcciones virtuales depende de la longitud de la palabra del sistema(n). El espacio tiene 2^n direcciones, dividido en 2^p páginas.
Por tanto, una dirección virtual, consta de dos campos:
| Campo de página (p) | Campo de offset(n-p) | 

El número de marcos de página que hay en la memoria principal es:
tamano_memFisica / tamano_pag

Cualquier página puede estar en cualquier marco de página, pero como el espacio de direcciones virtual puede ser mucho mas grande que el físico, no todas estarán en memoria simultáneamente. Cuando se intenta acceder a una página que no está en memoria, se produce un #Fallo_de_página. Esto provoca que la MMU envie una [[Excepciones|excepción]] y el proceso se bloquee mientras se busca y copia la página entera del disco a la memoria principal.

### Tabla de páginas
El índice de la TP es el número de la página virtual.
La estructura suele estar formada por:
- Número de marco de página: Si la página está en memoria, este es el número del marco, si no, será un 0
- Bit presenta/ausente
- Bits de protección: (rwx)-> por tanto, no se deben mezclar datos e instrucciones en la misma página
- Bit referenciada: Se usa para los algortimos de reemplaazo
- Bit de deshabilitación de uso de caché: Se usa en páginas compartidas o donde se ejecutan operaciones de lectura y escritura de E/S para mantener la #Coherencia_de_caché.

![[img_EntradaDeTP.png]]
![[img_TraduccionDirVirt-Fisica.png]]

### Aceleración de la paginación
La traducción de direcciones de físicas a virtuales y viceversa debe ser rápida. Para ello, existen varias técnicas para mejorar la efectividad:
- Usar TP multinivel o invertidas para espacios de direcciones muy grandes
- Usar TLB

#### #TLB (Buffer de traducción adelantada)
Es un dispositivo hardware que se inserta en la MMU y que asocia direcciones virtuales a direcciones físicas sin usar la TP de la memoria principal.
En la TLB se guarda un pequeño número de entradas, cuyos campos son:
- Núm de página virtual
- Bit de modificada
- Bits de protección
- Marco asociado
- Bit de validez
![[img_TLBTabla.png]]

###### Pasos para traducción
1. La MMU revisa si la dirección virtual está en la TLB
	1. Si se encuentra y el bit de validez es 1, se toma el marco de página correspondiente, sin pasar por la TP
2. SI no, se produce un fallo de TLB, por lo que hay que buscar la dirección en la TP.
3. Se busca en la TP el número del marco correspondiente a la dirección virtual. Si no se encuentra, se produce un #Fallo_de_página.
4. Si se encuentra, se copia a la TLB. Si esta está llena, se debe reemplazar por una de las entradas. Si el bit modificado=1, se pone a 1 también en la TP.

### Tablas de páginas multinivel
Si un espacio de direcciones es muy grande, sus TP también lo son.

Las TP multinivel, consisten en dividir la TP en varios bloques del tamaño de una página, de fomra de que cada uno pueda cargarse en un marco de la memoria principal, pero no todos ellos tengan que estar a la vez. **Esta división es análoga a la paginación del espacio de direcciones**.

Estudiaremos las traducciones en 2 niveles, aunque en sistemas con palabras muy grandes(64bits) puede llegar a usar 3 niveles.

#### Tablas de 2 niveles
Ahora, existe una tabla de primer nivel(TP1) única para cada proceso, que asocia las las tablas de segundo nivel(TP2) al marco que ocupan. Las TP2, contendrán las entradas de la TP correspondientes a un bloque.
Ahora, las direcciones virtuales son de la siguiente forma:
| Campo TP1 | Campo TP2 | Offset |

Para calcular el número de bits de cada campo, se necesita información del sistema. Con el tamaño de página y el tamaño de los espacios de direcciones, podemos averiguar el número de páginas y el de marcos que hay, dividiendo las direcciones posibles entre el tamaño de cada página. 

Para realizar las traducciones:
1. Se lee el campo de TP1 de la dirección.
	1. Si la entrada correspondiente no está memoria, se produce un #Fallo_de_página y se trae de memoria como una página normal
2. Si está, se lee el campo de la dirección TP2.
	1. Si no está, #Fallo_de_página y se carga
3. SI está, se procede con normalidad.

### Tablas de páginas invertidas
En sistemas de 64bits las TP son tan grandes que ni siquiera las TP multinivel se hacen manejables en memoria.

La solución es una tabla de páginas invertida, que se mantendrá siempre en memoria, y tendrá una entrada por marco de la memoria principal. Cada una de estas entradas especificará el número de página y proceso al que pertenece la página que se encuentra en el marco.

El número de entradas se calcula: 
Mem principal = 2^n
Tam página = 2^p
El número de entradas necesarias es = 2^(n-p)

De esta forma, se ahorran grandes cantidades, pero la traducción será muy lenta, ya que se debe recorrer la tabla entera de cada vez. Esto puede optimizarse con la #TLB y organizando la tabla como una Tabla Hash con encadenamiento, cuya clave sea la dirección virtual.

### Segmentación

![[img_Segmentos.png]]