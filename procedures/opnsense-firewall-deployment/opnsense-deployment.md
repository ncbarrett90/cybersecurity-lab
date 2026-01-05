# OPNsense Deployment

This procedure outlines the essential steps for deploying and configuring OPNsense in a production inspired home environment to ensure robust network security and reliable operation.

## Scope

**Included:**
- Initial installation
- Interface assignment/configuration
- DHCP/DNS configuration
- Administrative access configuration
- System hardening

**Excluded:**
- VPN configuration
- VLAN configuration
- IDS/IPS setup
- Detailed DNS setup	
- High availability

**These topics will be covered in later documentation.**

## Tools & Technologies

- OPNsense
- FreeBSD
- Web UI
- Unbound DNS

## Architecture & Design Notes 

### Network Design Overview

| Interface | Purpose | Notes | 
| -------------- | ------------- | --------- |
| WAN | Internet/upstream | Public IP from ISP |
| LAN | Trusted network | Internal network | 

**Note:** Consider creating VLANs for additional segmentation of traffic based on device type or function (e.g., Guest, IoT, Management). These configurations are not covered in this procedure but should be part of a segmented network design where applicable.

## Procedure Steps

### 1. Initial Installation

- Install OPNsense using ISO
- Assign physical interfaces during command line setup
	- WAN: Internet connection
	- LAN: Internal network
- Access the web interface
	- Default IP: 192.168.1.1

### 2. Interface Configuration

- Create VLANs and assign them to virtual interfaces
- For each interface:
	- Enable the interface
	- Prevent interface removal
	- Name (using "Description" field)
	- Configure with unique static IP address (use VLAN tag as part of the network address)

### 3. DHCP Server

- Interfaces requiring auto IP addressing:
	- Enable DHCP server and setup a reservation range (generally set from .100 to .199)
	- Configure static IP addresses within DHCP server (ensure static IP addresses are outside the DHCP range to avoid conflicts)

### 4. DNS Server

- Enable Unbound DNS
- Enable DNSSEC support
- Enable flush DNS cache on restart: clears stale DNS entries
- Create a blocklist using Steven Black List (Community blocklist of malicious domains)
- Ensure that the default DNS server is the OPNsense LAN IP address
- Disable the WAN DNS override via DHCP (system > settings > general)
	- Ensures that upstream DNS servers will not take effect

### 5. Administrative Access 

- Generate a random 20 character password for the root user
- Create secondary user and assign to admins group
- Disable the root user
- Disable SSH
	- Disabling both the root user login and SSH greatly reduces the attack surface of the machine. If SSH is required, it should be heavily monitored.

### 6. System Hardening

- Apply latest updates
- Set up email notification for both system updates and critical alerts so administrators are kept informed about what is going on with the system
- Automate configuration backups to GitHub

### 7. Firewall Rules

**LAN**
- Allow -> Internet

**WAN**
- Block all inbound

**Inter VLAN (if applicable)**
- Default deny between VLANs
- Explicit allow rules based on services/need

## Security Considerations

- Management interfaces are restricted to trusted and isolated networks
- Default deny policy enforced between zones
- Logging enabled for audit and troubleshooting
	- Add to this procedure to include how this integrates with a central log management solution such as Splunk or Wazuh.
- Access is tightly controlled
- Automated backup and update notification process

### Version:

- Document version: 1.1
- Last updated: 2026-01-04