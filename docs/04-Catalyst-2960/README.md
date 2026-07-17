# Cisco Catalyst 2960

## Descripción

El Cisco Catalyst 2960 es el switch principal del laboratorio **MS-LAB**.

Su función es realizar la segmentación de la red mediante VLANs, transportar el tráfico etiquetado hacia el router utilizando enlaces Trunk (IEEE 802.1Q) y conectar los dispositivos finales a sus respectivas redes.

---

# Especificaciones

| Modelo | Cisco Catalyst 2960 |
|---------|---------------------|
| Sistema Operativo | Cisco IOS 15.0 |
| Función | Switch de acceso |
| Rol | Segmentación de red |

---

# Funciones implementadas

- VLANs
- Puertos Access
- Enlace Trunk 802.1Q
- Spanning Tree (PVST)
- Administración remota mediante SSH
- VLAN de gestión

---

# VLANs configuradas

| VLAN | Nombre | Red |
|------|-------------|----------------|
| 10 | Administración | 192.168.10.0/24 |
| 20 | Producción/Multimedia | 192.168.20.0/24 |
| 30 | Invitados | 192.168.30.0/24 |
| 40 | Servidores | 192.168.40.0/28 |
| 99 | Gestión | 192.168.99.0/29 |

---

# Interfaces destacadas

| Puerto | Función |
|---------|----------|
| Gi0/1 | Trunk hacia RT-01 |
| Fa0/14 | Servidor (VLAN 40) |
| Fa0/19 | Cliente Invitados (VLAN 30) |

> El resto de los puertos pueden asignarse dinámicamente según las necesidades del laboratorio.

---

# Trunk

El enlace entre el switch y el router utiliza encapsulación IEEE 802.1Q para transportar múltiples VLAN a través de un único enlace físico.

### VLANs permitidas

- VLAN 10
- VLAN 20
- VLAN 30
- VLAN 40
- VLAN 99

---

# Administración

El switch se administra mediante SSH utilizando la VLAN 99 (Gestión).

IP de administración:

192.168.99.2/29

Gateway:

192.168.99.1

---

# Verificación

## VLANs

<img width="1833" height="297" alt="image" src="https://github.com/user-attachments/assets/2096f825-6d7e-4fda-9b54-acfe6fc5aebd" />


---

## Trunk

<img width="688" height="347" alt="image" src="https://github.com/user-attachments/assets/8fd9869c-22ba-4471-811c-5df7d8c6383f" />


---


## Configuración completa

La configuración completa puede consultarse en:

configs/SW-01-running-config.txt
