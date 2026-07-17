# Proxmox VE

## Descripción

Proxmox VE es la plataforma de virtualización utilizada en el laboratorio **MS-LAB**.

Se implementó para centralizar los servicios del laboratorio en un único servidor físico, permitiendo ejecutar contenedores LXC y máquinas virtuales de forma aislada y eficiente.

Actualmente aloja el servidor de archivos Samba y será la base para futuras implementaciones como Active Directory, DNS, VPN y servicios de monitoreo.

---

# Especificaciones

| Característica | Valor |
|---------------|-------|
| Plataforma | Proxmox VE |
| Tipo | Servidor de virtualización |
| Gestión | Interfaz Web |
| Red | VLAN 40 - Servidores |
| IP | 192.168.40.2/28 |
| Gateway | 192.168.40.1 |

---

# Función dentro del laboratorio

- Virtualización de servicios
- Centralización de la infraestructura
- Ejecución de contenedores LXC
- Base para futuras máquinas virtuales

---

# Red

El servidor se encuentra conectado al Cisco Catalyst 2960 mediante un puerto configurado como **Trunk**.

El bridge principal (vmbr0) está asociado a la interfaz física y permite el acceso a la red de servidores (VLAN 40).

---

# Servicios implementados

Actualmente:

- ✅ Contenedor LXC
- ✅ Servidor Samba

Próximamente:

- Active Directory
- DNS
- VPN
- Docker
- Monitoreo
- Servidor Web

---

# Contenedores

| Nombre | Función | Estado |
|---------|----------|--------|
| fileserver | Servidor Samba | 🟢 Activo |

---

# Almacenamiento

El almacenamiento local se utiliza para:

- Contenedores LXC
- Backups
- Imágenes ISO

---

# Administración

La administración se realiza mediante la interfaz web de Proxmox.

URL:

https://192.168.40.2:8006

---

# Verificación

## Panel principal

<img width="1908" height="1034" alt="image" src="https://github.com/user-attachments/assets/8cadb955-21be-431c-a5e0-0f1749378cdc" />


---

## Nodo

<img width="1907" height="775" alt="image" src="https://github.com/user-attachments/assets/014a937e-2141-4464-9264-cad78e19bd45" />


---

## Contenedor LXC

<img width="1910" height="768" alt="image" src="https://github.com/user-attachments/assets/2a5db9e2-143d-46f2-8537-9d3e17e0eb88" />


---

## Configuración de red

<img width="1905" height="732" alt="image" src="https://github.com/user-attachments/assets/bae9cf0d-bd20-48b7-b460-288f513e9f27" />


---

# Próximas implementaciones

- Windows Server 2022
- Active Directory
- DNS
- Docker
- Uptime Kuma
- VPN
- Servidor de monitoreo

---

# Configuración

Los archivos de configuración relevantes pueden consultarse en:

configs/proxmox-network.txt

y en la documentación específica de cada servicio implementado.
