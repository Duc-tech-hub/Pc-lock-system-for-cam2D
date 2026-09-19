# Intruder Monitoring System

## Overview

The Intruder Monitoring System is an advanced security application designed to protect workstation environments, monitor unauthorized access attempts, and maintain comprehensive violation logs through automated facial recognition, system-level locking, and cloud storage integration.

## Key Features

* **Live Facial Detection and Anti-Spoofing**: The client interface uses face-api.js to process webcam video streams, measure head pitch ratios to prevent static image spoofing, and verify face descriptors. Also, this system have live detection.
* **System-Level Security Control**: The backend server manages workstation security by updating the Windows Winlogon shell registry, terminating explorer.exe, and deploying a locked browser kiosk interface.
* **Cloud Storage and Database Integration**: Captured intrusion snapshots are automatically uploaded to Cloudinary, while violation records, timestamps, and reasons are persistently stored in Firebase Firestore.
* **Administrative Management Dashboard**: Authorized users can authenticate via facial verification or a master password to access a centralized dashboard, view violation logs grouped by date, and execute individual or bulk deletion tasks. This dashboard use vercel middleware to secure the database

## Property

* The system uses Windows encryption devices to protect your data from being read by intruders.
* The system disables the blue screen to prevent attackers from reaching safe mode, which could otherwise help them disable the system.
* Furthermore, in the Learn.md file, we instruct you on how to set up a BIOS passcode. Because the BIOS is the root system used to start your PC or laptop, attackers can exploit it to plug in a bootable virus USB or reinstall Windows.
* Launcher.exe, the shell file that replaces your user interface, is written in the C language, providing massive speed for the system to lock all keys and block access to the command prompt. After you unlock your device, this shell file is terminated and explorer.exe is started.
* Finally, this system runs locally; an internet connection is not necessary to unlock your device. Internet access is only required for uploading the intruder's image to the cloud.

## Data Flow

### pc-lock-system folder
index.html (Intruder's image) -> server.js -> Cloudinary -> server.js (save link to database) -> firestore

### Monitoring_system folder (Watch pictures)
index.html (request) -> intruder.js -> firestore -> intruder.js -> index.html