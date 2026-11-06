# Lab 01 — VLAN Segmentation & Trunking

## Objective

Configure VLAN segmentation and 802.1Q trunking
across a small multi-switch network.

## Technologies

- Cisco IOS
- VLANs
- Access Ports
- 802.1Q Trunking
- Layer 2 Switching

## VLANs

| VLAN | Name | Network |
|------|------|---------|
| 10 | HR | 192.168.10.0/24 |
| 20 | IT | 192.168.20.0/24 |
| 30 | SALES | 192.168.30.0/24 |
| 99 | MANAGEMENT | 192.168.99.0/24 |

## Topology
<img width="899" height="600" alt="image" src="https://github.com/user-attachments/assets/c55527fb-c293-4981-896a-e523e8adafe1" />



## Verification
<img width="686" height="702" alt="image" src="https://github.com/user-attachments/assets/ed9a3c26-6cd9-4e01-9533-cfa1055c18cb" />


## Outcome
Switches are configured with vlans and ports are assigned accordingly. After that trunking is done on the switches and it only allows the required vlans to carry traffic. Management vlan is configured as native vlan
