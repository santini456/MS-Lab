# Cisco 2901

## Descripción

El Cisco 2901 actúa como router principal del laboratorio MS-LAB.

Sus funciones son:

- Enrutamiento entre VLANs (Router-on-a-Stick)
- Servidor DHCP
- NAT/PAT para salida a Internet
- Administración remota mediante SSH

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

## Configuración completa

La configuración completa del router se encuentra en:

configs/RT-01-running-config.txt
