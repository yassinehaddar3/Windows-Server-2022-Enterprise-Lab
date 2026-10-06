# 🏢 Windows Server 2022 Enterprise Infrastructure Lab

## 🎯 Objective
This project demonstrates the deployment, configuration, and troubleshooting of a complete enterprise IT infrastructure using **Windows Server 2022** and **Windows 10**. The goal is to showcase practical System Administration skills, focusing on Active Directory, Network Services, Automation, Security, and Incident Resolution.

## 🏗️ Architecture & Topology
*   **Hypervisor:** VMware Workstation
*   **Network:** Host-Only (VMnet2) - Dedicated isolated network.
*   **Domain:** `lab1.local`
*   **Server (DC01):** Windows Server 2022 (Static IP: 192.168.10.10)
*   **Client (CLT-W10):** Windows 10 Pro (DHCP assigned IP)

## 🛠️ Technologies & Roles Implemented
*   Active Directory Domain Services (AD DS)
*   Domain Name System (DNS - Forward & Reverse Lookup Zones)
*   Dynamic Host Configuration Protocol (DHCP)
*   Group Policy Objects (GPO)
*   PowerShell Scripting (Automation)
*   File Server (SMB & NTFS Permissions)
*   Windows Server Backup

## 🚀 Key Milestones Completed

### Phase 1: Core Infrastructure Setup
*   Configured static IP addressing and promoted DC01 to a Domain Controller.
*   Configured DNS zones and integrated a Windows 10 Client into the `lab1.local` domain.
*   Configured a DHCP Scope (192.168.10.100 - 200).

### Phase 2: Active Directory & Automation
*   Designed the Organizational Unit (OU) structure (`IT_Department`).
*   **PowerShell Automation:** Created a script to bulk-create AD users and assign passwords securely from a CSV file.

### Phase 3: Security & File Management
*   **GPO:** Enforced user restrictions (blocked access to Control Panel) and verified application via `gpresult`.
*   **Security:** Implemented Account Lockout Policies (3 invalid attempts) to prevent brute-force attacks.
*   **File Server:** Created shared folders with restricted NTFS permissions (`Modify` for IT_Admins, `Explicit Deny` handling).
*   **Backup:** Added a virtual disk and performed a successful Windows Server Backup.

---

## 🔧 Troubleshooting Scenarios (Real-world Incident Management)
*This lab includes deliberate failure scenarios to demonstrate diagnostic and troubleshooting methodologies.*

1.  **DNS Resolution Failure:** Diagnosed a stopped DNS service causing domain unreachable errors. (`ipconfig /flushdns`).
2.  **DHCP Exhaustion/APIPA:** Resolved an issue where the client received a `169.254.x.x` IP by diagnosing and reactivating the DHCP Scope.
3.  **NTFS Permission Conflict:** Troubleshot an "Access Denied" issue caused by an `Explicit Deny` rule overriding group permissions.
4.  **Unapplied Group Policy:** Investigated a Ghost GPO issue using `gpresult /r` and resolved it by re-enabling the GPO Link.
5.  **PowerShell Execution Blocked:** Handled script execution errors by securely modifying the Execution Policy to `RemoteSigned`.
6.  **Broken Trust Relationship:** Repaired a broken secure channel between the Windows 10 workstation and the Domain Controller using the PowerShell cmdlet `Test-ComputerSecureChannel -Repair` without unjoining the domain.

---
*Created by [Your Name/Username] - Aspiring System and Network Administrator.*
