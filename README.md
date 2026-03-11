# Cybersecurity Lab

A hands on lab focused on cybersecurity, enterprise style network design, and IT best practices.



## Lab Overview

This lab simulates a small enterprise network with segmented security zones, firewalling, virtualized workloads, and layered defenses, enabling both blue-team (defensive) and red-team (offensive) cybersecurity practice. 



## Lab Modules

Documentation approach: Each module includes an overview, architecture details, key security configurations, challenges/validation and summarized implementation notes.

**Wazuh SIEM/EDR Detection Engineering** <br>
SIEM, EDR, threat detection, threat modeling, file integrity monitoring, Kali Linux, Sysmon, Active Directory <br>
→ [wazuh-detection-engineering](labs/wazuh-detection-engineering/wazuh-detection-engineering.md)

**Wazuh SIEM/Endpoint Detection & Response System Deployment** <br>
SIEM, vulnerability detection, file integrity monitoring, security operations, configuration assessment, threat hunting, Linux, Proxmox VE <br>
→ [wazuh-edr-implementation](labs/wazuh-edr-implementation/wazuh-edr-implementation.md)

**Proxmox Backup Server Deployment** <br>
Linux, Proxmox Backup Server, Open Media Vault, stateless API authentication, Proxmox VE, NAS, disaster recovery, ZFS RAID <br>
→ [backup-server-deployment](labs/backup-server-deployment/backup-server-deployment.md)

**Active Directory Environment Build** <br>
Active Directory, Domain Controller, Windows Server, Windows 10/11 <br>
→ [active-directory-environment](labs/active-directory-environment/active-directory-environment.md)

**Ubuntu Server Deployment & Hardening** <br>
Linux, Proxmox, Ubuntu, SSH, virtualization, fail2ban, unattended-upgrades, ufw <br>
→ [ubuntu-server-deployment](labs/ubuntu-server-deployment/ubuntu-server-deployment.md)

**Proxmox Hypervisor Deployment & Hardening** <br>
Linux, Proxmox, SSH, virtualization, SMTP <br>
→ [proxmox-deployment](labs/proxmox-deployment/proxmox-deployment.md)

**Local Network Segmentation w/ VLANs** <br>
Network security zones, switch & WAP configuration, firewall rules, 802.1Q VLAN trunking, wireless & Ethernet networking <br>
→ [local-network-segmentation](labs/local-network-segmentation/local-network-segmentation.md)

**OPNsense Firewall Deployment & Baseline Hardening** <br>
Firewall installation, interface configuration, NAT, DNS, DHCP, logging, VPN, device hardening <br>
→ [opnsense-deployment](labs/opnsense-deployment/opnsense-deployment.md)

## Architecture Diagram

**IN PROGRESS:** Wazuh endpoint detection and response implementation for the Active Directory subnet

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
- Wazuh 
- Proxmox Backup Server
- Open Media Vault
- Kali Linux
- Ubuntu server/desktop

</details>



## Roadmap

<details>
<summary><strong>Completed (full list)</strong></summary>

[X] OPNsense firewall deployment <br>
[X] VLAN based network segmentation <br>
[X] Production Proxmox server deployment & hardening<br>
[X] Ubuntu server (VM) deployment & hardening <br>
[X] Install Unifi Network Controller and import configuration <br> 
[X] Deploy a Docker host VM <br>

</details>

[X] Create virtualized Active Directory network <br>
[X] Implement automated backups to a centralized server for all VMs <br>
[X] Deploy Wazuh XDR & SIEM <br>
[X] Configure file integrity monitoring using EDR <br>
[X] Engineer threat detection rules for simulated attack <br>
[...] Simulate more complex attacks and detect using EDR/SIEM <br>
[...] Deploy Splunk server <br>
[...] Integrate Wazuh EDR (and other tools) w/ Splunk <br>
[...] Configure Suricata IDS/IPS <br>
[...] Deploy Nessus vulnerability scanner <br>



## About Me

This lab is part of a broader GitHub portfolio. For an overview of my background and other projects, see my [GitHub Profile](https://github.com/ncbarrett90)
