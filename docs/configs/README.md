# Configuraciones

Esta carpeta contiene las configuraciones completas de los equipos utilizados en el laboratorio **MS-LAB**.

El objetivo es conservar una copia de las configuraciones implementadas durante cada etapa del proyecto, facilitando su consulta, documentación y control de versiones.

---

# Equipos

| Equipo | Archivo |
|---------|---------|
| Cisco 2901 | RT-01-running-config.txt |
| Cisco Catalyst 2960 | SW-01-running-config.txt |

---

# Contenido

Las configuraciones incluyen, según corresponda:

## Router (Cisco 2901)

- Interfaces
- Subinterfaces 802.1Q
- Router-on-a-Stick
- VLAN Gateways
- DHCP
- NAT/PAT
- SSH
- Usuarios locales
- Configuración WAN

---

## Switch (Cisco Catalyst 2960)

- VLANs
- Trunk
- Puertos Access
- VLAN de Gestión
- SSH
- Spanning Tree

---

# Notas

Las configuraciones corresponden al estado actual del laboratorio al momento de cada versión publicada.

A medida que el proyecto evolucione (ACLs, Active Directory, VPN, etc.), los archivos serán actualizados y versionados mediante Git.

---

# Relación con la documentación

La explicación detallada de cada implementación se encuentra en la carpeta:

docs/

Mientras que esta carpeta contiene únicamente las configuraciones completas exportadas desde los equipos.
