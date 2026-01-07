# Procedure: Virus Cleanup (Windows Endpoint)

## Overview

This procedure outlines a best-effort remediation process for suspected malware infections on Windows systems, including browser-based threats, adware, and common malware indicators.

## Scope

**Included:**
- Pre-remediation steps
- Application audit
- Process & service audit
- Browser audit
- Antivirus and malware scans
- System integrity check
- System hardening

**Excluded:**
- Full file system audit (time intensive without the guarantee to improve outcome)
- Registry audit (high risk of system instability)
- Operating system reload (covered under separate procedure)

## Requirements & Prerequisites

- The client has acknowledged and accepted the risks associated with malware remediation versus a full operating system reload
- Administrative access to the system is available
- End user behavior may have contributed to the infection and is outside the scope of this procedure


## Tools & Technologies

- Antivirus/malware (Examples):  Malwarebytes, adwcleaner, HitManPro, RogueKiller, Windows Defender
- Offline recovery environments: Hirens Boot CD
- System utilities: Process Explorer, Task Manager, Control Panel

## Procedure Steps

**Important:** Do not connect the device to the internet prior to running offline scans and performing an audit of services, applications and the browser. This reduces the risk of malware communicating externally or spreading laterally.

### 1. Pre-remediation Steps

- Document the incident as much as possible
- Collect local computer and Microsoft credentials
- Determine what browser the owner uses on the system
- Discuss the risks with cleaning a system vs reloading the operating system
- Confirm symptoms reported (pop-ups, redirects, performance, credential compromise, etc.)

**Note:** During the audit phase, document everything that was found/removed from the system. When in doubt, document and research rather than immediately uninstall critical software.

### 2. Application Audit

- Check all applications to ensure only legitimate software is on the system
	- Settings and Control Panel
	- Sort installed programs by date

### 3. Process & Service Audit

- Check all processes and services running in task manager and remove anything known to be malicious
	- Task manager search online feature is very useful for looking into these
	- Process Explorer w/ virus total enabled is highly useful for looking deeper into processes
- Review startup items (Startup tab, autoruns if available)

### 4. Browser Audit

- Check extensions and clear up anything suspicious
- Clear site permissions for anything suspicious
	- Notifications
	- Pop-ups
	- Automatic downloads
	- locations/camera/microphone
- Check default search engines and address bar behavior to combat hijacks
- Configure homepage and "where you left off" settings to combat reoccurrence 

### 5. Antivirus/malware scans

**Run the following in order:**
- adwcleaner to remove adware, bloatware, browser hijackings and more
- HitManPro to scan for malware, remove manually (free version limitation)
- RogueKiller to scan for and remove viruses, rootkits and other malware
- MalwareBytes as an additional malware scan and removal tool
- Windows Defender to scan and verify that the system is clean

### 6. System Integrity Check

- Clean %temp% and C:\Windows\Temp
- Check for newly created accounts
- Run online Windows Defender scan
- Apply the latest firmware and operating system updates
- Run DISM to ensure drive image integrity
- Run SFC to check the filesystem for any corruption and repair
- Check task scheduler for recently added tasks

### 7. System Hardening

- Remove additional browsers that are not the main one used
- Add ublock origin to the default browser
- Ensure Windows Defender features are fully enabled
- Change DNS servers to 1.1.1.1 and 1.1.1.2 for malware and tracking prevention through Cloudflare
- Provide basic guidance to the user on avoiding similar infections

## Security Considerations

- Connecting infected computers to a network puts the network and other devices at risk, these devices should be connected to the internet in an isolated manner.
- It is always a better idea to wipe the device clean and start fresh vs trying to clean a system that has been infected with a virus. It cannot be guaranteed that a system is fully clear after this process.
- Assume credentials used on the system during infection may be compromised and should be changed from a known-clean device.

### Version:

- Document version: 1.0
- Last updated: 2025-01-04