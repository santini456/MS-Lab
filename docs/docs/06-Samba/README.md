# Servidor de Archivos (Samba)

## Descripción

Como parte de la infraestructura del laboratorio **MS-LAB**, se implementó un servidor de archivos utilizando **Samba** sobre un contenedor LXC en Proxmox VE.

El objetivo es ofrecer almacenamiento compartido dentro de la red de servidores, simulando un servicio habitual en entornos empresariales.

---

# Especificaciones

| Característica | Valor |
|---------------|-------|
| Plataforma | Proxmox VE |
| Tipo | Contenedor LXC |
| Sistema Operativo | Ubuntu Server |
| Servicio | Samba |
| Red | VLAN 40 - Servidores |
| Dirección IP | 192.168.40.3 |

---

# Funciones implementadas

- Compartición de archivos mediante SMB/CIFS
- Acceso desde equipos Windows
- Integración con la VLAN de servidores
- Administración mediante SSH

---

# Topología

Cliente Windows

↓

Cisco Catalyst 2960

↓

Cisco 2901

↓

Proxmox VE

↓

Contenedor LXC

↓

Servidor Samba

---

# Recursos compartidos

| Recurso | Descripción |
|----------|-------------|
| Compartida | Carpeta compartida para pruebas del laboratorio |

---

# Configuración de red

| Parámetro | Valor |
|-----------|-------|
| IP | 192.168.40.3 |
| Máscara | 255.255.255.240 |
| Gateway | 192.168.40.1 |

---

# Acceso

Desde un equipo Windows:

\\192.168.40.3\Compartida

o utilizando el nombre del servidor (cuando exista resolución DNS).

---

# Verificación

## Contenedor en ejecución

<img width="1911" height="779" alt="image" src="https://github.com/user-attachments/assets/7b8328b9-15cc-4118-9b66-eafe0015bd49" />


---

## Servicio Samba

<img width="1046" height="425" alt="image" src="https://github.com/user-attachments/assets/edf66d42-62ad-464e-851f-992844104518" />


---

## Acceso desde Windows

<img width="1121" height="646" alt="image" src="https://github.com/user-attachments/assets/afd8d128-74fd-47de-9b7a-0b8fc4f662cd" />


---


# Configuración

La configuración completa del servicio puede consultarse en:

<img width="1448" height="578" alt="image" src="https://github.com/user-attachments/assets/01a9a426-f18e-4bea-9721-eb5de469d0d1" />


---

# Próximas mejoras

- Integración con Active Directory
- Autenticación centralizada
- Permisos por grupos
- Resolución de nombres mediante DNS
