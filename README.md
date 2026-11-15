# ManzaNAS — OpenMediaVault NAS HomeLab

A personal Network Attached Storage (NAS) HomeLab built using OpenMediaVault on repurposed laptop hardware.

This project explores basic server administration, network file sharing, user access management, and cross-device file access within a local network.

## 1. Project Overview

ManzaNAS is a self-hosted NAS built using an old laptop running OpenMediaVault (OMV).

The goal was to repurpose available hardware into a centralized file-sharing system that allows multiple devices to access shared files through the local network.

The project was developed as a hands-on learning experience in IT infrastructure, system administration, and networking.

## 2. Project Objectives

- Deploy OpenMediaVault on repurposed laptop hardware.
- Configure network-based file sharing using SMB/CIFS.
- Create shared folders and manage user permissions.
- Connect Windows and Android devices to the NAS.
- Practice basic server configuration and troubleshooting.
- Document the implementation and network architecture.

## 3. Hardware Specifications

| Component | Specification |
|---|---|
| Server | Repurposed laptop |
| CPU | Intel Celeron N4000 @ 1.10 GHz |
| CPU Cores | 2 |
| Memory | 4 GB RAM |
| Storage | 500 GB HDD |
| Hostname | ManzaNAS |

## 4. Technologies and Tools

- **Operating System:** OpenMediaVault
- **File Sharing Protocol:** SMB/CIFS
- **Networking:** TCP/IP and Local Area Network (LAN)
- **Windows Client:** Windows 11
- **Android Client:** CX File Explorer
- **Documentation:** GitHub and Markdown
- **Network Diagram:** diagrams.net (draw.io), if used

## 5. Implemented Features

- OpenMediaVault installation and configuration.
- SMB/CIFS network file sharing.
- Shared folder configuration.
- Separate user accounts and access permissions.
- File access from Windows 11 and Android devices.
- Network-based access to shared storage.

## 6. Network Architecture

The NAS operates within a local network and provides shared storage access to connected client devices.

![ManzaNAS Network Diagram](docs/network-diagram.png)

## 7. Screenshots

### OpenMediaVault Dashboard

![System Dashboard](screenshots/01-system-dashboard.png)

### System Information

![System Information](screenshots/02-system-information.png)

### Storage and Shared Folders

![Storage Filesystems](screenshots/03-storage-filesystems.png)

![Shared Folders](screenshots/04-shared-folders.png)

### SMB Configuration

![SMB Configuration](screenshots/05-smb-configuration.png)

### User and Permission Management

![User Management](screenshots/06-user-management.png)

![Folder Permissions](screenshots/07-folder-permissions.png)

### Client Access

**Windows 11**

![Windows Client Access](screenshots/08-windows-client-access.png)

**Android**

![Android Client Access](screenshots/09-android-client-access.png)

## 8. Documentation

- [Setup Guide](docs/setup-guide.md)
- [Configuration Details](docs/configuration.md)
- [Troubleshooting](docs/troubleshooting.md)

## 9. Project Limitations

The current implementation has the following limitations:

- Remote access is not implemented.
- Automated backup is not implemented.
- The system uses repurposed laptop hardware with a single HDD.
- Access is intended for the local network.

## 10. Learning Outcomes

Through this project, I gained hands-on experience with:

- Installing and configuring a Linux-based NAS operating system.
- Understanding SMB/CIFS network file sharing.
- Configuring shared folders and user permissions.
- Connecting and accessing network storage from different client devices.
- Basic server and network troubleshooting.
- Technical documentation and network diagram preparation.

## 11. Future Improvements

Potential improvements include:

- Implementing an automated backup strategy.
- Exploring secure remote access.
- Monitoring system resources and storage health.
- Exploring additional network services.

---

**Project Name:** ManzaNAS  
**Project Type:** Personal IT HomeLab  
**Purpose:** Hands-on learning in system administration, networking, and IT infrastructure.
