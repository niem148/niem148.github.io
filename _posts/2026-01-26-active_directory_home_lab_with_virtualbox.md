---
title: "Setup a Basic Active Directory Home Lab with VirtualBox"
date: 2026-01-26 12:42:05 +0000
categories: [Windows Server 2022, Active Directory, IT Administration, Home Lab / Lab Builds]
tags: [windows-server-2022, windows-11, virtualbox, powershell, ad-ds, dns, dhcp, networking, sysadmin]
image: /assets/media/active_directory_home_lab/homelab_active_directory.png      
---

## Overview

This guide summarizes the steps demonstrated in the video *“How to Setup a Basic Home Lab Running Active Directory (Oracle VirtualBox)”*, updated to use **Windows Server 2022** as the Domain Controller and **Windows 11 Pro** as the client machine.

The lab is ideal for learning:
- Active Directory Domain Services (AD DS)
- DNS and DHCP
- NAT & Routing
- Domain joining and user management

## Reference Tutorial

The original tutorial that this lab is created from can be found here:

- **Josh Madakor – Active Directory Home Lab (VirtualBox)**  
  [https://www.youtube.com/watch?v=MHsI8hJmggI](https://www.youtube.com/watch?v=MHsI8hJmggI)

---

## Lab Architecture

- **DC VM**: Windows Server 2022  
- **Client VM**: Windows 11 Pro  
- **Hypervisor**: Oracle VirtualBox  
- **Networking**:
  - NAT (internet access)
  - Internal / Host-only (domain network)

---

## Step 1: Download Prerequisites

1. Install **Oracle VirtualBox** and the matching **Extension Pack**
2. Download:
   - **Windows Server 2022 ISO**
   - **Windows 11 ISO** (must be **Pro**, not Home)

> ⚠️ Windows 11 Home cannot join a domain.

---

## Step 2: Create the Domain Controller VM (Server 2022)

1. Create a new VM in VirtualBox:
   - Name: `DC`
   - Type: Windows
   - Version: Windows 2022 (64-bit)
   - Memory: 4-8 GB (more if available)
   - Disk: VDI, dynamically allocated

2. Configure **two network adapters**:
   - Adapter 1: **NAT**
   - Adapter 2: **Internal Network**

3. Attach the **Windows Server 2022 ISO** and start the VM.
4. Install **Windows Server 2022 – Desktop Experience**.
5. Set the local Administrator password.
![server setup](/assets/media/active_directory_home_lab/server_setup.png)  
  *Server setup.* 


---

## Step 3: Initial Server Configuration

1. Install **VirtualBox Guest Additions** (optional but recommended).
2. Rename the server to `DC` and reboot.
3. Assign a **static IP** to the internal adapter:
   - Example:
     - IP: `172.16.0.1`
     - Subnet: `255.255.255.0`
     - DNS: `127.0.0.1`

---

## Step 4: Install Active Directory Domain Services

1. Open **Server Manager**
2. Add Roles and Features → **Active Directory Domain Services**
3. Promote the server to a Domain Controller:
   - Create a **new forest**
   - Domain name: `lab.local` (recommended for labs)
4. Complete the wizard and reboot.

---

## Step 5: Create Admin and User Structure

1. Open **Active Directory Users and Computers**
2. Create Organizational Units (OUs), e.g.:
   - `_Admins`
   - `_Users`
3. Create a domain admin account and add it to:
   - **Domain Admins**
4. Log out and log back in using the domain admin account.

---

## Step 6: Configure NAT & Routing

1. Add the **Remote Access** role
2. Enable:
   - Routing
   - NAT
3. Configure NAT so the **internal network routes through the NAT adapter** for internet access.

 ![ras and nat](/assets/media/active_directory_home_lab/ras_nat.png)  
  *RAS and NAT.* 
---

## Step 7: Install and Configure DHCP

1. Add the **DHCP Server** role
2. Create a DHCP scope:
   - Range: `172.16.0.100 – 172.16.0.200`
   - Gateway: `172.16.0.1`
   - DNS: `172.16.0.1`
3. Authorize the DHCP server in AD.

 ![DHCP scope](/assets/media/active_directory_home_lab/dhcp_scope.png)  
  *DHCP scope.* 

## Step 8: Use the powershell script to bulk add users

1. The PowerShell script loops through each name, splits first/last and generates a username.
2. A text file contains a list of names.
3. After running the script, all users appear in ADUC inside the chosen OU.

---

## Step 9: Create Windows 11 Client VM

1. Create a new VM:
   - Name: `CLIENT1`
   - OS: Windows 11 (64-bit)
   - RAM: 4-8 GB recommended
2. Network Adapter:
   - **Internal Network** (same as DC)
3. Install **Windows 11 Pro**
   - Skip Microsoft account if allowed or create a temp microsoft account and later switch to local account.

---

## Step 10: Join Windows 11 to the Domain

1. Confirm the client receives an IP from DHCP.
2. Rename the PC to `CLIENT1`.
3. Join the domain:
   - Domain: `lab.local`
   - Credentials: Domain admin account
4. Reboot when prompted.

---

## Step 11: Verify the Lab

From the Windows 11 client:
- Log in using a **domain user**
- Confirm:
  - Internet access works
  - Domain login succeeds
  - Client appears in ADUC

From the Domain Controller:
- Verify DNS, DHCP leases and domain membership.

---
