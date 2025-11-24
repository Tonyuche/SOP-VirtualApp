<div align="center">
  
# Standard Operations Procedure For The Setup Of Standard Virtual Linux Server For Web Application Testing. #

## Tuchtech Ltd. ##
26 Kasmere Cove  
2048043950

### Purpose of Document ###
This document clearly outlines the steps for providing a secure and standard Linux Server virtual machine to host and test web applications in scalable environment.
</div>

### Scope ###
This procedures apply to; 
* Provide a standardized procedure for deploying a virtual Linux server for web application testing.
* Ensure consistency in environment setup, networking, and software installation.
* Facilitate reproducible test environments for developers and QA teams.

### Approval Table
| Role | Name | Signature| Date |
|-----|-------|------|----|
| Prepared by | Anthony |  |November 05, 2025 | 
| Reviewed by | David (IT Manager) |  | November 10, 2025 |
| Approved by | Ben (Security officer) |  | November 15, 2025 | 
| Approved by | Richard (Network Engineer) |  | November 20, 2025|

### Resources and Requirements
* Virtualization Platform: VMware Workstation / VirtualBox / Hyper-V
* Linux Distribution: Ubuntu Server 22.04 LTS (stable, widely supported)
* Hostname: webtest-server.local
* Networking:
    * Mode: Bridged or NAT depending on test requirements
    * Static IP: 192.168.1.40
    * Subnet: 255.255.255.0
    * Gateway: 192.168.1.1

* System Resources:
    * CPU: 2 vCPUs
    * RAM: 4 GB
    * Disk: 40 GB
* User Accounts:
    * admin (sudo privileges)
    * tester (restricted access for QA)

### Accountability Matrix
| **Task / Step**                                                             | **Responsible (R)** | **Accountable (A)** | **Consulted (C)** | **Informed (I)**         |
| --------------------------------------------------------------------------- | ------------------- | ------------------- | ----------------- | ------------------------ |
| **1. Receive Server Request & Review Requirements**                         | Systems Engineer    | IT Manager          | Security Officer  | Requestor / Project Team |
| **2. Select Virtualization Platform (VMware/Hyper-V/KVM)**                  | Systems Engineer    | IT Manager          | Network Engineer  | Dev/Test Team            |
| **3. Allocate Compute Resources (CPU, RAM, Storage)**                       | Systems Engineer    | IT Manager          | Capacity Planner  | Dev/Test Team            |
| **4. Create Virtual Machine & Base Configuration**                          | Systems Engineer    | IT Manager          | Security Officer  | Dev/Test Team            |
| **5. Install Linux OS (e.g., Ubuntu, RHEL, CentOS)**                        | Systems Engineer    | IT Manager          | Security Officer  | Dev/Test Team            |
| **6. Apply OS Hardening & Security Baseline**                               | Security Officer    | IT Manager          | Systems Engineer  | Dev/Test Team            |
| **7. Configure Network (IP, DNS, Firewall Rules)**                          | Network Engineer    | Network Manager     | Security Officer  | Systems Engineer         |
| **8. Install Required Packages & Runtime (Apache/Nginx, DB clients, etc.)** | Systems Engineer    | IT Manager          | Dev/Test Team     | Security Officer         |
| **9. Create Standard Users, Groups, & Permissions**                         | Systems Engineer    | IT Manager          | Security Officer  | Dev/Test Team            |
| **10. Configure SSH Access, Keys, and Authentication**                      | Systems Engineer    | Security Officer    | Network Engineer  | Dev/Test Team            |
| **11. Apply Monitoring & Logging Agents**                                   | Systems Engineer    | IT Manager          | Security Officer  | Dev/Test Team            |
| **12. Validate Server Functionality (Smoke Testing)**                       | QA Engineer         | QA Lead             | Dev/Test Team     | IT Manager               |
| **13. Backup Configuration & Register Server in Inventory**                 | Systems Engineer    | IT Manager          | Security Officer  | Compliance Team          |
| **14. Handover to Web Application Testing Team**                            | Systems Engineer    | IT Manager          | Dev/Test Team     | Security Officer         |
             Dev - Developer, QA - Quality Assurance
### Procedure Steps; 
#### Step 1: Create Virtual Machine
* Launch virtualization software.
* Allocate CPU, RAM, and disk resources.
* Attach Ubuntu Server ISO.
#### Step 2: Install Operating System
* Boot VM from ISO.
* Follow installation wizard.
* Set hostname: ```webtest-server.local```.
* Configure static IP networking.
#### Step 3: Update System using Bash
```sudo apt update && sudo apt upgrade -y```
#### Step 4: Install Essential Packages using Bash
* Web Server: Nginx or Apache ` webdock.io `
* Database Server: MySQL or PostgreSQL `linuxvox.com `
* Scripting Language: PHP or Python (depending on app stack) ` webdock.io `
* Version Control: Git
* Testing Tools: Apache JMeter (for load testing) ` codeless `
* Security Tools: ufw firewall, fail2ban
```Bash
sudo apt install nginx mysql-server php git -y
sudo apt install openjdk-11-jre-headless
wget https://downloads.apache.org//jmeter/binaries/apache-jmeter-5.6.2.tgz
tar -xvzf apache-jmeter-5.6.2.tgz
```
#### Step 5: Configure Services
* Enable and start Nginx: Using Bash
```
sudo systemctl enable nginx
sudo systemctl start nginx
```
* Secure MySQL installation: Using Bash
```
sudo mysql_secure_installation
```
#### Step 6: Deploy Test Application using Bash
* Clone application repo from GitHub.
* Place files in /var/www/html.
* Adjust permissions:
```
sudo chown -R www-data:www-data /var/www/html
```
#### Step 7: Verify Setup
* Access application via browser: http://192.168.1.40.
* Run JMeter tests to validate performance.

### Revision History
| **Version** | **Date**     |  **Author**            | **Description of Change**                                                             |
| ----------- | ----------   | --------------------- | ------------------------------------------------------------------------------------- |
| 1.0         | November 05, 2025   | Initial Author        | Initial creation of SOP and RACI (Accountability Matrix).               |
| 1.1         | November 10, 2025  | Reviewer / IT Manager | Updated steps to reflect new Linux OS baseline and security hardening standards.  |
| 1.2         | November 13, 2025   | Security Officer      | Added security compliance requirements and SSH key management procedures.        |
| 1.3         | November 17, 2025  | Network Engineer      | Updated networking section (firewall rules, DNS standards, VLAN assignments).     |

