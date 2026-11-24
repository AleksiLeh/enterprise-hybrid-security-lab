# enterprise-hybrid-security-lab
Homelab for practicing security, networks and administration skills

# Enterprise Hybrid Security Lab

A comprehensive, hands-on enterprise network and cybersecurity lab built on Proxmox VE. Designed to simulate multi-layered network segmentation, firewall management, and security monitoring environments.

---

## 🏗️ Architecture & Network Design
The lab environment is hosted on a physical HP ProDesk node running **Proxmox VE**, utilizing virtualized firewalls and segmented VLANs:
* **Hypervisor:** Proxmox VE
* **Firewall / Router:** OPNsense
* **Network Zones (Planned):**
  * **WAN / Management:** Initial gateway and hypervisor access.
  * **LAN / Corporate:** Trusted internal network segment.
  * **DMZ / Services:** Public-facing or shared services.
  * **SOC / Monitoring:** Security tools and SIEM logging.
  * **Honeypot / Attacker:** Isolated segments for threat simulation.

---

## 📂 Documentation & Phase Log
Step-by-step documentation and troubleshooting notes are tracked in the `docs/` directory:
* [Phase 1: Proxmox VE Installation & Network Troubleshooting](docs/01-proxmox-installation.md)
* [Phase 2: OPNsense Firewall Setup & Configuration](docs/02-opnsense-setup.md)

---

## 🚀 Objectives & Skills Demonstrated
* Hypervisor deployment and local console management.
* Network troubleshooting (Subnets, Gateways, Bridges, and Routing).
* Virtualized firewall and security perimeter configuration.
* Enterprise documentation and infrastructure-as-documentation practices.
