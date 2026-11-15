
# ManzaNAS Configuration

## 1. System Information

| Configuration | Details |
|---|---|
| Hostname | `ManzaNAS` |
| Operating System | Debian Linux + OpenMediaVault |
| Processor | Intel Celeron N4000 @ 1.10 GHz |
| CPU Cores | 2 |
| Memory | 4 GB RAM |
| Internal Storage | 500 GB HDD |
| Network Interfaces | Ethernet (`eno1`) / Wi-Fi (`wlo1`) |
| Network Environment | Local Area Network |

## 2. Storage Configuration

| Configuration | Details |
|---|---|
| Internal Storage Device | 500 GB HDD (Operating System) |
| External Storage Device | 28.5 GB USB Flash Drive (Data Storage)|
| Shared Folder | `ManzaNAS_Files` |
| Filesystem | EXT4 |
| File Sharing Protocol | SMB/CIFS |

- Shared folders are managed through the OpenMediaVault web interface.
- Storage access is controlled through user permissions.

## 3. Network Configuration

| Configuration | Details |
|---|---|
| Hostname | `ManzaNAS` |
| Active Connection | Wi-Fi (`wlo1`) |
| IP Configuration | Static IP |
| IPv4 Address | `192.168.x.x` |
| IPv4 Netmask | `255.255.255.0` |
| IPv4 Gateway | `192.168.1.1` |
| DNS Server | `8.8.8.8` |
| IPv6 | Disabled |
| SMB Service | Enabled |

### Network Notes

- The NAS uses a static IPv4 address for consistent local network access.
- IPv6 is disabled in the current configuration.
- Ethernet (`eno1`) is available as an alternative network interface.

## 4. File Sharing Configuration

| Configuration | Details |
|---|---|
| Service | SMB/CIFS |
| Shared Folder | `ManzaNAS_Files` |
| Access Method | Network File Sharing |
| Windows Client | Windows 11 |
| Android Client | CX File Explorer |
| Network Scope | Local Area Network |

SMB allows authorized devices to access shared files over the local network.

## 5. User and Access Management

| Account | Purpose |
|---|---|
| ` ` | System-level administration and recovery |
| ` ` | Debian operating system user with assigned hardware-related group memberships |
| ` ` | Dedicated OpenMediaVault user for SMB shared-folder access |

### Account Management Notes

- The ` ` account is reserved for privileged system operations.
- The ` ` account has the following hardware-related group memberships: `audio`, `bluetooth`, `cdrom`, `netdev`, `plugdev`, and `video`.
- The ` ` account is used for regular SMB authentication.
- File access is controlled through OpenMediaVault shared-folder permissions and SMB configuration.

## 6. Power Management

Laptop power-management settings were adjusted to prevent automatic suspension or hibernation during NAS operation.

The following command was executed to disable the corresponding systemd targets:

```bash
sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target
```

This configuration helps maintain NAS availability when the laptop is idle.

## 7. Security and Operational Notes

- Separate system and file-sharing accounts are maintained.
- SMB access requires valid user credentials.
- Shared-folder permissions control authorized file access.
- NAS administration is intended for the local network.
- Remote access is not currently configured.
- Automated backups are not yet implemented.

### Power and Restart Considerations

The current deployment has reported hardware-related restart quirks. Full shutdown and cold boot procedures are used when necessary instead of relying on routine soft reboots.

## 8. Backup and Recovery

An automated backup strategy has not yet been implemented.

The current deployment provides centralized file storage but should not be considered a complete backup solution for critical data.

Potential future improvements include:

- Automated scheduled backups.
- External backup storage.
- Periodic backup verification.
- Recovery testing.
- Storage redundancy where supported by the available hardware.

## 9. Configuration Summary

| Category | Current Status |
|---|---|
| Debian Linux | Installed |
| OpenMediaVault | Installed |
| Static IPv4 Configuration | Configured |
| Wi-Fi Connectivity | Configured |
| SMB/CIFS | Enabled |
| Shared Folder | Configured |
| Separate User Accounts | Configured |
| Windows 11 Access | Supported |
| Android Access | Supported |
| Remote Access | Not configured |
| Automated Backup | Not implemented |

---

**Project Name:** ManzaNAS  
**Project Type:** Personal IT HomeLab  
**Purpose:** Hands-on learning in system administration, networking, and IT infrastructure.
