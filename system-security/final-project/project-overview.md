# Final Project: Enterprise Network – System Security Deployment

## Objective
To design, configure, and secure a simulated enterprise network as part of a capstone project in System Security. The project involved setting up core infrastructure, applying system hardening techniques, managing domains, and implementing technical controls aligned with CIS Critical Security Controls - all within a closed virtual lab environment.

## Technologies Used
- pfSense Firewall (Simulated)
- Windows Server 2022 (Active Directory)
- Ubuntu Desktop & Server (Client + MediaWiki)
- Rocky Linux (MariaDB Database)
- MediaWiki (Web Application)
- VMware vSphere
- CIS Critical Security Controls (V8)

## Simulated Network Architecture

- **pfSenseRouter**  
  - WAN: `192.168.X.X/24`  
  - AdminNet: `10.42.X.X/24`  
  - ServerNet: `10.43.X.X/24`  

- **ADServer**  
  - Deployed as a Windows Domain Controller (`catflixXX.local`)  
  - Created domain users and group policies  

- **Sin10Client**  
  - Initially infected, malware removed  
  - Later joined to the domain  

- **UbuntuWebServer**  
  - Hosted MediaWiki site with custom branding  
  - Hardened using Linux permissions and firewall rules  

- **RockyDBServer**  
  - MariaDB configured as the MediaWiki backend  

- **UbuntuClient**  
  - Connected to ServerNet for DNS and functionality testing  

⚠️ _All network components and IPs were configured and tested inside a closed virtual lab environment._

## Key Security Configurations

### Firewall Hardening (pfSense)
- Default **deny-all** policy across all interfaces
- Allowed:
  - Only Sin10Client to access pfSense UI (HTTPS) and SSH
  - External access to **only** the MediaWiki homepage
  - AdminNet → ServerNet: unrestricted internal traffic
  - AdminNet/ServerNet: outbound DNS, HTTP, HTTPS, and ping only

### Malware Removal
- Used Wireshark on Sin10Client to identify C2 IP traffic
- Removed malware, verified no persistence after reboot
- Created a pfSense firewall rule to permanently block malicious IP
- Joined Sin10Client to the domain after cleanup

### Web Server Setup & Hardening
- Installed MediaWiki with:
  - `sysadmin` as the administrator account
  - Custom logo and title reflecting the simulated internal wiki
- Performed Linux hardening:
  - Disabled unused services
  - Configured strict file/folder permissions
  - Applied Apache access controls and firewall restrictions

## CIS Critical Security Controls Implemented

1. **CIS Control 1 & 2 – Inventory of Hardware/Software**
   - Documented all virtual machines, IPs, and services

2. **CIS Control 4 – Secure Configuration**
   - Hardened SSH and Apache
   - Enforced password policies and disabled unnecessary accounts

3. **CIS Control 6 – Access Control**
   - Restricted administrative privileges
   - Created role-based user accounts (`sysadmin`, `ADadmin`)
   - Used security group `SecDev` for permission management

## Validation & Testing
- Confirmed NAT, DNS, and DHCP via command-line tools
- Verified firewall rules using internal/external test clients
- Successfully joined Sin10Client to domain and applied GPOs
- MediaWiki homepage accessible externally, all other services internally restricted

## Outcome
Successfully deployed a multi-layered enterprise network simulation and demonstrated the ability to secure it using industry best practices. Covered everything from domain management and malware response to firewall rule creation and CIS-aligned control implementation.

⚠️ _Note: All data, IP addresses, domain names, and configurations shown in this project are part of a private, simulated lab environment and do not reflect any real-world infrastructure._

<div align="center">

--- 🔹🔹🔹 End of Section 🔹🔹🔹 ---

</div>

