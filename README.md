# Cybersecurity Lab

A hands on lab focused on cybersecurity, enterprise style network design, and IT best practices.



## Lab Overview

This lab simulates a small enterprise network with segmented security zones, firewalling, virtualized workloads, and layered defenses, enabling both blue-team (defensive) and red-team (offensive) cybersecurity practice. 



## Lab Modules

Documentation approach: Each module includes an overview, architecture details, key security configurations, challenges/validation and summarized implementation notes.

1. **OPNsense Firewall Deployment & Baseline Hardening** <br>
Firewall installation, interface configuration, NAT, DNS, DHCP, logging, VPN, device hardening <br>
→ [opnsense-deployment](labs/opnsense-deployment/opnsense-deployment.md)

2. **Local Network Segmentation w/ VLANs** <br>
Network security zones, switch & WAP configuration, firewall rules, 802.1Q VLAN trunking, wireless & Ethernet networking <br>
→ [local-network-segmentation](labs/local-network-segmentation/local-network-segmentation.md)

3. **Proxmox Hypervisor Deployment & Hardening** <br>
Linux, Proxmox, SSH, virtualization, SMTP <br>
→ [proxmox-deployment](labs/proxmox-deployment/proxmox-deployment.md)

3. **Ubuntu Server Deployment & Hardening** <br>
Linux, Proxmox, Ubuntu, SSH, virtualization, fail2ban, unattended-upgrades, ufw <br>
→ [ubuntu-server-deployment](labs/ubuntu-server-deployment/ubuntu-server-deployment.md)



## Architecture Diagram

**IN PROGRESS:** Production Proxmox server deployment and hardening

![Network Diagram](network-diagram.png)

**Note:** This is not all configured as of yet and is subject to change as the lab develops



## Objectives

- Design and operate a segmented enterprise style network
- Build a secure virtualized lab environment
- Implement layered security controls across the entire network
- Develop hands on blue and red team cybersecurity skills
- Document and automate lab infrastructure
- Enable controlled offensive security testing

<details>
<summary><strong>Technology Stack</strong></summary>

- OPNsense 25.7.10
- Netgear 24 port managed switch (GS728TPV2)
- TP-Link 8 port managed switch (TL-SG108E 6.0)
- Unifi Network Server (10.0.156)
- Unifi Access Point (AP AC Pro)
- Proxmox VE (9.1.4)
- Unbound Recursive DNS
- WireGuard VPN (network level)
- ISC DHCPv4
- Packet capture
- Traceroute
- Firewall logs

</details>



## Roadmap

[X] OPNsense firewall deployment <br>
[X] VLAN based network segmentation <br>
[X] Production Proxmox server deployment & hardening<br>
[X] Ubuntu server (VM) deployment & hardening <br>
[X] Install Unifi Network Controller and import configuration <br> 
[X] Deploy a Docker host VM <br>
[...] Deploy Wazuh XDR & SIEM <br>
[...] Configure Suricata IDS/IPS <br>
[...] Deploy Nessus vulnerability scanner <br>
[...] Create virtualized Active Directory network <br>



## About Me

This lab is part of a broader GitHub portfolio. For an overview of my background and other projects, see my [GitHub Profile](https://github.com/ncbarrett90)
