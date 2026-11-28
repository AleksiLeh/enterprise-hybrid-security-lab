# Enterprise Hybrid Security Lab - Firewall Rules and Traffic Control

This document outlines the firewall rules, traffic control policies, and segmentation logic implemented in OPNsense for the Proxmox-based enterprise hybrid security lab.

## 1. Default Security Posture
OPNsense enforces an **Implicit Deny** policy on all newly created VLAN interfaces. By default, all incoming traffic is blocked unless an explicit `Pass` rule is defined.

---

## 2. VLAN Firewall Rules and Access Control Lists (ACLs)

| Interface | Action | Source | Destination | Description / Purpose |
| :--- | :--- | :--- | :--- | :--- |
| **Corporate** (VLAN 10) | Pass | `CORPORATE net` | `any` | Allows workstations to access the internet and standard network services. |
| **SOC** (VLAN 20) | Pass | `SOC net` | `any` | Grants monitoring and management workstations full visibility across networks. |
| **Honeypot** (VLAN 30) | Block | `HONEYPOT net` | `any` | Isolates decoy systems and blocks any outbound malicious traffic. |
| **Attacker** (VLAN 40) | Block | `ATTACKER net` | `CORPORATE net` | Prevents the attacker network from reaching the corporate internal network. |
| **Attacker** (VLAN 40) | Pass | `ATTACKER net` | `HONEYPOT net` | Allows the attack machine to target and test the honeypot systems. |

---

## 3. Configuration Principles
1. **Rule Evaluation Order:** OPNsense processes firewall rules from **top to bottom**, stopping at the first matching rule. Specific **Block** rules must always be positioned above broader **Pass** rules.
2. **Gateway Assignment:** Default gateway configurations are used for standard routing unless specific tunneling (such as VPN) is required.

<img width="429" height="443" alt="kuva" src="https://github.com/user-attachments/assets/465e6dae-a118-4591-b0dc-ee774ed33800" />

<img width="539" height="558" alt="kuva" src="https://github.com/user-attachments/assets/b0cb6614-c257-4bbd-bea3-599184ab481a" />

<img width="1039" height="398" alt="kuva" src="https://github.com/user-attachments/assets/b80bb5ea-623f-4fef-ae2e-d190c4d58128" />

