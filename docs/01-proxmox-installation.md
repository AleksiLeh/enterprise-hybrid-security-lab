Markdown

# Phase 1: Proxmox VE Installation & Initial Setup

## Objective
Install and configure Proxmox VE on the physical HP ProDesk server node to serve as the core hypervisor for the enterprise hybrid security lab.

## Prerequisites & Media Preparation
1. Downloaded the official Proxmox VE ISO image.
2. Flashed the ISO onto a USB flash drive using Rufus.
3. Connected physical display, keyboard, and Ethernet cable to the HP ProDesk node.

## Installation Steps
1. Booted the server from the USB installation media and selected **Install Proxmox VE**.
2. Accepted the End User License Agreement (EULA) and selected the target NVMe/SSD drive for installation.
3. Configured localization settings (Country, Time Zone, Keyboard layout).
4. Set a strong `root` password and provided a valid administrator email address.
5. Configured management network settings:
   - **Management Interface:** Selected the primary physical NIC.
   - **Hostname:** `pve.lab.local`
   - **IP Address & Gateway:** Assigned initial static network parameters.
6. Completed the installation and rebooted the server into the Proxmox login console.
