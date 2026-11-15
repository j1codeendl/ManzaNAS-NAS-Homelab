# ManzaNAS Setup Guide

## 1. Overview

This guide documents the installation and initial configuration of a
Network Attached Storage (NAS) system using **Debian Linux** and
**OpenMediaVault (OMV)** on repurposed laptop hardware.

The project demonstrates how an older computer can be repurposed into a
centralized file storage system accessible through a local network.

### Project Configuration

| Component | Specification |
|---|---|
| Operating System | Debian Linux 13 |
| NAS Platform | OpenMediaVault 8 |
| Hardware | Repurposed laptop |
| Processor | Intel Celeron N4000 |
| Memory | 4 GB RAM |
| Internal Storage | 500 GB HDD |
| Network | Ethernet / Wi-Fi |
| File Sharing Protocol | SMB/CIFS |
| Data Storage | External USB storage |
| Filesystem | EXT4 |
| Client Devices | Windows 11 PC and Android |

### Project Features

-   Centralized file storage
-   SMB-based network file sharing
-   Separate user accounts
-   Shared folder permissions
-   Access from Windows and Android devices
-   Web-based NAS administration

------------------------------------------------------------------------

## 2. Prerequisites

### Hardware Requirements

-   Repurposed laptop or desktop computer
-   Internal storage device for the operating system
-   External USB storage device for shared files
-   Ethernet connection (recommended)
-   Another computer for accessing the NAS

### Software Requirements

-   Debian 13 installation ISO
-   Bootable USB installer
-   Internet connection
-   OpenMediaVault installation script

### Important Preparation

Before installation:

1.  Back up important files from the target computer.
2.  Prepare a bootable USB installer containing Debian 13.
3.  Connect the computer to the network using Ethernet.
4.  Connect the external USB storage device intended for NAS data.

**Storage configuration:** The internal HDD is used for Debian and
OpenMediaVault. The external USB storage device is used for shared
files. Do not format the internal system drive during the shared-storage
configuration process.

------------------------------------------------------------------------

## 3. Debian Installation

### 3.1 Boot from the Installation USB

1.  Insert the bootable Debian USB installer.
2.  Restart the computer.
3.  Open the BIOS/UEFI boot menu.
4.  Select the USB installation device.
5.  Proceed with the Debian installation.

### 3.2 Install Debian

During installation:

1.  Select the appropriate language and regional settings.
2.  Configure the keyboard layout.
3.  Connect to the network using Ethernet.
4.  Configure the hostname.
5.  Create the required administrative account.
6.  Select the internal HDD as the operating system installation target.
7.  Configure disk partitions according to the installation
    requirements.
8.  Complete the installation.

For a minimal NAS installation, avoid installing unnecessary desktop
environments or additional packages.

### 3.3 Complete Initial Setup

After installation:

1.  Remove the installation USB.
2.  Restart the computer.
3.  Log in using the configured administrative account.
4.  Verify network connectivity.
5.  Update the Debian package lists and installed packages.

``` bash
sudo apt update
sudo apt upgrade -y
```

------------------------------------------------------------------------

## 4. OpenMediaVault Installation

OpenMediaVault provides a web-based management interface for configuring
storage, users, network services, and file sharing.

### 4.1 Install Required Packages

``` bash
sudo apt install curl wget sudo -y
```

### 4.2 Download and Execute the Installation Script

Download the official OpenMediaVault installation script:

``` bash
wget -O install-openmediavault.sh https://github.com/OpenMediaVault-Plugin-Developers/installScript/raw/master/install
```

Execute the installer:

``` bash
sudo bash install-openmediavault.sh
```

Allow the installation process to complete. The installation may take
several minutes and can automatically restart the system.

### 4.3 Access the Web Administration Interface

After the installation and restart:

1.  Identify the NAS computer's assigned IP address.
2.  Open a web browser on another device connected to the same network.
3.  Enter the NAS IP address in the browser's address bar.

``` text
http://<NAS-IP-ADDRESS>
```

4.  Log in using the initial OpenMediaVault administrator credentials.
5.  Change the default administrator password after the first login.

Keep operating-system accounts and OpenMediaVault web administrator
accounts separate.

------------------------------------------------------------------------

## 5. Network Configuration

A stable network connection is necessary for reliable NAS access.

### 5.1 Ethernet Configuration

Ethernet is recommended for the primary NAS connection because it
provides a more stable connection for file transfers.

In OpenMediaVault:

1.  Navigate to **Network \> Interfaces**.
2.  Locate the active Ethernet interface.
3.  Review its current network configuration.
4.  Configure the addressing method according to the local network
    requirements.

A DHCP reservation on the router is recommended to keep the NAS
accessible at a consistent address.

### 5.2 Wi-Fi Configuration

Wi-Fi can be used when Ethernet is unavailable.

On Debian, identify the wireless interface:

``` bash
ip link
```

Verify the available network interfaces and wireless connection status
before configuring wireless networking.

For this deployment, Ethernet is the preferred connection.

### 5.3 Verify Network Connectivity

``` bash
ip addr
```

Check the network connection:

``` bash
ping -c 4 8.8.8.8
```

------------------------------------------------------------------------

## 6. Storage Configuration

OpenMediaVault uses storage management tools to prepare disks and
organize shared data.

### 6.1 Identify the Storage Device

Navigate to **Storage \> Disks**.

Identify the external USB storage device intended for shared files.

Verify the device model, capacity, and mount status before making
changes.

### 6.2 Create a Filesystem

1.  Navigate to **Storage \> File Systems**.
2.  Select the external USB storage device.
3.  Create an EXT4 filesystem if the device does not already have one.
4.  Apply the changes.
5.  Mount the filesystem.

Formatting erases existing data on the selected device. Ensure the
correct disk is selected before proceeding.

### 6.3 Create a Shared Folder

1.  Navigate to **Storage \> Shared Folders**.
2.  Select **Create**.
3.  Enter a shared folder name, for example:

``` text
ManzaNAS_Files
```

4.  Select the mounted external filesystem.
5.  Configure the folder permissions.
6.  Save and apply the changes.

------------------------------------------------------------------------

## 7. SMB/CIFS Configuration

SMB (Server Message Block) enables file sharing between the NAS and
other devices on the local network.

### 7.1 Enable SMB/CIFS

1.  Navigate to **Services \> SMB/CIFS \> Settings**.
2.  Enable the SMB/CIFS service.
3.  Configure the workgroup according to the network environment.
4.  Save and apply the configuration.

### 7.2 Create an SMB Share

1.  Navigate to **Services \> SMB/CIFS \> Shares**.
2.  Select **Create**.
3.  Choose the previously created shared folder.
4.  Configure the share settings.
5.  Enable the share.
6.  Save and apply the changes.

The shared folder should now be available to authorized devices on the
local network.

------------------------------------------------------------------------

## 8. User and Permission Management

Separate user accounts help control access to shared files.

### 8.1 Create a User Account

1.  Navigate to **Users \> Users**.
2.  Select **Create**.
3.  Enter a username.
4.  Set a strong password.
5.  Save the account.

Use a dedicated SMB user account instead of sharing the operating-system
root or administrative account.

### 8.2 Configure Shared Folder Permissions

1.  Navigate to **Storage \> Shared Folders**.
2.  Select the shared folder.
3.  Open its permissions or access control settings.
4.  Assign the appropriate read and write permissions to the intended
    users.
5.  Save and apply the changes.

### 8.3 Verify Access

Test the account by connecting from a client device.

Confirm that:

-   Authorized users can access the shared folder.
-   Users with write permissions can create and modify files.
-   Users without the required permissions cannot access restricted
    content.

------------------------------------------------------------------------

## 9. Client Device Access

The NAS can be accessed by devices connected to the same local network.

### 9.1 Windows 11

1.  Connect the Windows computer to the same network as the NAS.
2.  Open File Explorer.
3.  Enter the following address in the navigation bar:

``` text
\\<NAS-IP-ADDRESS>
```

4.  Locate the configured SMB shared folder.
5.  Enter the SMB username and password when prompted.
6.  Verify access by creating or opening a test file.

The shared folder can also be mapped as a network drive through File
Explorer.

### 9.2 Android

An SMB-compatible file manager can be used to access the NAS from an
Android device.

Example application: **CX File Explorer**

1.  Connect the Android device to the same local network.
2.  Open CX File Explorer.
3.  Navigate to the Network section.
4.  Select the option to add a network location or SMB connection.
5.  Enter the NAS IP address.
6.  Provide the SMB username and password.
7.  Connect to the shared folder.

Verify that files can be viewed, downloaded, and uploaded according to
the configured permissions.

------------------------------------------------------------------------

## 10. Verification and Testing

After completing the configuration, perform the following checks.

| Test | Expected Result |
| :--- | :--- |
| OpenMediaVault dashboard | Accessible through a web browser |
| Network connectivity | NAS reachable on the local network |
| Storage detection | External storage recognized |
| Filesystem | EXT4 mounted successfully |
| Shared folder | Available through SMB |
| User authentication | Valid credentials accepted |
| Windows access | Shared files accessible |
| Android access | Shared files accessible |
| File operations | Authorized upload and download successful |
| Restart behavior | Services and storage return after reboot |

## 11. Current Limitations

The implementation may have the following limitations, depending on the
deployment:

-   Access is restricted to the local network unless secure remote
    access is configured.
-   Automated backup may not be configured.
-   Performance is limited by the server hardware.
-   Storage capacity depends on the connected storage device.
-   Wi-Fi performance may vary depending on network conditions.

This implementation is intended for learning, experimentation, and basic
centralized file sharing rather than production-critical storage.

---

**Project Name:** ManzaNAS  
**Project Type:** Personal IT HomeLab  
**Purpose:** Hands-on learning in system administration, networking, and IT infrastructure.
