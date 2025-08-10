# UBNetDef F24 Informational Report

**Author:** Raghavi  
**Date:** November 29, 2024  

<div align="center">

----- [ Section Break ] -----

</div>

**Note:** All IP addresses, domain names, and usernames in this report are from a simulated lab environment.  

## Table of Contents
1. [Executive Summary](#executive-summary)
2. [Technical Findings](#technical-findings)
   - [CIS Control 01: Inventory and Control of Enterprise Assets](#cis-control-01-inventory-and-control-of-enterprise-assets)
   - [CIS Control 04: Secure Configuration of Enterprise Assets and Software](#cis-control-04-secure-configuration-of-enterprise-assets-and-software)
   - [CIS Control 14: Controlled Access Based on the Need to Know](#cis-control-14-controlled-access-based-on-the-need-to-know)
3. [Works Cited](#works-cited)
4. [Appendices](#appendices)

---

## Executive Summary
UBNetDef implemented essential security measures to safeguard Catflix’s critical systems and infrastructure.  
Efforts focused on restricting access to sensitive assets, monitoring key activities, and minimizing risks from unauthorized access or modifications.  
Key measures included:
- Applying Access Control Lists (ACLs) to critical configuration files.
- Enhancing logging policies for accountability.
- Blocking malicious IP addresses via firewall rules.
- Enforcing User Account Control (UAC) prompts for administrative changes.

These steps addressed immediate security concerns while creating a resilient framework against evolving threats.

<div align="center">

----- [ Section Break ] -----

</div>

## Technical Findings

### CIS Control 01: Inventory and Control of Enterprise Assets

**Summary:**  
Active scanning was conducted on AdminNet, ServerNet, and the External Interface to build an inventory of connected devices, identify services, and detect unauthorized access points.

#### Observations
**AdminNet (10.42.X.X/24)**  
- **AD Server** – Windows Server with LDAP, Kerberos, and DNS services.  
- **Workstation** – Windows OS with Microsoft RPC, NetBIOS, and SMB services.

**ServerNet (10.43.X.X/24)**  
- **Database Server** – MariaDB with SSH and MySQL ports open.  
- **Web Server** – Ubuntu Linux with Apache HTTP and SSH.  
- **Client Machine** – Ubuntu Linux with no open ports (hardened).

**External Interface**  
- DNS, HTTP, and HTTPS services available for public access.

#### Risk Reduction & Operational Improvements
- Unauthorized devices were identified and removed.
- Reduced attack surface via service restriction.
- Improved troubleshooting through a clear inventory.

#### Comprehensive Device Inventory
| IP Address     | Network     | Device Type      | OS / Service Info               | Open Ports      |
|----------------|-------------|------------------|--------------------------------- |-----------------|
| 10.42.X.X      | AdminNet    | Windows Server   | LDAP, Kerberos, DNS              | 53, 88, 135, 389, 445 |
| 10.42.X.X      | AdminNet    | Workstation      | RPC, NetBIOS, SMB                | 135, 139, 445   |
| 10.43.X.X      | ServerNet   | Database Server  | MariaDB, SSH                     | 22, 3306        |
| 10.43.X.X      | ServerNet   | Web Server       | Apache HTTP, SSH                 | 22, 80          |
| 10.43.X.X      | ServerNet   | Client Machine   | No services exposed              | None            |
| 192.168.XXX.XX | External    | Router/Gateway   | DNS, HTTP, HTTPS                 | 53, 80, 443     |

<div align="center">

----- [ Section Break ] -----

</div>

### CIS Control 04: Secure Configuration of Enterprise Assets and Software

**Summary:**  
Hardened system configurations to secure critical servers and applications.

#### Actions Taken
1. **Advanced Audit Policies on AD Server** – Enabled logging for credential validation and account management.  
2. **User Account Control (UAC)** – Configured to “Always Notify” for admin actions.  
3. **Database Firewall Rule** – Limited MySQL access to the web server only.  
4. **Apache File Permissions** – Set to `640` to restrict unauthorized edits.

#### Risk Reduction & Operational Improvements
- Enhanced visibility for authentication and account changes.  
- Reduced risk from unauthorized admin changes.  
- Limited database access points to trusted systems.  
- Protected Apache configs from tampering.

<div align="center">

----- [ Section Break ] -----

</div>

### CIS Control 14: Controlled Access Based on the Need to Know

**Summary:**  
Restricted access to sensitive configuration files on the web and database servers.

#### Actions Taken
1. **Apache Config Directory ACLs** – Granted read-only access to `sysadmin` user.  
2. **MariaDB Config ACLs** – Granted read-write access to `sysadmin`, read-only to others.

#### Risk Reduction & Operational Improvements
- Prevented unauthorized changes to critical configs.  
- Reduced chance of accidental misconfigurations.  
- Enforced role-based access.

<div align="center">

----- [ Section Break ] -----

</div>

## Works Cited
1. CIS Security, “CIS Controls – Version 8.” Available: https://is.gd/CISSecurity  
2. Microsoft, “Audit Policy Recommendations.” Available: https://shorturl.at/Bqu0E  
3. Microsoft, “User Account Control (UAC).” Available: https://shorturl.at/dTJj4  
4. GeeksforGeeks, “Access Control Lists (ACL) in Linux.” Available: https://www.geeksforgeeks.org/access-control-listsacl-linux/

<div align="center">

----- [ Section Break ] -----

</div>

## Appendices

### Appendix A: Network Topology
The network consists of three primary segments:  
- **AdminNet** – Hosts AD server and Windows workstation.  
- **ServerNet** – Hosts database server, web server, and Linux client.  
- **External Interface** – Provides limited public-facing services (HTTP, HTTPS, DNS).

### Appendix B: Firewall Rules Configuration
Firewall policies include:  
- **WAN Interface** – Allow HTTPS to web server; block all other inbound traffic.  
- **AdminNet Interface** – Allow admin workstation to access pfSense UI and SSH; permit outbound DNS/HTTP/HTTPS.  
- **ServerNet Interface** – Restrict database access to the web server only.  
- **Floating Rules** – Global block for malicious IP addresses.

<div align="center">

--- 🔹🔹🔹 End of Section 🔹🔹🔹 ---

</div>
