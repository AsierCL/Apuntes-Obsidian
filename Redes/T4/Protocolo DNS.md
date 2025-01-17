El **Domain Name System** es una parte fundamental de internet, que actua como una guía de la red. Los números no son fáciles de memorizar para los humanos, pero los nombres si. Por ello, el protocolo DNS se encarga de traducir `google.com` a `142.250.190.46`.
También gestiona información relacionada, como servidores de correo electrónico y servicios específicos asociado a un dominio.

## Componentes del DNS

### A. Espacio de nombres
El DNS organiza los nombres de dominio en una estructura jerárquica.
##### Dominio raíz
Es el nivel más alto, representado con un punto `.`
##### **TLD** (Top Level Domain o dominios de nivel superior)
Incluyen:
- Genéricos: `.com`, `.org`, `.net`.
- Geográficos (todos los de 2 letras): `.es`(España), `.uk`(Reino Unido)
- Patrocinados: `.gov`, `.edu`
##### Dominios de segundo nivel
Ejemplos: `google.com`, `wikipedia.org`
##### Subdominios
Ejemplos: `mail.google.com`, `es.wikipedia.org`

### B. Servidores DNS
##### Servidor raiz
Es el punto de contacto en el sistema DNS. 
Conoce los servidores responsables de cada TLD
##### Servidor de TLD
Responde por los dominios específicos bajo su TLD
### Servidor autoritativo
Contiene la información definitiva para un dominio específico.
Por ejemplo, el servidor de nombres de google.com, proporciona las IPs de sus subdominios
##### Servidor resolutor
Interactua con los servidores DNS para obtener la información.
Para ello, realiza peticiones recursivas.

## Ejemplo de consulta
1. El cliente solicita una dirección al equipo (equipo.red.com)
2. El equipo consulta, en caso de que exista, a su servidor DNS de la red local (dns.red.com)
3. El servidor local, si no tiene la dirección, consulta al servidor DNS raíz.
4. Este, va al servidor TLD correspondiente.
5. El TLD, consulta al servidor DNS autorizado correspondiente.
6. La respuesta pasa del servidor autorizado al TLD, y del TLD al raíz, y asi recursivamente.

	IMPORTANTE: Si en alguno de los pasos, la consulta está cacheada (ejemplo: el TLD correspondiente tiene la IP), no se consultarán los siguientes servidores, (ejemplo: el servidor autorizado).