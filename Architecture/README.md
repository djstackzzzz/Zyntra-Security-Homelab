# Zyntra Security — Enterprise Network Architecture

## Overview

This architecture represents an enterprise-style virtual infrastructure designed to demonstrate network security, centralized identity management, hybrid cloud integration, security monitoring, and authorized penetration testing.

## Network Architecture Diagram

```mermaid
flowchart TD
    Internet((Internet))
    Entra["Microsoft Entra ID<br/>Cloud Identity"]
    Firewall["pfSense Firewall<br/>Gateway and Network Security"]
    LAN["Internal Enterprise Network"]
    DC["DC01<br/>Windows Server 2025<br/>AD DS, DNS, GPO"]
    Sync["ENTRASYNC01<br/>Entra Cloud Sync Agent"]
    Client["Windows 11<br/>Enterprise Workstation"]
    Wazuh["Wazuh SIEM<br/>Security Monitoring"]
    Kali["Kali Linux<br/>Authorized Security Testing"]
    Shares["Department File Shares<br/>NTFS and RBAC"]

    Internet --> Firewall
    Firewall --> LAN
    LAN --> DC
    LAN --> Sync
    LAN --> Client
    LAN --> Wazuh
    LAN --> Kali
    DC --> Shares
    DC --> Sync
    Sync -->|Identity Synchronization| Entra
    DC -.->|Security Events| Wazuh
    Client -.->|Endpoint Events| Wazuh

    classDef cloud fill:#0078d4,color:#fff,stroke:#005a9e
    classDef security fill:#b91c1c,color:#fff,stroke:#991b1b
    classDef server fill:#166534,color:#fff,stroke:#14532d
    classDef endpoint fill:#334155,color:#fff,stroke:#1e293b

    class Entra cloud
    class Firewall,Wazuh security
    class DC,Sync,Shares server
    class Client,Kali endpoint
```

## Infrastructure Inventory

| System | Operating System | Primary Function |
|---|---|---|
| pfSense | FreeBSD-based | Firewall and network gateway |
| DC01 | Windows Server 2025 | Active Directory, DNS and Group Policy |
| ENTRASYNC01 | Windows Server 2025 | Hybrid identity synchronization |
| WIN11 | Windows 11 | Enterprise workstation |
| Wazuh Server | Linux | SIEM and security monitoring |
| Kali Linux | Kali Linux | Authorized penetration testing |

## Identity Management

- Centralized Active Directory administration
- 50 simulated employee accounts
- Seven organizational departments
- Role-based access control
- Least-privilege access management
- Microsoft Entra Cloud Sync
- Password hash synchronization

## Security Controls

- Network firewall protection
- Group Policy enforcement
- NTFS access permissions
- Centralized security event collection
- Endpoint security monitoring
- Vulnerability detection
- Privileged account separation

## Virtualization Platform

Oracle VirtualBox

## Security Notice

This infrastructure operates within an authorized homelab environment. Sensitive configuration details and credentials are excluded from public documentation.

## Project Status

Under continuous development.
