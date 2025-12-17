---
title: "Setting Up a Legacy Server as an Ubuntu File Server"
date: 2025-11-14 09:42:05 +0000
categories: [servers, linux]
tags: [ubuntu, fileserver, supermicro, legacy, cloud, repurpose, itskills]
image: /assets/media/ubuntu_server/IMG_9688.JPG

I had an old Supermicro server that I originally used for 3D rendering. Once I transitioned to cloud-based rendering, the server was no longer needed for that purpose. Since it was a legacy system and no longer received Windows updates, I decided to repurpose it by installing Ubuntu Desktop and turning it into a file server. The server helped to free up space and kept my workstation organised and uncluttered.

![Ubuntu Server](/assets/media/ubuntu_server/IMG_9691.JPG)
*The legacy supermicro server.*

## Step by Step

### Flashing the USB Drive

Downloaded the latest Ubuntu Desktop ISO from the official site.

Used Rufus on Windows to flash the ISO onto a USB stick (minimum 8 GB).

Verified the USB was bootable before moving on.

### Preparing the Hardware

Installed the primary SATA HDD into the server machine.

Entered the BIOS/UEFI setup to confirm the drive was detected.

Changed the boot priority so the system would boot from the USB drive first.

### Wiping and Partitioning the Drive

Booted into the Ubuntu Desktop installer from the USB.

Selected the option to erase disk and install Ubuntu.

### Installing Ubuntu Desktop

Followed the guided installer:

Selected language and keyboard layout.

Configured network settings.

Created a user account with a secure password.

Installed the system onto the newly partitioned SATA drive.

Rebooted, removed the USB, and booted into Ubuntu Desktop for the first time.

Configured the system to bypass login at startup for convenience.

![Ubuntu Server](/assets/media/ubuntu_server/IMG_9685.JPG)
*The system boot drive.*

### Post Install Setup

Updated packages:

`sudo apt update && sudo apt upgrade -y`

Installed useful tools (e.g., OpenSSH for remote access).

Configured firewall with UFW:

```bash
sudo ufw allow 2222/tcp
sudo ufw enable
```

(Port 2222 was chosen instead of the default SSH port for added flexibility.)

### Adding Extra Storage

Installed two additional SATA drives named share_1 and share_2.

Mounted them under /srv/samba/share_1 and /srv/samba/share_2 for organized access.

![Ubuntu Server](/assets/media/ubuntu_server/IMG_9686.JPG)
*The legacy supermicro server.*

### Setting Up Samba for File Sharing

Install Samba:

`sudo apt install samba -y`

Create shared directories:

```bash
sudo mkdir -p /srv/samba/share_1 /srv/samba/share_2
sudo chown nobody:nogroup /srv/samba/share_1 /srv/samba/share_2
sudo chmod 0775 /srv/samba/share_1 /srv/samba/share_2
```

Edit Samba config:

`sudo nano /etc/samba/smb.conf`

Add:

```bash
[Share_1]
   path = /srv/samba/share_1
   browseable = yes
   read only = no
   guest ok = yes

[Share_2]
   path = /srv/samba/share_2
   browseable = yes
   read only = no
   guest ok = yes
```

Restart Samba:

`sudo systemctl restart smbd`

### Remote Troubleshooting

Used the Terminus app on my iPhone to SSH into the server.

Connected using port 2222 for secure remote management.

### Networking Setup

Connected the server directly to my Windows laptop using a patch cable (wired Ethernet).

This bypassed slow Wi‑Fi speeds and provided a stable connection.

Configured both network interfaces with static IP addresses on the same subnet to ensure reliable communication.

I used a ugreen usb-c ethernet adapter with my laptop since it doesn’t have a built‑in ethernet port.

## Future Steps

Setup a RAID 1 mirror using the servers hardware RAID controller or choose the mdadm software option in Ubuntu for greater flexibility.
