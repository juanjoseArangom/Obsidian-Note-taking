Es el acrónimo de *Domain Name System*. Permite traducir direcciones de dominio a IP. Sirve para recordar más fácilmente las páginas visitadas.
**Nos interesa** porque permite obtener información pública sobre una organización. Descubrir relaciones entre dominios y hosts. Técnicas de explotación específicas (DNS Spoofing).
# ¿Cómo funciona?
### DNS Zone
Agrupación de registros y datos DNS. Contienen diferentes tipos de registro relacionados con un mismo dominio particular, con un mantenimiento delegado a una organización concreta.
##### Tipos de registro:
![[Pasted image 20250207175339.png]]

# Fichero de Zona en DNS

Un **fichero de zona** es un archivo de texto utilizado en el sistema de nombres de dominio (**DNS**) para definir la relación entre nombres de dominio y sus direcciones IP u otros recursos. Es esencial para el funcionamiento del DNS, ya que almacena la información necesaria para la resolución de nombres dentro de una zona específica.

## Importancia del Fichero de Zona

1. **Traducción de nombres de dominio a direcciones IP**  
   Permite que los usuarios accedan a servicios en Internet utilizando nombres en lugar de direcciones IP numéricas.

2. **Estructuración jerárquica del DNS**  
   Define una "zona" dentro del DNS, especificando los registros para un dominio y sus subdominios.

3. **Delegación de autoridad**  
   Facilita la delegación de autoridad sobre partes del espacio de nombres de dominio, permitiendo una administración descentralizada.

4. **Registros esenciales**  
   Contiene registros como:
   - **SOA (Start of Authority)**: Define la autoridad principal de la zona.
   - **NS (Name Server)**: Especifica los servidores de nombres responsables de la zona.
   - **A/AAAA**: Asocian nombres de dominio con direcciones IPv4/IPv6.
   - **CNAME (Canonical Name)**: Define alias para otros nombres de dominio.
   - **MX (Mail Exchange)**: Especifica los servidores de correo.
   - **TXT**: Permite almacenar información arbitraria, como configuraciones de seguridad (SPF, DKIM).

5. **Gestión de la resolución de nombres**  
   Sin estos archivos, los servidores DNS no podrían responder correctamente a las consultas de los clientes, lo que afectaría la conectividad y disponibilidad de los servicios en línea.

En resumen, los ficheros de zona son fundamentales para la administración de dominios y la correcta operación del DNS, garantizando la accesibilidad y la seguridad de los servicios en Internet.

## Obtener NS de un dominio usando nslookup
1) Escribir el comando nslookup
2) Definir el tipo de registro DNS: set type=ns
3) Escribir el dominio: Ejemplo: zonetransfer.me

# Aplicaciones Útiles
### Central Ops
Sirve mucho para las primeras fases de recopilación de información.

### DNS dumpster
### Sniffer: Wireshark
Sirve para ver el tráfico de red de un equipo
### Sniffer: TCPdump
