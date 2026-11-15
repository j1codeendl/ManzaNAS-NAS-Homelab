# ManzaNAS Configuration

## 1. System Information

| Configuration | Details |
|---|---|
| Hostname | ManzaNAS |
| Operating System | Debian Linux + OpenMediaVault |
| Processor | Intel Celeron N4000 |
| CPU Cores | 2 |
| Memory | 4 GB RAM |
| Storage | 500 GB HDD |
| Network | Ethernet (`eno1`) / Wi-Fi (`wlo1`) |
| Network Environment | Local Area Network |

## 2. Storage Configuration

- **Storage device:** 500 GB HDD
- **Shared folder:** `ManzaNAS_Files`
- **Filesystem:** ext4 / BTRFS (Refer to actual OMV filesystem)

## 3. Network Configuration

The NAS is connected to the local network via Wi-Fi and provides file-sharing services to client devices.

- **Hostname:** ManzaNAS
- **Active Connection:** Wi-Fi (`wlo1`)
- **IP Configuration:** Static IP
- **IPv4 Address:** `192.168.1.14`
- **IPv4 Netmask:** `255.255.255.0`
- **IPv4 Gateway:** `192.168.1.1`
- **DNS Servers:** `8.8.8.8`
- **IPv6 Method:** Disabled (to prevent routing conflicts)
- **SMB Service:** Enabled

## 4. File Sharing Configuration

| Item | Configuration |
|---|---|
| Service | SMB/CIFS |
| Shared Folder | `ManzaNAS_Files` |
| Access Method | Network file sharing |
| Windows Client | Windows 11 |
| Android Client | CX File Explorer |

## 5. User and Access Management

Separate user accounts were configured to manage access and separate OS operations from file sharing.

- **`root`**: Used strictly for emergency system administration in the terminal.
- **`lj814`**: The foundational Debian OS user. Retains hardware groups (`audio, bluetooth, cdrom, netdev, plugdev, video`) for physical access.
- **`manza`**: Dedicated standard user created within OMV exclusively for SMB folder access.

## 6. Power Management and Uptime Optimization

Because the NAS runs on laptop hardware, default sleep states were disabled via the CLI to prevent the network from dropping when the lid is closed or the system is idle.

**Command applied to disable sleep states:**
`sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target`

## 7. Security and Operational Notes

- Separate user accounts are used for access management.
- The NAS is meant to run continuously; soft reboots (`reboot`) should be avoided due to hardware quirks. Full Cold Boots (`poweroff`) are required.
- NAS administration is intended for the local network.
- Remote access is not currently implemented.

## 8. Backup and Recovery

An automated backup strategy has not yet been implemented. The current deployment should not be treated as a secure backup solution for critical data until redundancy is established.
