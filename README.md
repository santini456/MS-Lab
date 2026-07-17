Banner

<img width="1088" height="779" alt="image" src="https://github.com/user-attachments/assets/f9ec4258-0d40-4474-99a8-75495057fb90" />


MS-LAB
Laboratorio personal de infraestructura IT

Desarrollado como complemento a mi formación en la Escuela Técnica N°5 de Lanús.

El objetivo de este laboratorio es implementar tecnologías utilizadas en entornos reales, documentar cada configuración y adquirir experiencia práctica en infraestructura IT.

Tecnologías
Tecnología	Estado
Cisco IOS	✅
VLAN	✅
Router-on-a-Stick	✅
DHCP	✅
NAT/PAT	✅
SSH	✅
Proxmox VE	✅
Samba	✅
ACL	🔄
Active Directory	⏳
DNS	⏳
VPN	⏳
Hardware
Equipo	Modelo
Router	Cisco 2901
Switch	Cisco Catalyst 2960
Switch	Cisco SLM224G
Servidor	Proxmox VE
Cliente	Windows 11
Topología

<img width="700" height="702" alt="image" src="https://github.com/user-attachments/assets/bc7c7c78-cea7-45cb-ad9d-dc7632ee11e7" />


Direccionamiento
VLAN	Nombre	Red
10	Administración	192.168.10.0/24
20	Producción	192.168.20.0/24
30	Invitados	192.168.30.0/24
40	Servidores	192.168.40.0/28
99	Gestión	192.168.99.0/29
Implementaciones
Router-on-a-Stick

✔ Subinterfaces 802.1Q

✔ Gateways

✔ Routing Inter-VLAN

DHCP

✔ Pool independiente por VLAN

✔ Exclusión de direcciones

✔ Gateway automático

NAT

✔ Acceso a Internet

✔ PAT

SSH

✔ Acceso remoto seguro

Virtualización

✔ Proxmox VE

✔ Contenedor LXC

✔ Servidor Samba

Roadmap
 VLANs
 DHCP
 NAT
 SSH
 Samba
 ACLs
 Active Directory
 DNS
 VPN
 Wireless




