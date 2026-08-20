Decisiones

Este archivo es para justificar las acciones que tomé al configurar este laboratorio

VLAN 40 (/28)

La red de servidores utiliza una máscara /28 debido a la baja cantidad de dispositivos previstos (Proxmox, contenedores LXC y futuras máquinas virtuales), reduciendo el desperdicio de direcciones IP.

VLAN 99 (/29)

La VLAN de gestión está destinada exclusivamente a la administración de equipos de red. Se eligió una máscara /29 por requerir únicamente direcciones para el router, switch y estación de administración.

Router-on-a-Stick

Se implementó Router-on-a-Stick utilizando un Cisco 2901 para practicar enrutamiento Inter-VLAN con hardware real, simulando una infraestructura de pequeña empresa.

Proxmox

Se optó por Proxmox VE como plataforma de virtualización para centralizar los servicios del laboratorio y facilitar futuras implementaciones como Active Directory, DNS y VPN.

Samba

Se implementó un servidor Samba dentro de un contenedor LXC para ofrecer almacenamiento compartido en la VLAN de servidores, replicando un servicio habitual en pequeñas organizaciones.

ACLs

Decidí implementar ACLs extendidas en lugar de una única ACL genérica para poder controlar de forma más precisa qué puede hacer cada VLAN, no solo permitir o denegar salida a Internet.

La idea fue simular políticas reales de una organización pequeña: las redes de usuarios (Administración y Producción/Multimedia) necesitan llegar a recursos puntuales del sector de Servidores (el FileServer), pero no tienen ningún motivo para acceder al resto de esa VLAN ni a la red de Gestión, donde administro el router, el switch y el Access Point. Por eso cada ACL permite explícitamente los hosts necesarios y deniega el resto de esas dos redes, dejando el resto del tráfico (incluida la salida a Internet) permitido.

Para la red de Invitados apliqué el criterio opuesto: no tiene motivo para acceder a ninguna red interna, así que deniego explícitamente el acceso a las demás VLANs y solo dejo pasar la salida a Internet.

Durante la implementación cometí un error que me sirvió como aprendizaje: al promover el servidor a Controlador de Dominio, las ACLs de Administración y Multimedia todavía no contemplaban el acceso al Controlador de Dominio (192.168.40.5), por lo que ningún equipo de esas VLANs podía autenticarse contra el dominio. Además, al corregirlo, en un primer intento invertí por error las reglas entre ambas VLANs y también eliminé sin darme cuenta la ACL completa de Invitados, lo que dejó esa red sin ningún filtro aplicado. Esto me dejó como práctica la importancia de verificar con show access-lists después de cualquier cambio, en lugar de asumir que un comando se aplicó correctamente solo porque no arrojó ningún error.

Active Directory

Implementé Active Directory Domain Services (AD DS) en un Windows Server dentro de Proxmox para practicar administración centralizada de identidades, como se usa en la mayoría de las organizaciones reales. Junto con AD DS instalé también el rol de DNS, ya que Active Directory depende directamente de un DNS funcionando correctamente para operar (localización de controladores de dominio, autenticación, etc.). Configuré forwarders hacia DNS públicos para que los clientes que usan este servidor como DNS también puedan resolver nombres de Internet, además de la zona interna mslab.local.

Todavía me falta sumar la estructura de Unidades Organizativas, usuarios, grupos de seguridad y GPOs, que planeo documentar en una próxima etapa.

Access Point

Incorporé un Cisco RV110W en modo Access Point puro (sin usar sus funciones de router/firewall/VPN) para dar cobertura wifi segmentada por VLAN. Configuré el puerto hacia el switch en modo trunk, con SSIDs independientes asociados a la VLAN de Administración y a la VLAN de Invitados, para que cada red inalámbrica mantenga la misma segmentación y las mismas políticas de ACL que ya tenía definidas para el resto del laboratorio.
