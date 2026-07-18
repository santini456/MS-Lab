# Decisiones 

Este archivo es para justificar las acciones que tome al configurar este laboratorio

#







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
