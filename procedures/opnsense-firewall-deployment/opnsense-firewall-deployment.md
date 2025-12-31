# OPNsense Firewall Deployment

This procedure outlines the baseline deployment and configuration of OPNsense to improve network security in a production inspired home environment.

## Scope

- Included:
	- Initial installation
	- Interface assignment/configuration
	- DHCP/DNS configuration
	- Administrative access configuration
	- System hardening

- Excluded:
	- VPN configuration
	- IDS/IPS setup
	- Detailed DNS setup
	- High availability

## Tools & Technologies

- OPNsense 25.7.10
- FreeBSD 14.3
- Web UI
- Unbound DNS
- VLAN capable switch (if segmenting management interfaces)
- Access point for wireless network

## Architecture & Design Notes 

### Network Design Overview

| Interface | Purpose | Notes | 
| -------------- | ------------- | --------- |
| WAN | Internet/Upstream | Public IP from ISP |
| MGMT | Core trusted network | Management access | 
| HOME | Trusted network | Endpoint internet/service access | 
| GUEST | Untrusted network | Endpoint internet access only | 

**Design Rationale:**
- Default deny posture between VLAN segments
- Rule based access 
- Clear zone separation for core, trusted, and untrusted devices

## Procedure Steps

### 1. Initial Installation

- Install OPNsense using ISO
- Assign physical interfaces during command line setup
- Access the web interface

### 2. Interface Configuration

- Create VLANs and assign them to interfaces
- For each interface:
	- Enable the interface
	- Prevent interface removal
	- Name (using "Description" field)
	- Configure with static IP (use VLAN tag as part of the network address)

### 3. DHCP Server

- Interfaces requiring auto IP addressing:
	- Enable DHCP server and setup a reservation range
	- Configure static IP addresses within DHCP server for devices the require one

### 4. DNS Server

- Enable Unbound
- Enable DNSSEC support
- Enable flush DNS cache on restart
- Create a blocklist using Steven Black List
- Ensure that the default DNS server is the OPNsense MGMT IP address
- Disable the WAN DNS override via DHCP (system > settings > general)

### 5. Administrative Access 

- Change the root user password (random 20 char.)
- Create secondary user and assign to admins group
- Disable the root user
- Disable SSH

### 6. System Hardening

- Apply latest updates
- Set up email notification when updates are released (avoiding automatic updates on a router)
- Automate configuration backups

### 7. Firewall Rules

**MGMT**
- Allow -> Internet

**HOME**
- Allow -> Internet
- Allow (explicit) -> Services on MGMT

**GUEST**
- Allow -> internet
- Client isolation

**WAN**
- Block all inbound

**Inter VLAN**
- Default deny between VLANs
- Explicit allow rules based on services/need

## Security Considerations

- Management interfaces are restricted to trusted and isolated networks
- Default deny policy enforced between zones
- Logging enabled for audit and troubleshooting
- Access is tightly controlled
- Automated backup and update notification process