# ManzaNAS Setup Guide

## 1. Overview

This guide documents the general deployment and initial setup of ManzaNAS using OpenMediaVault on repurposed laptop hardware.

## 2. Prerequisites

### Hardware
- Repurposed laptop
- Intel Celeron N4000 processor
- 4 GB RAM
- 500 GB HDD
- Network connectivity

### Software and Tools
- OpenMediaVault installation media
- USB installation drive
- Windows 11 client
- CX File Explorer on Android
- Web browser

## 3. Installation and Initial Configuration

1. Prepare a bootable USB installation drive.
2. Boot the laptop using the installation media.
3. Install OpenMediaVault onto the target storage device.
4. Complete the initial system configuration.
5. Access the OpenMediaVault web administration interface.
6. Verify that the system and network are functioning correctly.

## 4. Storage Configuration

1. Check that the storage device is detected.
2. Verify the filesystem.
3. Mount the filesystem through the OpenMediaVault interface.
4. Create the required shared folder.

## 5. User and Permission Configuration

1. Create separate user accounts.
2. Configure shared folder access permissions.
3. Assign the appropriate permissions to each user.
4. Verify access using the intended user accounts.

## 6. SMB File Sharing Configuration

1. Open the SMB/CIFS service settings.
2. Enable the SMB service.
3. Add the intended shared folder to the SMB configuration.
4. Apply and save the configuration.
5. Verify that the shared folder is accessible from client devices.

## 7. Client Connection

### Windows 11

1. Open File Explorer.
2. Navigate to the network location using the NAS address.
3. Enter the appropriate credentials when prompted.
4. Access the shared folder.

Example network path:

`\\<NAS-LAN-IP>\<SHARE-NAME>`

### Android

1. Open CX File Explorer.
2. Navigate to the Network or SMB section.
3. Add the NAS server address.
4. Enter the appropriate user credentials.
5. Open the shared folder.

## 8. Verification

- Confirm successful access from Windows 11.
- Confirm successful access from Android.
- Test file uploads and downloads.
- Verify that user permissions behave as configured.

## 9. Notes

The procedures above describe the main deployment workflow. Exact menus and options may differ depending on the OpenMediaVault version.

Sensitive information such as passwords and private network details should not be included in public documentation.
