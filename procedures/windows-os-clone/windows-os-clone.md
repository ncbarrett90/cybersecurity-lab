# Procedure: Windows Operating System Cloning

## Overview

This procedure describes how to clone an existing Windows 10/11 operating system from a source drive to a target drive. This process is typically used for hardware upgrades, drive replacement, disaster recovery, or as part of an upgrade from Windows 10 to Windows 11, while preserving the existing OS configuration.

## Scope

**Included:**
- Pre-cloning preparation
- Disk imaging of the source system
- Image deployment to the target drive
- Post image cleanup
- System hardening & integrity checks
- Final validation

**Excluded:**
- Application reconfiguration or licensing issues
- Advanced storage configurations (e.g. RAID, dual-boot systems, Optane)
- Data recovery from failing or corrupted drives

## Requirements & Prerequisites

**The system owner must provide:**
- Local or domain Windows credentials
- Microsoft account credentials associated with the system
- BitLocker recovery key ( if disk encryption is enabled)

**Technician responsibilities:**
- Verify BitLocker is suspended or decrypted prior to imaging
- Confirm a backup or the original machine is available before proceeding
- Label and document all components of the project

**Notes about the new system:**
- Target drive capacity must be equal to or greater than the used space on the source drive
- Best results are achieved when cloning to similar manufacturer hardware (e.g. Dell to Dell)

## Tools & Technologies

- Imaging tools (use one): NinaOne Restore, Macrium Reflect, Windows Backup and Restore
- Disk utilities: Diskpart, MBR2GPT
- Operating systems & environments: Windows 10/11, Windows Recovery Environment, Windows PE

## Procedure Steps

### 1. Pre-cloning preparation

**Collect system and user information:**
- Local or domain account credentials
- Microsoft account credentials
- BitLocker recovery key
- List of critical or licensed applications (e.g., paid antivirus)

**User communication:**
- Explain the cloning process and expected downtime
- Set expectations for post-clone login and verification

### 2. Disk imaging of the source system

**Important:** The source drive must not be modified during the imaging process.

- Identify all storage devices connected to the system
- Verify BitLocker is suspended or the drive is decrypted
- Create a full disk image of the OS drive to external storage
- Confirm the image completes successfully and passes integrity verification
- Document image location and filename

### 3. Image deployment to the target drive

- Deploy the image to the target drive
- Check if the disk is GPT using diskpart
- If the disk is MBR, convert using mbt2gpt
- Ensure Boot mode is UEFI
- Ensure secure boot is enabled
- Boot into Windows to confirm successful startup

### 4. Post imaging cleanup

- Remove manufacturer-specific software from the target system
- Install appropriate drivers and utilities for the target hardware
- Review Device Manager and remove orphaned or conflicting devices
- Confirm no unknown devices remain

### 5. System hardening & integrity checks

- Update system firmware
- Apply all Windows updates
- Confirm Windows Defender is enabled and up to date
	- Run quick scan
- Run system integrity checks (Administrator PowerShell or Command Prompt)
	- DISM 
	- SFC
- Reboot and confirm system stability 

### 6. Final validation

**Hardware functionality:**
- Trackpad / mouse
- Keyboard
- Camera
- Microphone
- Speakers
- Wireless networking
- Ethernet
	
**System integrity:**
- Firmware up to date
- OS fully updated
- DISM and SFC completed without errors

**Operating system settings:**
- Correct time zone
- Device manager shows no errors
- Network settings cleared
	
**Physical device:**	
- Clean device exterior
- Verify all screws and panels are secure
- Clean and organize workspace

## Rollback & Failure Handling

- The original source drive must remain unchanged.
- If any step in the imaging, deployment, or validation process fails, determine why before attempted another clone.

**Common failure scenarios and actions:**
- Imaging failure: Verify storage space, BitLocker status, and tool selection, then reattempt imaging.
- Boot failure after deployment: Verify UEFI boot mode and disk configuration.
- Driver or hardware issues: Install correct drivers for the target hardware.
- User access issues: Microsoft account credentials may be required due to TPM changes.
- If repeated failures occur or data integrity cannot be confirmed, stop work and escalate.

## Security Considerations

- All system images must be deleted once the cloning process is complete and validation is successful.
- External drives used for imaging must be securely wiped at least every three months to prevent data recovery.
- TPM changes may clear Windows Hello PINs; Microsoft account credentials are required for post-clone access.

### Version:

- Document version: 1.0
- Last updated: 2026-01-03