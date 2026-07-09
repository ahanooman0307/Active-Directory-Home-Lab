# Group Policy

## Overview

Group Policy provides centralized management of Windows computers and users within an Active Directory environment. In this home lab, Group Policy was used to automatically map department-specific network drives to domain users after they logged into the Windows 10 Pro client.

---

## Environment

| Component | Configuration |
|-----------|---------------|
| Domain | mydomain.com |
| Domain Controller | Windows Server 2022 |
| Client | Windows 10 Pro |
| Hypervisor | Oracle VirtualBox |
| Host OS | Ubuntu Linux |

---

## Objectives

The objectives of this Group Policy implementation were to:

- Centralize user configuration
- Automatically map shared network drives
- Apply policies based on Active Directory Security Groups
- Simulate enterprise Windows domain management
- Verify successful Group Policy application on domain clients

---

## Configuration Steps

### 1. Created Shared Folders

Created department-specific shared folders on the Domain Controller for user access.

### 2. Configured Share & NTFS Permissions

Assigned permissions using Active Directory Security Groups to ensure users could only access resources for their department.

### 3. Created a Group Policy Object (GPO)

Using **Group Policy Management**, created a new GPO responsible for mapping network drives.

### 4. Configured Drive Mapping

Configured the GPO under:

```
User Configuration
└── Preferences
    └── Windows Settings
        └── Drive Maps
```

Configured the network drive to:

- Action: **Create**
- Location: Network Share
- Drive Letter: Assigned drive letter
- Label: Department Share

### 5. Linked the GPO

Linked the Group Policy Object to the appropriate Organizational Unit containing the target users.

### 6. Applied the Policy

Updated Group Policy on the client using:

```cmd
gpupdate /force
```

Verified successful policy application using:

```cmd
gpresult /r
```

---

## Verification

Successfully verified:

- Windows 10 Pro client received the Group Policy.
- Network drive mapped automatically after user login.
- Users could access only authorized shared folders.
- Group Policy applied successfully after troubleshooting and policy refresh.

---

## Troubleshooting

During implementation, the mapped network drive did not initially appear on the Windows 10 client.

The issue was diagnosed by:

- Running `gpresult /r`
- Verifying Group Policy links
- Confirming Security Group membership
- Checking SMB share permissions
- Verifying NTFS permissions
- Testing network connectivity between the client and Domain Controller
- Identifying Windows Firewall as the cause of the issue

After correcting the firewall configuration and recreating the drive mapping using the **Create** action, the policy successfully applied and the mapped drive appeared on the client.

---

## Skills Demonstrated

- Active Directory
- Group Policy Management
- Drive Mapping
- Organizational Units
- Security Groups
- SMB File Sharing
- NTFS Permissions
- Windows Server Administration
- Windows 10 Client Management
- Troubleshooting Group Policy
- Enterprise Windows Administration

---

## Related Screenshots

### Group Policy Management

![Group Policy](../screenshots/09-group-policy.png)

### Windows 10 Client Verification

![Client Verification](../screenshots/10-client-verification.png)
