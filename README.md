Este proyecto configura dos servidores DNS utilizando BIND. El servidor Tierra actúa como el servidor DNS maestro (primario) y el servidor Venus como servidor DNS esclavo (secundario). Ambos servidores gestionan las zonas directa e inversa del dominio ficticio sistema.test.

Archivos Modificados

En Tierra (Servidor Maestro)

1. /etc/bind/named.conf.options:

   - Configura las opciones generales del servidor BIND, incluyendo:
       - Reenvío de peticiones DNS a servidores externos (forwarders).
       - Recursión permitida para ciertas subredes.
       - Escucha en todas las interfaces y en IPv4/IPv6.

2. /etc/bind/named.conf.local:

    - Define las zonas DNS principales:
        - sistema.test: Zona directa (resolución de nombres a IP).
        - 57.168.192.in-addr.arpa: Zona inversa (resolución de IP a nombres).

3. /etc/bind/sistema.test.zone:

    - Archivo de zona directa que contiene los registros de nombres a direcciones IP, como A y MX.

4. /etc/bind/57.168.192.rev:

    - Archivo de zona inversa que contiene los registros PTR para la resolución inversa de IPs.


En Venus (Servidor Esclavo)

1. /etc/bind/named.conf.options:

    - Configura las opciones generales de BIND, similar al servidor maestro.
2. /etc/bind/named.conf.local:

   - Define las zonas DNS como esclavas, sincronizadas desde Tierra:
       - sistema.test: Zona directa esclava.
       - 57.168.192.in-addr.arpa: Zona inversa esclava.
         

Cómo Funciona
    1. El servidor Tierra es el servidor maestro que contiene los archivos de zona con la información DNS del dominio sistema.test.
    2. El servidor Venus actúa como esclavo y recibe copias sincronizadas de las zonas desde Tierra.
    3. Las consultas DNS enviadas a cualquiera de los dos servidores resuelven nombres e IPs para el dominio sistema.test. 
