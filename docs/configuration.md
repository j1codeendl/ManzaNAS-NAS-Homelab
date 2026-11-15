# ManzaNAS Configuration

## 1. System Information

| Configuration | Details |
|---|---|
| Hostname | ManzaNAS |
| Operating System | OpenMediaVault |
| Processor | Intel Celeron N4000 |
| CPU Cores | 2 |
| Memory | 4 GB RAM |
| Storage | 500 GB HDD |
| Network | Ethernet / Wi-Fi |
| Network Environment | Local Area Network |

## 2. Storage Configuration

- Storage device: 500 GB HDD
- Shared folder: ManzaNAS_LJ
- Filesystem: Refer to the actual configured filesystem in OpenMediaVault.

## 3. Network Configuration

The NAS is connected to the local network and provides file-sharing services to client devices.

- Hostname: ManzaNAS
- Connection type: [Specify actual active connection]
- IP configuration: [DHCP or static, verify before completing]
- SMB service: Enabled

The private LAN IP address is intentionally omitted from this public documentation.

## 4. File Sharing Configuration

| Item | Configuration |
|---|---|
| Service | SMB/CIFS |
| Shared Folder | ManzaNAS_LJ |
| Access Method | Network file sharing |
| Windows Client | Windows 11 |
| Android Client | CX File Explorer |

## 5. User and Access Management

Separate user accounts were configured to manage access to shared storage.

Access permissions were assigned according to the intended use of each account.

Verify actual folder permissions before publishing screenshots.

## 6. Client Devices

### Windows 11
Used File Explorer to access the NAS shared folder over the local network.

### Android
Used CX File Explorer to connect to the NAS through SMB.

## 7. Security and Operational Notes

- Separate user accounts are used for access management.
- Credentials should not be stored in public documentation.
- NAS administration is intended for the local network.
- Remote access is not currently implemented.

## 8. Backup and Recovery

An automated backup strategy has not yet been implemented.

The current deployment should not be treated as a backup solution for important files until a separate backup and recovery process is established.
