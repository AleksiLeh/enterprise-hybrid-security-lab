# Enterprise Hybrid Security Lab - Verkkotopologia ja VLAN-segmentointi

## 1. Laitteisto ja Ympäristö
* **Host:** HP ProDesk (Proxmox VE)
* **Palomuuri / Reititin:** OPNsense (asennettuna UFS-tiedostojärjestelmälle)
* **Hallintatyöasema:** Linux Mint (kytketty eristettyyn sisäverkkoon)

## 2. Proxmoxin Verkkosillat (Bridges)
* `vmbr0`: Kotiverkon / WAN-yhteys (isäntäkoneen hallinta)
* `vmbr1`: Eristetty sisäverkon silta (ilman fyysistä verkkokorttia), johon OPNsensen LAN (`vtnet1`) ja Linux Mint on kytketty.

## 3. VLAN-segmentit ja IP-osoiteavaruus

| VLAN ID | Alueen Nimi | Yhdyskäytävä (Gateway) | DHCP-alue | Käyttötarkoitus |
| :--- | :--- | :--- | :--- | :--- |
| **VLAN 10** | Corporate | `10.0.10.1/24` | `10.0.10.100` – `10.0.10.200` | Yrityksen simuloitu sisäverkko (työasemat) |
| **VLAN 20** | SOC | `10.0.20.1/24` | `10.0.20.100` – `10.0.20.200` | Valvonta, lokitus ja hallintatyökalut |
| **VLAN 30** | Honeypot | `10.0.30.1/24` | `10.0.30.100` – `10.0.30.200` | Haavoittuvat syöttölaitteet ja ansat |
| **VLAN 40** | Attacker | `10.0.40.1/24` | `10.0.40.100` – `10.0.40.200` | Hyökkäyskoneen / Red Team -toiminnan verkko |

<img width="1018" height="636" alt="kuva" src="https://github.com/user-attachments/assets/435cc914-551d-42f3-b617-7409dfadfac4" />

<img width="848" height="464" alt="kuva" src="https://github.com/user-attachments/assets/4cbb4f79-49c9-4a75-bf6c-3fe5e34e696e" />

<img width="1017" height="609" alt="kuva" src="https://github.com/user-attachments/assets/377ebf4b-23de-4f61-8917-96133b4b4e39" />
