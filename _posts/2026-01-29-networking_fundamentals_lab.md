---
title: "Networking Fundamentals Lab with VirtualBox"
date: 2026-01-29 09:42:05 +0000
categories: [windows server, network, home lab]
tags: [dhcp,dns, active directory, subnetting, tcp/ip, virtualbox, internal networking, ip addressing, routing basics, windows server 2022]     # TAG names should always be lowercase
image: /assets/media/networking_home_lab/home_lab.png
---

<div class="skills-box">
  <strong>Skills:</strong>
  <ul>
    <li>Designed a private `/24` network  </li>
    <li>Configured DHCP scopes and leases </li>
    <li>Implemented DNS and tested name resolution  </li>
    <li>Tested routing and default gateway behaviour </li>
    <li>Built an isolated network using VirtualBox</li>
  </ul>
</div>

---

## Overview

This lab covers the following networking concepts:

- Subnetting and network design  
- Static IP address configuration  
- DHCP scope creation and lease testing  
- DNS configuration and name resolution  
- Routing and default gateway behaviour  
- Connectivity testing between devices  

## Network Design and Subnetting

```text
                         +----------------------------------+
                         | Domain Controller                |
                         | -------------------------------- |
                         | Hostname     : DC                |
                         | IP Address   : 172.16.0.1        |
                         | Subnet Mask  : 255.255.255.0     |
                         | Default GW   : (none / isolated) |
                         | DNS Server   : 127.0.0.1         |
                         | Roles        : AD DS, DNS, DHCP  |
                         +------------------+---------------+
                                            |
                                    VirtualBox Internal
                                          Network
                                            |
        +-----------------------------------+-----------------------------------+
        |                                   |                                   |
+--------------------+          +--------------------+          +--------------------+
| Client VM 01       |          | Client VM 02       |          | Client VM 03       |
| IP Address : DHCP  |          | IP Address : DHCP  |          | IP Address : DHCP  |
| Subnet Mask: /24   |          | Subnet Mask: /24   |          | Subnet Mask: /24   |
| Default GW : .1    |          | Default GW : .1    |          | Default GW : .1    |
| DNS Server : .1    |          | DNS Server : .1    |          | DNS Server : .1    |
+--------------------+          +--------------------+          +--------------------+
```

The lab uses the private Class B subnet:

- **Network:** `172.16.0.0/24`
- **Subnet Mask:** `255.255.255.0`
- **Usable Hosts:** `172.16.0.1 – 172.16.0.254`

### Addressing Plan

| Device / Role     | IP Address       | Notes               |
| ----------------- | ---------------- | ------------------- |
| Domain Controller | 172.16.0.1       | Static IP           |
| DHCP Scope        | 172.16.0.100–200 | Assigned to clients |
| Default Gateway   | N/A (isolated)   | Conceptual only     |
| DNS Server        | 172.16.0.1       | Hosted on DC        |

---

## VirtualBox Network Setup

All virtual machines are connected to a **VirtualBox Internal Network**.

**Benefits:**
- Full isolation from host and internet  
- Safe testing environment  
- Predictable routing behaviour  

---

## Server Configuration (Static IP)

The Windows Server VM (Domain Controller) is configured with a static IP:

- **IP Address:** `172.16.0.1`
- **Subnet Mask:** `255.255.255.0`
- **Default Gateway:** *(none)*
- **DNS Server:** `127.0.0.1`

The DNS server points to localhost because DNS is hosted on the Domain Controller.

---

## DHCP Configuration

The **DHCP Server role** is installed on the Windows Server VM.

### DHCP Scope Settings

| Setting         | Value         |
| --------------- | ------------- |
| Start IP        | 172.16.0.100  |
| End IP          | 172.16.0.200  |
| Subnet Mask     | 255.255.255.0 |
| Default Gateway | 172.16.0.1    |
| DNS Server      | 172.16.0.1    |

---

### DHCP Lease Testing

Client machines are configured to obtain an IP address automatically.

### Commands Used

```shell
ipconfig /release
ipconfig /renew
ipconfig /all
```
### Example Lease Details

IP Address: 172.16.0.100
Lease Type: DHCP
DNS Server: 172.16.0.1
Domain: mydomain.com

### DNS Testing

Installing Active Directory Domain Services automatically installs and configures DNS.

### DNS Test Commands
```shell
nslookup dc.mydomain.com
ping dc.mydomain.com
ipconfig /displaydns
```
**Expected Results**

- nslookup returns 172.16.0.1
- ping resolves the hostname successfully
- displaydns shows cached DNS entries

## Routing and Default Gateway Behaviour

Clients use 172.16.0.1 as a default gateway to simulate routing behaviour.

**Routing Tests**

```shell
ipconfig
ping 172.16.0.1
tracert 8.8.8.8
```

**Explanation**

- Gateway responds to ping
- tracert stops at the gateway due to isolation
- No external routing exists in this lab
- Connectivity Testing
- Connectivity is tested from a client machine.

**Ping Tests**
```shell
ping 172.16.0.1
ping dc
ping dc.mydomain.com
```
**Expected Outcome**

- Name resolution works correctly
- IP connectivity is confirmed
- Domain Controller is reachable

## Conclusion

This lab demonstrates essential networking fundamentals required for many IT and infrastructure roles, including:
- DHCP configuration and testing
- DNS resolution
- Subnetting and IP planning
- Default gateway behaviour
- Client-server connectivity


