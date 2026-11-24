Markdown

# Phase 1: Proxmox VE Installation & Network Troubleshooting

## Challenge
The Proxmox VE web management interface (`https://192.168.100.2:8006`) was initially unreachable from the workstation. 
The browser encountered connection timeouts and `Host unreachable` errors because the server's network bridge (`vmbr0`) was not on the same subnet as the home router.

## Solution
1. Connected a physical monitor and keyboard directly to the Proxmox server node.
2. Logged into the local Proxmox console using `root` credentials.
3. Edited the network configuration file:
   ```bash
   nano /etc/network/interfaces

    Replaced the misconfigured IP address with a static IP matching the local subnet and defined the correct gateway.
    IP address changed from 192.168.100.2/24 to 192.168.1.100/24
    Default gateway changed from 192.168.1.2 to 192.168.1.1

    After this it still didn't work but all it needed was a restart for the networking system.

    Restarted the networking service to apply changes:
    Bash

    systemctl restart networking

    Verified successful connection via web browser at https://192.168.1.100:8006.
    And used ip a command on proxmox CLI to check vmbr0 address which changed to 192.168.1.100
