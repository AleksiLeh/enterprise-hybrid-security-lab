# Enterprise Hybrid Security Lab - Network Topology and VLAN Segmentation

## 1. Hardware and Environment
- **Host:** HP ProDesk (Proxmox VE)
- **Firewall / Router:** OPNsense (installed on UFS file system)
- **Management Workstation:** Linux Mint (connected to an isolated internal network)

---

## 2. Proxmox Network Bridges
- `vmbr0`: Home network / WAN connection (host management)
- `vmbr1`: Isolated internal network bridge (without a physical network card), to which the OPNsense LAN (`vtnet1`) and Linux Mint are connected.

---

## 3. VLAN Segments and IP Address Space

| VLAN ID | Area Name | Gateway | DHCP Range | Purpose |
| :--- | :--- | :--- | :--- | :--- |
| **VLAN 10** | Corporate | `10.0.10.1/24` | Simulated corporate internal network (workstations) |
| **VLAN 20** | SOC | `10.0.20.1/24` | Monitoring, logging, and management tools |
| **VLAN 30** | Honeypot | `10.0.30.1/24` | Vulnerable decoy systems and traps |
| **VLAN 40** | Attacker | `10.0.40.1/24` | Attack machine / Red Team activity network |

<img width="1018" height="636" alt="kuva" src="https://github.com/user-attachments/assets/435cc914-551d-42f3-b617-7409dfadfac4" />

<img width="848" height="464" alt="kuva" src="https://github.com/user-attachments/assets/4cbb4f79-49c9-4a75-bf6c-3fe5e34e696e" />

<img width="1017" height="609" alt="kuva" src="https://github.com/user-attachments/assets/377ebf4b-23de-4f61-8917-96133b4b4e39" />

Putting DHCP on in interfaces

<img width="1015" height="512" alt="kuva" src="https://github.com/user-attachments/assets/ceddd1f0-0f08-4d74-ba02-5ed9237273af" />
