---
title: "Helpdesk Scenario: Network Connectivity Troubleshooting"
date: 2026-01-30
categories: [Helpdesk, Troubleshooting]
tags: [Networking, CompTIA, Diagnostics, Windows, Command Line]
description: "A realistic helpdesk-style walkthrough of diagnosing a user's network connectivity issue using the CompTIA A+ troubleshooting methodology."
image: /assets/media/network_connectivity/modern clean header.png   
---

<div class="skills-box">
  <strong>Skills:</strong>
  <ul>
    <li>Structured troubleshooting — following the CompTIA A+ methodology  </li>
    <li>Command-line diagnostics — using ipconfig, ping, tracert  </li>
    <li>DNS and DHCP analysis — identifying root causes  </li>
    <li>Clear user communication — guiding users through resolution </li>
    <li>Ticket documentation — recording findings and outcomes</li>
  </ul>
</div>

## Overview

This post walks through a realistic helpdesk scenario using the CompTIA A+ troubleshooting methodology to resolve a network connectivity issue. It demonstrates structured diagnostics, command-line tools, and clear communication — all essential for IT support roles.

---

## 1. Identify the Problem

User reports:  
“I can’t access the internet.”

Clarifying questions:  
Is it wired or wireless?  
Is it just one device or multiple?  
What changed recently?

---

## 2. Establish a Theory of Probable Cause

Possible causes:  
DHCP failure  
DNS misconfiguration  
Physical cable issue  
NIC driver problem  
Firewall blocking traffic

---

## 3. Test the Theory

Run diagnostic commands:

```shell
ipconfig /all
ping 8.8.8.8
ping google.com
tracert 8.8.8.8
```

## 4. Establish a Plan of Action and Implement the Solution

Depending on findings, follow the steps below:

### Case 1: No IP Address

**Solution:** Release and renew DHCP lease

```bash
ipconfig /release
ipconfig /renew
```
![Commands](/assets/media/network_connectivity/Screenshot 2026-01-30 112334.png) 
![Commands](/assets/media/network_connectivity/Screenshot 2026-01-30 114207.png) 
![Commands](/assets/media/network_connectivity/Screenshot 2026-01-30 114226.png) 

### Case 2: DNS Failure

**Solution:** Change DNS server using the Windows GUI.

1. Open **Control Panel**.  
2. Navigate to **Network and Internet → Network and Sharing Center**.  
3. Click on **Change adapter settings** on the left panel.  
4. Right-click your **Ethernet** connection and select **Properties**.  
5. In the **This connection uses the following items** list, select **Internet Protocol Version 4 (TCP/IPv4)** and click **Properties**.  
6. Choose **Use the following DNS server addresses:**  
   - **Preferred DNS server:** `8.8.8.8`  
   - **Alternate DNS server:** `1.1.1.1`  
7. Click **OK** to save changes, then **Close**.  
8. Restart your browser or computer to apply the new DNS settings.

![Commands](/assets/media/network_connectivity/Screenshot 2026-01-30 114621.png) 

### Case 3: NIC (Network Interface Card) Failure

**Solution:** Reinstall or update the network adapter driver.

1. Open **Device Manager**:

```shell
devmgmt.msc
```

1. Expand **Network adapters** in Device Manager.
2. Right-click your network adapter and select **Uninstall device**.
3. Confirm any prompts that appear.
4. Restart your computer.
5. Windows will automatically detect the NIC and reinstall the driver.
6. *(Optional)* To update the driver manually:
   - Right-click the NIC → **Update driver** → **Search automatically for drivers**

![Commands](/assets/media/network_connectivity/Screenshot 2026-01-30 115444.png)

## 5. Document Findings, Actions, and Outcomes

Example ticket notes:

- Issue: DHCP lease failure
- Action: Renewed lease, verified IP
- Outcome: User regained connectivity
- Ticket: #12345 updated with resolution steps
