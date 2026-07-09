# Domain Name System (DNS)

## Overview

This document explains how Domain Name System (DNS) was configured in my Windows Server 2022 Active Directory home lab. DNS provides name resolution for devices on the network and is a core dependency of Active Directory, allowing domain-joined computers to locate services such as the Domain Controller.

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

The objectives of this implementation were to:

- Configure DNS for the Active Directory domain
- Create a Forward Lookup Zone
- Enable hostname resolution between domain devices
- Support Active Directory authentication and domain services
- Verify successful DNS name resolution

---

## Configuration Steps

### 1. Installed the DNS Server Role

Installed the DNS Server role while promoting the Windows Server to a Domain Controller.

---

### 2. Created the Active Directory DNS Zone

Configured an Active Directory-integrated Forward Lookup Zone for:

```text
mydomain.com
```

This allows DNS records to be stored within Active Directory and replicated automatically.

---

### 3. Verified DNS Records

Confirmed that DNS records were automatically created for domain resources, including:

- Domain Controller (DC)
- Windows 10 Pro Client (CLIENT1)
- Name Server (NS)
- Start of Authority (SOA)

These records allow devices to locate domain services using hostnames instead of IP addresses.

---

### 4. Configured the Client

Configured the Windows 10 Pro client to use the Domain Controller as its DNS server.

The client uses:

```text
172.16.0.1
```

for all DNS queries within the domain.

---

## Verification

Successfully verified:

- The Forward Lookup Zone was created.
- DNS records were present for the Domain Controller and client.
- The Windows 10 Pro client successfully resolved domain resources.
- Active Directory authentication functioned correctly using DNS.

---

## Importance of DNS in Active Directory

DNS is one of the most important services in an Active Directory environment.

It enables clients to:

- Locate the Domain Controller
- Authenticate users
- Apply Group Policy
- Access shared resources
- Resolve hostnames across the domain

Without a properly configured DNS server, Active Directory services would not function correctly.

---

## Skills Demonstrated

- Windows Server Administration
- DNS Server
- Active Directory Integration
- Forward Lookup Zones
- Hostname Resolution
- Windows Networking
- Domain Services
- Windows Client Configuration

---

