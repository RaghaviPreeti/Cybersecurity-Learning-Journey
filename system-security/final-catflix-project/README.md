# Final Project: Catflix Enterprise Network – System Security Deployment

## Objective
To design, configure, and secure a simulated enterprise network for a fictional client, “Catflix,” as part of a capstone project in System Security. The project includes setting up infrastructure, applying system hardening, managing domains, and implementing technical controls aligned with CIS Critical Security Controls - all within a closed virtual lab environment.

---

## Technologies Used
- pfSense Firewall (Simulated)
- Windows Server 2022 (Active Directory)
- Ubuntu Desktop & Server (Client + MediaWiki)
- Rocky Linux (MariaDB Database)
- MediaWiki (Web Application)
- VMware vSphere
- CIS Critical Security Controls (V8)

---

## Simulated Network Architecture

- **pfSenseRouter**  
  - WAN: `192.168.254.X/24`  
  - AdminNet: `10.42.X.0/24`  
  - ServerNet: `10.43.X.0/24`  

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

> _All network components and IPs were configured and tested inside a closed virtual lab environment._

---

## Key Security Configurations

### Firewall Hardening (pfSense)
- Default **deny-all** policy across all interfaces
- Allowed:
  - Only Sin10Client to access pfSense UI (HTTPS) and SSH
  - External access to **only** the MediaWiki homepage
  - AdminNet → ServerNet: unrestricted internal traffic
  - AdminNet/ServerNet: outbound DNS, HTTP, HTTPS, and ping only

📸 See `firewall-screenshots/` for pfSense rule documentation

---

### Malware Removal
- Used Wireshark on Sin10Client to identify C2 IP traffic
- Removed malware, verified no persistence after reboot
- Created a pfSense firewall rule to permanently block malicious IP
- Joined Sin10Client to the domain after cleanup

---

### Web Server Setup & Hardening
- Installed MediaWiki with:
  - `sysadmin` as administrator
  - Custom logo and title: **Catflix Admin Wiki**
- Performed Linux hardening:
  - Disabled unused services
  - Configured strict file/folder permissions
  - Applied Apache access controls and firewall restrictions

---

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

📸 See `controls-screenshots/` for configuration

---

## Validation & Testing
- Confirmed NAT, DNS, and DHCP via command-line tools
- Verified firewall rules using internal/external test clients
- Successfully joined Sin10Client to domain and applied GPOs
- MediaWiki homepage accessible externally, all other services internally restricted

---

## Appendices
- **Appendix A:** Network Topology Diagram  
- **Appendix B:** pfSense Firewall Rules (All Interfaces)  
- **Appendix C:** CIS Controls Implementation Proof

---

## Outcome
Successfully deployed a multi-layered enterprise network simulation and demonstrated the ability to secure it using industry best practices. Covered everything from domain management and malware response to firewall rule creation and CIS-aligned control implementation.

> ⚠️ _Note: All data, IP addresses, domain names, and configurations shown in this project are part of a private, simulated lab environment and do not reflect any real-world infrastructure._

