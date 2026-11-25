# Phase 2: OPNsense Firewall Setup & Configuration

## Objective
Deploy OPNsense as a virtual firewall on Proxmox VE to handle future network segmentation and VLAN routing.

## Implementation Steps
1. Created a new VM (`ID: 100`, Name: `OPNsense-Firewall`) with 2 vCPUs, 2 GB RAM, and 25 GB NVMe storage.
2. Mounted the OPNsense ISO image and completed the disk installation using default UFS parameters.
3. Removed the installation media and rebooted the VM into the live environment.
4. Assigned initial network interfaces (WAN/LAN) via the console prompt.


## Network Interface & IP Configuration
5. Detached the installation ISO media from the VM hardware settings.
6. Assigned interfaces via the OPNsense console:
   - **WAN:** `vtnet0` (DHCP from home router)
   - **LAN:** `vtnet1`
<img width="865" height="448" alt="kuva" src="https://github.com/user-attachments/assets/1f707d72-6707-4b0c-859c-026e8beba3e2" />

7. Reconfigured the LAN interface IP address from the default `192.168.1.1/24` to `10.0.1.1/24` (with DHCP enabled for `10.0.1.100 - 10.0.1.200`) to avoid IP conflicts with the upstream home router.
<img width="1601" height="675" alt="kuva" src="https://github.com/user-attachments/assets/10cdb004-2c72-4cb6-9971-72409c5b81e6" />
<img width="1050" height="412" alt="kuva" src="https://github.com/user-attachments/assets/68e70cca-6903-409e-ad4c-3c8d01098b05" />

