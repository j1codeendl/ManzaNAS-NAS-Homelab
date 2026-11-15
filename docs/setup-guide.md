# ManzaNAS Setup Guide

## 1. Overview

This guide documents the general deployment and initial setup of ManzaNAS using Debian Linux and OpenMediaVault on repurposed HP laptop hardware.

## 2. Prerequisites

### Hardware
- Repurposed HP laptop
- Intel Celeron N4000 processor
- 4 GB RAM
- 500 GB HDD
- Network connectivity (Ethernet for initial setup, Wi-Fi for deployment)

### Software and Tools
- Debian Linux ISO and OpenMediaVault installation script
- USB installation drive (flashed via balenaEtcher)
- Windows 11 client
- CX File Explorer on Android
- Web browser

## 3. Installation and Initial Configuration

1. Prepare a bootable USB installation drive with Debian Linux.
2. Boot the laptop using the installation media and follow the Debian installer.
3. Create the foundational OS user (`lj814`). This user will automatically inherit required hardware groups (audio, video, netdev, plugdev).
4. Boot into the Debian terminal, connect an Ethernet cable (`eno1`), and log in as `root`.
5. Install OpenMediaVault via the official script:
   `wget -O - https://github.com/OpenMediaVault-Plugin-Developers/installScript/raw/master/install | sudo bash`
6. Reboot and identify the assigned DHCP IP address by running `ip a`.
7. Access the OpenMediaVault web administration interface from a Windows browser.

## 4. Storage Configuration

1. Check that the 500 GB HDD is detected in the OMV interface.
2. Verify and format the filesystem.
3. Mount the filesystem through the OpenMediaVault interface.
4. Create the required shared folder named `ManzaNAS_LJ`.

## 5. User and Permission Configuration

1. Create a dedicated user account inside OMV (`manza`) for network file sharing.
2. Ensure the primary OS user (`lj814`) is left alone and used only for local physical terminal access.
3. Configure shared folder access permissions for `ManzaNAS_LJ`.
4. Assign Read/Write permissions to the `manza` account.

## 6. SMB File Sharing Configuration

1. Open the SMB/CIFS service settings in OMV.
2. Enable the SMB service.
3. Add the `ManzaNAS_LJ` shared folder to the SMB configuration.
4. Apply and save the configuration using the yellow pending changes banner.
5. Verify that the shared folder is accessible from client devices.

## 7. Client Connection

### Windows 11

1. Open File Explorer.
2. Navigate to the network location using the NAS address (e.g., `\\192.168.1.14\ManzaNAS_LJ`).
3. Enter the `manza` credentials when prompted.
4. Access the shared folder.

### Android

1. Open CX File Explorer.
2. Navigate to the Network or SMB section.
3. Add the NAS server address (`192.168.1.14`).
4. Enter the `manza` user credentials.
5. Open the shared folder.

## 8. Verification

- Confirm successful access from Windows 11.
- Confirm successful access from Android.
- Test file uploads and downloads.
- Verify the system boots headless on Wi-Fi without Ethernet.
