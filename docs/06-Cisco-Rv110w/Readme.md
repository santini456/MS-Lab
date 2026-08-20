Cisco RV110W
Descripción

El Cisco RV110W se utiliza dentro del laboratorio como Access Point, sin utilizar sus funciones de router, NAT, firewall o VPN.

El Cisco 2901 mantiene la responsabilidad del enrutamiento entre VLANs, NAT, DHCP y salida a Internet. El RV110W se encarga exclusivamente de proporcionar conectividad Wi-Fi y asociar cada SSID con la VLAN correspondiente mediante 802.1Q.

De esta forma, los dispositivos conectados por Wi-Fi mantienen la misma segmentación lógica y las mismas políticas de red que los equipos conectados directamente al Catalyst 2960.

Diagrama
Internet
   │
Cisco 2901
   │
   │ Trunk
   │
Catalyst 2960
   │ Fa0/24
   │ Trunk 802.1Q
   │
Cisco RV110W
192.168.99.6
Modo Access Point
   │
   ├── SSID ADMINISTRACION → VLAN 10
   │
   └── SSIDINVITADOS → VLAN 30
Especificaciones
Característica	Valor
Equipo	Cisco RV110W
Función	Access Point
Modo de operación	AP / Bridge
Gestión	Interfaz Web
Red de gestión	VLAN 99
IP de gestión	192.168.99.6/29
Gateway	192.168.99.1
Conexión	LAN 1
Puerto del switch	Catalyst 2960 Fa0/24
Enlace	Trunk 802.1Q
DHCP	Cisco 2901
Routing	Cisco 2901
NAT	Cisco 2901
Firewall	Cisco 2901
Función dentro del laboratorio
Proporcionar conectividad Wi-Fi.
Separar los clientes mediante VLANs.
Asociar cada SSID con su VLAN correspondiente.
Mantener la red de administración separada de las redes de usuarios.
Extender las políticas de segmentación existentes hacia la red inalámbrica.
Transportar las VLANs mediante un enlace 802.1Q Trunk hacia el Catalyst 2960.
VLANs configuradas
VLAN ID	Nombre	Uso
10	ADMINISTRACION	Usuarios / oficinas
20	MULTIMEDIA	Producción / multimedia
30	INVITADOS	Acceso de invitados
99	GESTION	Administración de equipos de red

La VLAN 1 corresponde a la VLAN por defecto del equipo y no se utiliza para el tráfico de los SSID ni para la administración del RV110W.

VLAN de gestión

El RV110W posee una dirección IP perteneciente a la VLAN 99:

IP:       192.168.99.6/29
Gateway:  192.168.99.1
VLAN:     99

Esta dirección permite acceder a la interfaz web de administración del equipo desde la red de gestión.

Configuración de VLAN Membership

El puerto físico utilizado para conectar el RV110W al Catalyst 2960 transporta las VLAN configuradas mediante etiquetas 802.1Q.

VLAN	LAN 1 / Trunk	LAN 2	LAN 3	LAN 4
1	Excluded	Excluded	Excluded	Excluded
10	Tagged	Excluded	Excluded	Excluded
20	Tagged	Excluded	Excluded	Excluded
30	Tagged	Excluded	Excluded	Excluded
99	Tagged	Excluded	Excluded	Excluded

Puerto LAN 1: utilizado como enlace troncal hacia el Catalyst 2960.

RV110W LAN 1
      │
      │ 802.1Q Trunk
      │ VLAN 10, 20, 30, 99
      │
Catalyst 2960 Fa0/24
SSIDs configurados
SSID	VLAN	Seguridad	Función
MSLAB-ADMINISTRACION	10	WPA2-PSK	Acceso inalámbrico de administración / usuarios
MSLAB-INVITADOS	30	WPA2-PSK	Acceso inalámbrico para invitados

Los SSID se encuentran asociados directamente a sus respectivas VLANs. De esta manera, un cliente conectado a MSLAB-ADMINISTRACION ingresa a la VLAN 10, mientras que un cliente conectado a MSLAB-INVITADOS ingresa a la VLAN 30.

Conexión hacia el switch

El RV110W se conecta físicamente al puerto Fa0/24 del Catalyst 2960.

El puerto se encuentra configurado como trunk, permitiendo transportar las VLAN necesarias hacia el Access Point.

                 TRUNK 802.1Q
┌──────────────────────────────┐
│      Catalyst 2960           │
│                              │
│ Fa0/24 ──────────────────────┼──── LAN 1
└──────────────────────────────┘      Cisco RV110W
                                      192.168.99.6
                                      VLAN 99

Las VLAN transportadas por el enlace son:

VLAN 10 → Administración
VLAN 20 → Multimedia
VLAN 30 → Invitados
VLAN 99 → Gestión
Servicios de red

El RV110W no entrega direcciones IP mediante DHCP.

La asignación de direcciones IP continúa siendo responsabilidad del Cisco 2901, que también proporciona:

DHCP.
Gateway de cada VLAN.
Enrutamiento inter-VLAN.
NAT.
Acceso a Internet.
Aplicación de las políticas de red mediante ACL.

Por lo tanto, el flujo de un cliente Wi-Fi es:

Cliente Wi-Fi
     │
     ▼
Cisco RV110W
     │
     │ VLAN 802.1Q
     ▼
Catalyst 2960
     │
     ▼
Cisco 2901
     │
     ├── DHCP
     ├── Routing
     ├── NAT
     └── Internet
Administración

El Cisco RV110W no dispone de una CLI/SSH utilizada para su configuración en este laboratorio.

La administración se realiza mediante su interfaz web utilizando la dirección:

https://192.168.99.6

La dirección pertenece a la VLAN 99 de gestión, manteniendo separada la administración del equipo respecto de las redes de usuarios e invitados.

Verificación

Para comprobar el funcionamiento del equipo se verifican los siguientes elementos:

VLAN Membership

Se verifica que el puerto LAN 1 transporte las VLAN:

10 → Tagged
20 → Tagged
30 → Tagged
99 → Tagged
SSIDs

Se verifica la existencia de:

MSLAB-ADMINISTRACION → VLAN 10
MSLAB-INVITADOS      → VLAN 30
Cliente conectado

Al conectar un dispositivo al SSID correspondiente, se debe comprobar que:

Reciba una dirección IP mediante DHCP.
La dirección pertenezca a la red de la VLAN correspondiente.
Utilice como gateway la dirección del Cisco 2901.
Pueda acceder a los recursos permitidos por las ACL.
Tenga salida a Internet cuando la política de esa VLAN lo permita.
Ubicación dentro de la infraestructura
                    INTERNET
                       │
                       ▼
                 ┌───────────┐
                 │ Cisco 2901│
                 │  Routing  │
                 │ DHCP/NAT  │
                 └─────┬─────┘
                       │
                       │ Trunk
                       ▼
              ┌─────────────────┐
              │  Catalyst 2960  │
              │                 │
              │ VLAN 10         │
              │ VLAN 20         │
              │ VLAN 30         │
              │ VLAN 99         │
              └────────┬────────┘
                       │ Fa0/24
                       │ 802.1Q Trunk
                       ▼
                ┌──────────────┐
                │ Cisco RV110W │
                │ Access Point │
                │ 192.168.99.6 │
                └──────┬───────┘
                       │
             ┌─────────┴─────────┐
             │                   │
             ▼                   ▼
      MSLAB-ADMINISTRACION   MSLAB-INVITADOS
             │                   │
          VLAN 10              VLAN 30
Nota de configuración

Hay una pequeña inconsistencia en el texto original: se menciona que el RV110W permite 3 VLAN adicionales a la VLAN 1, pero la configuración que pasaste utiliza 4 VLAN etiquetadas: 10, 20, 30 y 99. Para que la documentación coincida con la configuración que efectivamente estás describiendo, arriba lo dejé como VLAN 10/20/30/99 y VLAN 1 excluida.

Además, aunque actualmente los SSID publicados son solamente VLAN 10 y VLAN 30, la VLAN 20 queda transportada por el trunk para mantener disponible la segmentación del laboratorio.
