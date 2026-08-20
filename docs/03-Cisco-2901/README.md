# Cisco 2901

## Descripción

El Cisco 2901 actúa como router principal del laboratorio MS-LAB.

Sus funciones son:

- Enrutamiento entre VLANs (Router-on-a-Stick)
- Servidor DHCP
- NAT/PAT para salida a Internet
- Administración remota mediante SSH
- ACLS

 ## ACL

S## ACL

Se implementaron ACLs extendidas para controlar el tráfico entre VLANs, restringiendo el acceso a las redes de Servidores y Gestión desde las demás VLANs, y permitiendo únicamente el acceso puntual a los recursos necesarios.

**ADMINISTRACION** (VLAN 10) y **PRODUCCION-MULTIMEDIA** (VLAN 20)
- Se permite el acceso al FileServer (`192.168.40.3`)
- Se permite el acceso al Controlador de Dominio (`192.168.40.5`), necesario para autenticación de usuarios y equipos contra Active Directory
- Se deniega el acceso al resto de la red de Servidores (VLAN 40)
- Se deniega el acceso a la red de Gestión (VLAN 99)
- Se permite el resto del tráfico (incluyendo salida a Internet)

**INVITADOS** (VLAN 30)
- Se deniega el acceso a todas las demás VLANs internas (Administración, Multimedia, Servidores, Gestión)
- Se permite únicamente la salida a Internet

Además, se mantiene una ACL estándar (`access-list 1`) utilizada junto con NAT/PAT para permitir la salida a Internet de todo el rango `192.168.0.0/16`.



---

## Interfaces

| Interfaz | Función |
|----------|---------|
| Gi0/0 | WAN (Internet) |
| Gi0/1 | Enlace Trunk hacia el Catalyst 2960 |

---

## Subinterfaces

| Interfaz | VLAN | Red |
|----------|------|----------------|
| Gi0/1.10 | 10 | 192.168.10.0/24 |
| Gi0/1.20 | 20 | 192.168.20.0/24 |
| Gi0/1.30 | 30 | 192.168.30.0/24 |
| Gi0/1.40 | 40 | 192.168.40.0/28 |
| Gi0/1.99 | 99 | 192.168.99.0/29 |

---

## Servicios implementados

- ✅ Router-on-a-Stick (802.1Q)
- ✅ DHCP
- ✅ NAT/PAT
- ✅ SSH
- ✅ ACL

---

## Verificación

### Interfaces

<img width="870" height="498" alt="image" src="https://github.com/user-attachments/assets/3e7c56e0-3788-4298-82f7-5e85c8e1269e" />


---

### Tabla de rutas

<img width="1118" height="650" alt="image" src="https://github.com/user-attachments/assets/00ac82aa-7576-4416-9ec4-5548d82c4705" />


---

### Configuración DHCP

<img width="897" height="404" alt="image" src="https://github.com/user-attachments/assets/3e6565ce-04e2-4759-8890-026b609e7114" />


---

### Configuración de subinterfaces


<img width="1628" height="617" alt="image" src="https://github.com/user-attachments/assets/dd0e0060-5bff-42d3-aa70-a75bc7a101b7" />

---

Configuración de ACL



<img width="630" height="415" alt="image" src="https://github.com/user-attachments/assets/d8e197b7-8fd2-4048-983e-f235fb7638c4" />



## Configuración completa

La configuración completa del router se encuentra en:

configs/RT-01-running-config.txt
