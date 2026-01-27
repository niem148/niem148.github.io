---
title: "Windows Server 2022 File Server & Drive Mapping Guide"
date: 2026-01-26 09:42:05 +0000
categories: [Windows Server 2022, Active Directory & Group Policy, File Server Management, IT Administration, Home Lab / Lab Builds]
tags: [Windows Server 2022, File Server, FSRM, File Server Resource Manager, VSS Agent Service, SMB Shares, Drive Mapping]
image: /assets/media/windows_server_2022_fileserver/server_manager.png      
---

<div class="skills-box">
  <strong>Skills:</strong>
  <ul>
    <li>Windows Server 2022 file server configuration</li>
    <li>Group Policy Object (GPO) creation and management</li>
    <li>Drive mapping using Group Policy Preferences</li>
    <li>User and group management in Active Directory</li>
    <li>Troubleshooting connectivity issues</li>
    <li>Joining a domain from a client machine</li>
  </ul>
</div>

A structured walkthrough for installing the **File Server role** (including **FSRM** and **VSS Agent Service**), creating the **SALES** share at `C:\Shares\SALES`, applying a **10 GB quota**, and mapping the share for all users in the `_USERS` OU using **Group Policy**.

---

## 1. Prerequisites

- **Operating System:** Windows Server 2022 (domain-joined)
- **Permissions:** Domain Admin or equivalent
- **Domain Environment:** Active Directory configured

---

## 2. Install File Server, FSRM, and VSS Agent Service

### 2.1 Start the Add Roles and Features Wizard

1. Open **Server Manager**
2. Select **Manage → Add Roles and Features**
3. Choose **Role-based or feature-based installation**
4. Click **Next**
5. Select the target server
6. Click **Next**

 ![Fileserver Roles](/assets/media/windows_server_2022_fileserver/fileserver_role.png)  
  *Adding the filserver role and additional services.* 


---

### 2.2 Select Required Role Services

1. Expand:
   - **File and Storage Services**
     - **File and iSCSI Services**
2. Enable the following:
   - ✅ File Server  
   - ✅ File Server Resource Manager  
   - ✅ File Server VSS Agent Service
3. Accept any prompts to add required features
4. Complete the wizard:
   - **Next → Install → Close**

---

## 3. Create the SALES Share (`C:\Shares\SALES`)

### 3.1 Create the Share in Server Manager

1. Open **Server Manager**
2. Navigate to: **File and Storage Services → Shares**

3. Select **TASKS → New Share**
4. Choose **SMB Share – Quick**
5. Browse to: (`C:\Shares\SALES`)

6. Configure the share:
- **Share Name:** `SALES`
- **UNC Path:**
  ```
  \\DC.mydomain.com\SALES
  ```

7. Configure share options as required
8. Set permissions (example):
- `SALES_Users` → **Modify**
9. Confirm settings and select **Create**
10. Click **Close**
 ![Creating the share](/assets/media/windows_server_2022_fileserver/create_share.png)  
  *Creating the share.* 


---

## 4. Apply a 10 GB Quota Using FSRM

### 4.1 Open File Server Resource Manager

1. Open **Server Manager**
2. Go to: **Tools → File Server Resource Manager**

---

### 4.2 Apply the Quota to the SALES Folder

1. Right-click **Quotas** → **Create Quota**
2. Set **Quota Path**:(`C:\Shares\SALES`)

3. Select:
- **Derive properties from this quota template**
4. Choose a **10 GB quota template**
- Create one beforehand if required
5. Click **Create**
6. Close the console
 ![Creating the quota](/assets/media/windows_server_2022_fileserver/create_quota.png)  
  *Creating the quota.* 
---

## 5. Map the SALES Share for All Users in `_USERS` OU (Group Policy)

### 5.1 Open Group Policy Management

1. Open **Server Manager**
2. Navigate to:**Tools → Group Policy Management**

---

### 5.2 Create and Link a GPO

1. Locate the `_USERS` OU
2. Right-click → **Create a GPO in this domain, and Link it here**
3. Name the GPO:**Map SALES Drive for USERS**

---

### 5.3 Configure Drive Mapping

1. Right-click the new GPO → **Edit**
2. Navigate to:**User Configuration → Preferences → Windows Settings → Drive Maps**


3. Right-click → **New → Mapped Drive**
4. Configure the following:

| Setting      | Value                     |
| ------------ | ------------------------- |
| Action       | Create                    |
| Location     | `\\DC.mydomain.com\SALES` |
| Label        | SALES                     |
| Drive Letter | `S:`                      |
| Reconnect    | Enabled (optional)        |

5. Save and close the Group Policy Editor

 ![Fileserver Roles](/assets/media/windows_server_2022_fileserver/drive_mapping.png)  
  *Mapping the SALES share for _USERS.* 


---

### 5.4 Test the Mapping

1. On a client machine, run:

powershell

```bash
gpupdate /force
```

Log off and log back on as a user in the _USERS OU

Confirm:

S: drive is mapped

Points to: `\\DC.mydomain.com\SALES`
