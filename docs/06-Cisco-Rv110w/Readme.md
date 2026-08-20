Cisco RV110W
Descripción

El Cisco RV110W se incorporó al laboratorio en modo Access Point puro, sin utilizar sus funciones nativas de router, firewall o VPN. El enrutamiento, NAT y DHCP siguen siendo responsabilidad exclusiva del Cisco 2901.

Su función es brindar cobertura wifi segmentada, asociando cada SSID a la VLAN correspondiente mediante 802.1Q, replicando la misma segmentación y políticas de ACL ya definidas para el resto del laboratorio.


Red de gestión	VLAN 99 - Gestión
IP de gestión:	192.168.99.6/29
Gateway:	192.168.99.1
Conexión	Puerto LAN 1 → Trunk hacia Catalyst 2960 (Gi0/1)
Diagrama
Internet
   │
Cisco 2901
   │
Catalyst 2960 (Trunk Gi0/1)
   │
Cisco RV110W (192.168.99.6) - Modo Access Point
   │
   ├── SSID Administración → VLAN 10
   └── SSID Invitados      → VLAN 30
VLAN Membership

Como el equipo solo permite crear 3 VLANs adicionales a la VLAN 1 (Default), se utilizó el siguiente mapeo:

VLAN ID	Descripción	Uso
1	Default	Invitados
10	Administración	Red de usuarios / oficinas
20	Multimedia	Producción / Multimedia
30 INVITADOS
99	Gestión	Administración de equipos de red



VLAN ID	Puerto 1 (Trunk)	Puerto 2	Puerto 3	Puerto 4
1	Excluded	Excluded	Excluded	Excluded
10	Tagged	Excluded	Excluded	Excluded
30  Tagged  Excluded  Excluded  Excluded
20	Tagged	Excluded	Excluded	Excluded
99	Tagged	Excluded	Excluded	Excluded
SSIDs
SSID	VLAN	Seguridad
MSLAB-ADMINISTRACION	10	WPA2-PSK
MSLAB-INVITADOS	30	WPA2-PSK
Conexión hacia el switch

El puerto físico del RV110W se conecta al puerto fa 0/24 del Catalyst 2960, configurado en modo trunk, permitiendo el paso de las 4 VLANs etiquetadas:



El DHCP para los clientes wifi de cada VLAN es entregado por el Cisco 2901, no por el RV110W. El decisorio completo de por qué se optó por este equipo en modo Access Point, en lugar de usarlo como router/firewall, se encuentra documentado en Decisiones.md.

Verificación

Este equipo no dispone de CLI/SSH para configuración; toda la gestión se realiza mediante su interfaz web. A continuación se documentan las pantallas de configuración relevantes.

VLAN Membership


<img width="1913" height="947" alt="image" src="https://github.com/user-attachments/assets/487d0138-d048-400d-a05f-a96eea2f2b25" />





SSIDs configurados

<img width="1911" height="948" alt="image" src="https://github.com/user-attachments/assets/a5e2e740-ac95-4378-afcf-f380b42a6ccd" />


Cliente conectado 
<img width="354" height="770" alt="image" src="https://github.com/user-attachments/assets/16258979-0506-4ba2-b324-d2f0f6e345cd" />

