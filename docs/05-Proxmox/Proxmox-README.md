# Proxmox VE

## Descripción

Proxmox VE es la plataforma de virtualización utilizada en el laboratorio MS-LAB.

Se implementó para centralizar los servicios del laboratorio en un único servidor físico, permitiendo ejecutar contenedores LXC y máquinas virtuales de forma aislada y eficiente.

Actualmente aloja el servidor de archivos Samba y el controlador de dominio (Active Directory / DNS), y será la base para futuras implementaciones como VPN y servicios de monitoreo.

## Diagrama

Internet │ Cisco 2901 │ Catalyst 2960 (Trunk) │ Proxmox VE (192.168.40.2) │ ├── LXC - FileServer (Samba) │ └── VM - DC01 (Windows Server / AD DS / DNS)

## Especificaciones

| Característica | Valor |
|---|---|
| Plataforma | Proxmox VE |
| Tipo | Servidor de virtualización |
| Gestión | Interfaz Web |
| Red | VLAN 40 - Servidores |
| IP | 192.168.40.2/28 |
| Gateway | 192.168.40.1 |

## Función dentro del laboratorio

- Virtualización de servicios
- Centralización de la infraestructura
- Ejecución de contenedores LXC
- Ejecución de máquinas virtuales

## Red

El servidor se encuentra conectado al Cisco Catalyst 2960 mediante un puerto configurado como Trunk.

El bridge principal (vmbr0) está asociado a la interfaz física y permite el acceso a la red de servidores (VLAN 40).

## Servicios implementados

Actualmente:

- ✅ Contenedor LXC
- ✅ Servidor Samba
- ✅ Máquina Virtual - Windows Server
- ✅ Active Directory Domain Services (AD DS)
- ✅ DNS

Próximamente:

- OUs, Usuarios, Grupos y GPOs
- Docker
- Monitoreo
- Servidor Web
- VPN

## Contenedores

| Nombre | Función | Estado |
|---|---|---|
| fileserver | Servidor Samba | 🟢 Activo |

## Máquinas Virtuales

| Nombre | Función | Sistema Operativo | IP | Estado |
|---|---|---|---|---|
| DC01 | Controlador de Dominio (AD DS / DNS) | Windows Server 2022 | 192.168.40.5 | 🟢 Activo |

### Active Directory

El servidor DC01 fue promovido a Controlador de Dominio, dejando operativo el dominio interno del laboratorio `mslab.local`.

Junto con AD DS se instaló el rol de DNS, encargado de resolver la zona interna del dominio. Se configuraron *forwarders* (`8.8.8.8` / `1.1.1.1`) para permitir además la resolución de nombres hacia Internet a los clientes que usan este servidor como DNS.

Pendiente: estructura de Unidades Organizativas (OUs), usuarios, grupos de seguridad y GPOs.

## Almacenamiento

El almacenamiento local se utiliza para:

- Contenedores LXC
- Máquinas virtuales
- Backups
- Imágenes ISO

## Administración

La administración se realiza mediante la interfaz web de Proxmox.

URL:
https://192.168.40.2:8006

## Verificación

### Panel principal
<img width="1915" height="942" alt="image" src="https://github.com/user-attachments/assets/fe171a25-d3a6-4412-bc60-ceaef1795287" />


### Nodo
<img width="1918" height="941" alt="image" src="https://github.com/user-attachments/assets/ebec4209-c333-40fa-ac65-6d3f77d652b0" />


### Contenedor LXC
<img width="1913" height="943" alt="image" src="https://github.com/user-attachments/assets/5c65120d-f02d-4dd2-81cd-88b113c49002" />




### Máquina Virtual - Windows Server
<img width="1913" height="953" alt="image" src="https://github.com/user-attachments/assets/32c598c8-9afa-4de8-803c-6a68dce2741b" />


### Active Directory - Controlador de Dominio
<img width="1912" height="943" alt="image" src="https://github.com/user-attachments/assets/b8db0917-4323-41e4-b16d-5f6510e8d1a3" />



## Próximas implementaciones

- OUs, Usuarios, Grupos y GPOs
- Docker
- Uptime Kuma
- VPN
- Servidor de monitoreo

## Configuración

Los archivos de configuración relevantes pueden consultarse en:
configs/proxmox-network.txt

y en la documentación específica de cada servicio implementado.
